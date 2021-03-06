# qafactor-rs   多因子权重测试微服务:

factor-rs

>> 除了数据获取以外, 毫秒级的账户撮合以及成交撮合

![image.png](http://pic.yutiansut.com/FmrONcJhrY-qigeuMrb2cQ4H5EhC)

POST: http://127.0.0.1:8031/factor/submit

headers: 

Content-Type: application/json

```json
{"codelist": ["000001", "000002"], "start": "2018-08-22", "end": "2018-08-28", "init_cash": 100000.0, "weights": {
    "2018-08-22":{"000001":0.2, "000002": 0.8},
    "2018-08-23":{"000001":0.4, "000002": 0.6},
    "2018-08-24": {"000001":0.6, "000002": 0.4},
    "2018-08-27": {"000001":0.2, "000002": 0.8},
    "2018-08-28": {"000001":0.8, "000002": 0.2}
}}
```
    

    
### python 代码
```python
import requests
import json
import pandas as pd
pd.DataFrame(json.loads(requests.post('http://192.168.2.124:8031/factor/submit', json={"codelist": ["000001", "000002"], "start": "2018-08-22", "end": "2018-08-28", "init_cash": 100000.0, "weights": {
    "2018-08-22":{"000001":0.2, "000002": 0.8},
    "2018-08-23":{"000001":0.4, "000002": 0.6},
    "2018-08-24": {"000001":0.6, "000002": 0.4},
    "2018-08-27": {"000001":0.2, "000002": 0.8},
    "2018-08-28": {"000001":0.8, "000002": 0.2}
}}).text))

```

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>account_cookie</th>
      <th>amount</th>
      <th>code</th>
      <th>commission</th>
      <th>datetime</th>
      <th>direction</th>
      <th>frozen</th>
      <th>message</th>
      <th>order_id</th>
      <th>price</th>
      <th>realorder_id</th>
      <th>tax</th>
      <th>trade_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>model</td>
      <td>2000.0</td>
      <td>000001</td>
      <td>4.62000</td>
      <td>2018-08-22</td>
      <td>1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>9.24</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>0.000</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
    </tr>
    <tr>
      <th>1</th>
      <td>model</td>
      <td>3200.0</td>
      <td>000002</td>
      <td>19.12800</td>
      <td>2018-08-22</td>
      <td>1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>23.91</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>0.000</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
    </tr>
    <tr>
      <th>2</th>
      <td>model</td>
      <td>700.0</td>
      <td>000002</td>
      <td>4.02500</td>
      <td>2018-08-23</td>
      <td>-1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>23.00</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>16.100</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
    </tr>
    <tr>
      <th>3</th>
      <td>model</td>
      <td>2000.0</td>
      <td>000001</td>
      <td>4.65000</td>
      <td>2018-08-23</td>
      <td>1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>9.30</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>0.000</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
    </tr>
    <tr>
      <th>4</th>
      <td>model</td>
      <td>800.0</td>
      <td>000002</td>
      <td>4.53200</td>
      <td>2018-08-24</td>
      <td>-1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>22.66</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>18.128</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
    </tr>
    <tr>
      <th>5</th>
      <td>model</td>
      <td>2100.0</td>
      <td>000001</td>
      <td>4.88775</td>
      <td>2018-08-24</td>
      <td>1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>9.31</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>0.000</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
    </tr>
    <tr>
      <th>6</th>
      <td>model</td>
      <td>4100.0</td>
      <td>000001</td>
      <td>10.27050</td>
      <td>2018-08-27</td>
      <td>-1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>10.02</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
      <td>41.082</td>
      <td>f3b4958c-52a1-11e7-8001-010203040506</td>
    </tr>
    <tr>
      <th>7</th>
      <td>model</td>
      <td>1700.0</td>
      <td>000002</td>
      <td>9.76650</td>
      <td>2018-08-27</td>
      <td>1</td>
      <td>0.0</td>
      <td></td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>22.98</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
      <td>0.000</td>
      <td>f3b4958c-52a1-11e7-8002-010203040506</td>
    </tr>
  </tbody>
</table>

### pandas 接入示例
```python
import QUANTAXIS as QA
block = QA.QA_fetch_stock_block_adv().get_block('上证50')
data = QA.QA_fetch_stock_day_adv(block.code, '2016-01-01', '2019-11-10').pivot('close')

dp = data.dropna(axis=1).bfill().apply(lambda x: x/x.sum(), axis=1)
dp.index = dp.index.map(lambda x: str(x)[0:10])
dp = dp.applymap(lambda x: round(x -0.001, 3))

requests.post('http://192.168.2.124:8031/factor/submit', 
                                      json={"codelist":dp.columns.tolist(), 
                                            "start":dp.index.map(lambda x: str(x)[0:10])[0], 
                                            "end": dp.index.map(lambda x: str(x)[0:10])[-1], 
                                            "init_cash": 1000000000.0, 
                                            "weights":dp.to_dict(orient='index')}).text
```


首先需要注意的是本模式是等市值(动态市值)的调仓模式


及每日基于账户的动态权益重新分配市值权重
考虑一种极端情况 :

A 股票一直涨停
B 股票一直跌停

等权重的模型则会表现出的调仓情况为:

SELL A || BUY B
来保证 A/B 的动态市值是相等的
    
### EXAMPLE 

POST: http://127.0.0.1:8031/factor/submit

headers: 

Content-Type: application/json
```json
{"codelist": ["000001", "000002"], "start": "2018-08-22", "end": "2018-08-28", "init_cash": 100000.0, "weights": {
    "2018-08-22":{"000001":0.2, "000002": 0.8},
    "2018-08-23":{"000001":0.4, "000002": 0.6},
    "2018-08-24": {"000001":0.6, "000002": 0.4},
    "2018-08-27": {"000001":0.2, "000002": 0.8},
    "2018-08-28": {"000001":0.8, "000002": 0.2}
}}
```
   
```json
[
    {
        "code": "000001",
        "amount": 2000.0,
        "price": 9.24,
        "datetime": "2018-08-22",
        "order_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "account_cookie": "model",
        "commission": 4.62,
        "tax": 0.0,
        "message": "",
        "frozen": 0.0,
        "direction": 1
    },
    {
        "code": "000002",
        "amount": 3200.0,
        "price": 23.91,
        "datetime": "2018-08-22",
        "order_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "account_cookie": "model",
        "commission": 19.128,
        "tax": 0.0,
        "message": "",
        "frozen": 0.0,
        "direction": 1
    },
    {
        "code": "000002",
        "amount": 700.0,
        "price": 23.0,
        "datetime": "2018-08-23",
        "order_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "account_cookie": "model",
        "commission": 4.025,
        "tax": 16.1,
        "message": "",
        "frozen": 0.0,
        "direction": -1
    },
    {
        "code": "000001",
        "amount": 2000.0,
        "price": 9.3,
        "datetime": "2018-08-23",
        "order_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "account_cookie": "model",
        "commission": 4.65,
        "tax": 0.0,
        "message": "",
        "frozen": 0.0,
        "direction": 1
    },
    {
        "code": "000002",
        "amount": 800.0,
        "price": 22.66,
        "datetime": "2018-08-24",
        "order_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "account_cookie": "model",
        "commission": 4.532,
        "tax": 18.128,
        "message": "",
        "frozen": 0.0,
        "direction": -1
    },
    {
        "code": "000001",
        "amount": 2100.0,
        "price": 9.31,
        "datetime": "2018-08-24",
        "order_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "account_cookie": "model",
        "commission": 4.8877500000000005,
        "tax": 0.0,
        "message": "",
        "frozen": 0.0,
        "direction": 1
    },
    {
        "code": "000001",
        "amount": 4100.0,
        "price": 10.02,
        "datetime": "2018-08-27",
        "order_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8001-010203040506",
        "account_cookie": "model",
        "commission": 10.2705,
        "tax": 41.082,
        "message": "",
        "frozen": 0.0,
        "direction": -1
    },
    {
        "code": "000002",
        "amount": 1700.0,
        "price": 22.98,
        "datetime": "2018-08-27",
        "order_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "trade_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "realorder_id": "f3b4958c-52a1-11e7-8002-010203040506",
        "account_cookie": "model",
        "commission": 9.7665,
        "tax": 0.0,
        "message": "",
        "frozen": 0.0,
        "direction": 1
    }
]
```


首先我们随机分配权重给这些品种:

000001 / 000002

### day1: 2018-08-22 初始值 账户动态权益: 100000.0

```
000001 赋予初始权重 0.2
000002 赋予初始权重 0.8
```

"2018-08-22":{"000001":0.2, "000002": 0.8},

price: 000001:9.24, 000002:  23.91

base on marketValue:   / 23.91*3200.0 = 76512 ==  0.189 大致是 1:4 关系

生成订单: 000001 2000股  9.24 多单

撮合订单:  9.24*2000 = 18480  费用(万2.5) 18480*0.00025= 4.62

生成订单: 000002 3200股  23.91  多单

撮合订单: 23.91*3200.0 = 76512  费用(万2.5) 76512*0.00025= 19.128

```md
===========

账户初始资金: 100000
- 现金买入000001: 18480 
- 手续费  4.62

- 现金买入000002: 76512
- 手续费  19.128

账户期末资金: 4984.252 
账户期末持仓: 
    000001 2000股 * 9.24  市值 18480 
    000002 3200股 * 23.91 市值 76512
```


### day2: 2018-08-23 调整后 账户动态权益: 97184.252

```

账户初始市值:
现金: 4984.252 
000001: 9.3 openprice  市值 18600
000002: 23  openprice  市值 73600

权益: 97184.252

```

```
000001 权重上调: 0.2 -> 0.4
000002 权重下调: 0.8 -> 0.6

000001 应占市值: 0.4*97184.252=38873.7008
000002 应占市值: 0.6*97184.252=58310.5512

=> 000001 应补充市值  (38873.7008-18600) =20273.7008  
    20273.7008/ 9.3 =2179 股
    按 100股/手  - 1 手的原则 => 补充 2000 股 000001

=> 000002 应补充市值  (58310.5512-73600) = -15289.4488
    -15289.4488 /23 = -664.758
    按 100股/手 + 1 手 的原则 => 卖出 700 股 000002

```
"2018-08-23":{"000001":0.4, "000002": 0.6},

price: 000001:9.3, 000002:  23

生成订单: 000001 2000股  9.3 多单

撮合订单:  9.3*2000 = 18600  费用(万2.5) 18600*0.00025= 4.65

生成订单: 000002 -700股  23  空单

撮合订单: 23*700.0 = 16100  费用(万2.5) 16100*0.00025= 4.025 | 印花税(千 1) 16100 * 0.001 = 16.1



```md
===========

账户初始市值:  97184.252  / 现金 4984.252 
+ 卖出 000002: 16100
- 手续费  4.025 
- 印花税  16.1


- 现金买入 000001: 18600
- 手续费  4.65


账户期末资金: 2459.477
账户期末持仓: 
    000001 4000股 * 9.3  市值 37200
    000002 2500股 * 23 市值 57500
```

37200/57500 = 0.64  大致== 0.4/0.6=0.66


### day3: 2018-08-24
"2018-08-24": {"000001":0.6, "000002": 0.4},


### da4: 2018-08-27
"2018-08-27": {"000001":0.2, "000002": 0.8},


### day5: 2018-08-28
"2018-08-28": {"000001":0.8, "000002": 0.2}
