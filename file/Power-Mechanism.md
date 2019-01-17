# 以太零Power值详解

## **一、简述**

Power为以太零原生代币，PoS机制发行，不可交易，仅用于以太零交易时的Gas消耗。所有余额大于或等于0.01etz的账号，都会随着区块的增长持续产出Power，直到达到Power上限。

console下查询自己的可用Power：

```javascript
web3.fromWei(eth.getPower("your address"), "ether")
```

![](https://github.com/etherzero-org/wiki/blob/master/img/assets_-LP94keYaE-d-gp2r4-__-LP9GJ_SIwEvql4BW7UH_-LP9GtDIvWThfJRajX3t_%E6%88%AA%E5%9B%BE.png?raw=true)

------

## **二、Power的两个属性**

1、上限值Max (由etz余额决定上限)

2、每个区块产出的速度Speed (由etz余额决定速度)

------

## **三、Power的实现原理**

#### 1、一个账户的Power

**Power = Min(PowerMax, BlockGap * PowerSpeed)**

BlockGap = 当前区块高度 - 上一笔交易区块高度

#### 2、一笔交易消耗的Power

**PowerSpend = Gas * GasPrice**

例如一笔普通转账的Gas为21000，GasPrice为18Gwei

18Gwei = 0.000,000,018 ether

一笔普通转账需要power = 21000 * 0.000000018 = 0.000378 ether

#### 3、一个账户的Power上限值

**PowerMaxPowerMax = (Math.exp(-1/(x*50)*10000)*10000000+200000)*0.000000018**

![](https://github.com/etherzero-org/wiki/blob/master/img/assets_-LP94keYaE-d-gp2r4-__-LP9GJ_SIwEvql4BW7UH_-LP9H-VCU2xdEWU8ACQB_%E6%88%AA%E5%9B%BE%20(1).png?raw=true)

例如一个有0.01etz余额的账户，PowerMax为0.0036 ether

假设GasPrice设置为18Gwei（即0.000000018 ether），这个0.01etz余额的账户单笔交易最大可设置Gas = 0.0036 / 0.000000018 = 200000

GasPrice为18Gwei的情况下，这个账户不能发送gas超过20万的交易

假设GasPrice设置为36Gwei（即0.000000036 ether），这个0.01etz余额的账户单笔交易最大可设置Gas = 0.0036 / 0.000000036 = 100000

GasPrice为36Gwei的情况下，这个账户不能发送gas超过10万的交易

#### **4、一个账户的Power恢复速度PowerSpeed**

**PowerSpeed = (Math.exp(-1/(x\*2)\*1000)\*200000+1000)\*0.000000018**

![](https://github.com/etherzero-org/wiki/blob/master/img/assets_-LP94keYaE-d-gp2r4-__-LP9GJ_SIwEvql4BW7UH_-LP9H-VCU2xdEWU8ACQB_%E6%88%AA%E5%9B%BE%20(1).png?raw=true)

例如一个余额为0的账户，在区块高度100时收到了0.01etz

这个账户的在区块高度101时的Power = (101 - 100) * 0.000018 = 0.000018

这个账户的在区块高度102时的Power = (102 - 100) * 0.000018 = 0.000036

这个账户的在区块高度201时的Power = (201 - 100) * 0.000018 = 0.0018

这个账户的在区块高度301时的Power = (301 - 100) * 0.000018 = 0.0036

这个账户的在区块高度401时的Power = (401 - 100) * 0.000018 = 0.0036 （不会再继续增长）

 区块高度301之后，已经达到了上限值，如需要提升Power，需要增加账户余额。

![](https://github.com/etherzero-org/wiki/blob/master/img/assets_-LP94keYaE-d-gp2r4-__-LP9GJ_SIwEvql4BW7UH_-LP9H6zJ_h2Y7aF-UYax_%E6%88%AA%E5%9B%BE%20(3).png?raw=true)

## **四、Balance-Power对照表**

![](https://github.com/etherzero-org/wiki/blob/master/img/assets_-LP94keYaE-d-gp2r4-__-LP9GJ_SIwEvql4BW7UH_-LP9HADdJJkI6Wp2ZEDM_%E6%88%AA%E5%9B%BE%20(4).png?raw=true)

从表中可以查询到，一个0.01etz余额的账户，单笔交易最高可消耗Gas为360万（假设GasPrice设置为1Gwei）

