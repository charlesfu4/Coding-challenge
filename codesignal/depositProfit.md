## Deposit Profit

You have deposited a specific amount of money into your bank account. Each year your balance increases at the same growth rate. With the assumption that you don't make any additional deposits, find out how long it would take for your balance to pass a specific threshold.

**Brilliant Solution**

```java
int depositProfit(int deposit, int rate, int threshold) {
    return (int)Math.ceil(Math.log((double)threshold / deposit) / Math.log(1 + (rate / 100.0)));
}
```

This solution makes use of log to calculate the power. 

