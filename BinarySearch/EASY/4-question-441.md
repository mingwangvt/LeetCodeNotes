\#441 Arranging Coin

```
public int arrangeCoins(int n) {
        if (n <= 1) return n;
        double num = n / 100.0 * 2;
        double row = Math.sqrt(num + 0.25 / 100) - 0.5 / 10;
        return (int)(row * 10);
    }
```
(1 + row) * row / 2 = total;
==> row = sqrt(2 * total + 1 / 4) - 1 / 2;
question:
overflow!
input 1 or 36, after square root in code line 4, result 0.999... and 7.999... instead of 1 and 8. How to deal with overflow caused by multiply???
