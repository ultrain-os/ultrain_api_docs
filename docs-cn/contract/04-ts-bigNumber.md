## 方法列表
超脑TS_lib的BIGNUMBER所支持的方法如下表所示。

| 方法                                                                                        | 描述                                                 |
| :------------------------------------------------------------------------------------------| :----------------------------------------------------|
| [bn_cmp](docs-cn/ts-lib/04-ts-bigNumber#bn_cmp)                           |比较p，q大小。-1：p<q;0:p=q;1:p>q;                              |
| [bn_gcd](docs-cn/ts-lib/04-ts-bigNumber#bn_gcd)                           |求p，q公约数                            |
| [bn_is_probab_prime](docs-cn/ts-lib/04-ts-bigNumber#bn_is_probab_prime)                           |判断是否为素数。返回0为合数，1为素数，2可能为素数。p有4^(-reps)概率为合数。                            |
| [bn_mul](docs-cn/ts-lib/04-ts-bigNumber#bn_mul)                           |求p，q乘积                            |
| [bn_pow_mod](docs-cn/ts-lib/04-ts-bigNumber#bn_pow_mod)                           |求m^e%n                            |


## bn_cmp
```
(static) bn_cmp(p, q, base)
```
比较p，q大小。-1：p<q;0:p=q;1:p>q;

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|p              | number |                     |是     |
|q              | number |                     |是     |
|base           | number |进制，范围2-62                     |是     |

#### 参考示例
```nodejs
import { bn_cmp } from "ultrain-ts-lib/src/big_number";
```

## bn_gcd
```
(static) bn_gcd(p, q, base)
```
求p，q公约数

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|p              | number |                     |是     |
|q              | number |                     |是     |
|base           | number |进制，范围2-62                     |是     |

#### 参考示例
```nodejs
import { bn_gcd } from "ultrain-ts-lib/src/big_number";
```

## bn_is_probab_prime
```
(static) bn_is_probab_prime(p, reps, base)
```
判断是否为素数。返回0为合数，1为素数，2可能为素数。p有4^(-reps)概率为合数。

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|p              | number |                     |是     |
|reps              | number | 取15至50比较合理                    |是     |
|base           | number |进制，范围2-62                     |是     |

#### 参考示例
```nodejs
import { bn_is_probab_prime } from "ultrain-ts-lib/src/big_number";
```

## bn_mul
```
(static) bn_mul(p, q, base)
```
判断是否为素数。返回0为合数，1为素数，2可能为素数。p有4^(-reps)概率为合数。

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|p              | number |                     |是     |
|q              | number |                    |是     |
|base           | number |进制，范围2-62                     |是     |

#### 参考示例
```nodejs
import { bn_mul } from "ultrain-ts-lib/src/big_number";
```

## bn_pow_mod
```
(static) bn_pow_mod(m, e, n, base)
```
求m^e%n

#### 参数说明
|参数               |类型    |说明                            |是否必填|
| :----------------| :------| :-----------------------------|:-----|
|m              | number | 底                    |是     |
|e              | number | 指数                 |是     |
|n              | number |  除数                |是     |
|base           | number |进制，范围2-62                     |是     |

#### 参考示例
```nodejs
import { bn_pow_mod } from "ultrain-ts-lib/src/big_number";
```
