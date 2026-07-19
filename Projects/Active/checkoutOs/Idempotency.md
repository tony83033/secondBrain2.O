CLIENT                          checkoutOs                      REDIS
  |                                |                              |
  |  POST /payments                 |                              |
  |  Idempotency-Key: abc-123       |                              |
  |  {amount: 50000, currency: INR} |                              |
  |-------------------------------->|                              |
  |                                |                              |
  |                          [Middleware]                          |
  |                          1. Extract header "abc-123"          |
  |                          2. Validate UUID format              |
  |                          3. Hash request body → SHA256        |
  |                          4. Attach {key, hash} to req         |
  |                                |                              |
  |                          [Service Layer]                       |
  |                          Check idempotency:                   |
  |                                |                              |
  |                          GET chk:idem:abc-123                 |
  |                                |----------------------------->|
  |                                |        null (key not found)  |
  |                                |<-----------------------------|
  |                                |                              |
  |                          Key doesn't exist → MISS             |
  |                          Create record:                        |
  |                          SET chk:idem:abc-123                 |
  |                            {hash, status: IN_PROGRESS}        |
  |                            NX (only if still doesn't exist)   |
  |                                |----------------------------->|
  |                                |              OK              |
  |                                |<-----------------------------|
  |                                |                              |
  |                          Proceed to create payment:           |
  |                          1. Call Razorpay API                 |
  |                          2. Save to chk:pay:*                 |
  |                          3. Return paymentUrl                 |
  |                                |                              |
  |                          Mark complete:                        |
  |                          UPDATE chk:idem:abc-123              |
  |                            {hash, status: COMPLETED,          |
  |                             response: {paymentId, url, ...}}  |
  |                                |----------------------------->|
  |                                |              OK              |
  |                                |<-----------------------------|
  |                                |                              |
  |  200 {paymentId: chk_xyz, url: ...}                           |
  |<----------------------------------------------------------------|