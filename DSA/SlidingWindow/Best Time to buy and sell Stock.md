
We have an array 
10,1,5,6,7,1

we need to subtract selling price to buy price

sellingPrice - buy price = prices[i] - buyprice;

first we need to identify which is the smallest number in the array 
because if we buy in less and sell in high we make profit

```java
class Solution {

    public int maxProfit(int[] prices) {

        int maxProfit = 0;

        // at beginning minimun price is the first price

        int buyPrice = prices[0];

        for(int i=1;i<prices.length;i++){

            if(prices[i]<buyPrice){

                buyPrice = prices[i];

            }else{

                int profit = prices[i]-buyPrice;

                maxProfit = Math.max(profit,maxProfit);

            }

        }

        return maxProfit;

    }

}
```