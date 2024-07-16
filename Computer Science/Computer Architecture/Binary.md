### Decimal (Base$_{10}$)
| Voltage | Value |
| ------- | ----- |
| 0v      | 0     |
| 5v      | 1     |
| 10v     | 2     |
| 15v     | 3     |
| 20v     | 4     |
| ...     | ...   |
| 45v     | 9     |
There are too many available values, so it's prone to mistakes

### Binary (Base$_{2}$)
| Voltage | Value |
| ------- | ----- |
| 0v      | 0     |
| 45v     | 1      |
If there's much power at all, then it's probably a 1. Otherwise it'll be 0.


### Converting Binary to Decimal
| $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 64    | 32    | 16    | 8     | 4     | 2     | 1     |
Binary is a **true**/**false** system, so each binary digit can be enabled or disabled to add up to some decimal number

| Index                 | $2^6$     | $2^5$    | $2^4$     | $2^3$    | $2^2$     | $2^1$    | $2^0$     |     |
| --------------------- | --------- | -------- | --------- | -------- | --------- | -------- | --------- |
| Value                 | 64        | 32       | 16        | 8        | 4         | 2        | 1              |
| Enabled               | **False** | **True** | **False** | **True** | **False** | **True** | **False** |     |
| Binary Representation | 0         | 1        | 0         | 1        | 0         | 1        | 0          |     |
= `0101010`$_{2}$ = 42$_{10}$

### Converting Decimal to Binary
| Step | Operation           | Remainder |
| ---- | ------------------- | --------- |
| 1    | $\frac{42}{2}=21$   | 0         |
| 2    | $\frac{21}{2} = 10$ | 1         |
| 3    | $\frac{10}{2}$ = 5  | 0         |
| 4    | $\frac{5}{2} = 2$   | 1         |
| 5    | $\frac{2}{2} = 1$   | 0         |
| 6    | $\frac{1}{2} = 0$   | 1         |
Each step is also the position in binary. So 42$_{10}$ = `101010`$_{2}$ (read from bottom up on chart)