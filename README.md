# Blockchain
搭建一个属于自己的区块链

## 实验背景
在逛B站时，突然发现了一个对区块链原理讲解十分透彻的视频，遂有了本次区块链实验。  
视频链接：[想知道比特币（和其他加密货币）的原理吗？](https://www.bilibili.com/video/av12465079)

## 实验环境
1.	基于VMware的Ubuntu18.04虚拟机
2.	Postman接口测试工具

## 实验步骤

### 1.实现区块链类
我们要创建一个 Blockchain 类 ，他的构造函数创建了一个初始化的空列表（要存储我们的区块链），并且另一个存储交易。下面是我们这个类的实例:
```
class Blockchain(object):
    def __init__(self):
        self.chain = []
        self.current_transactions = []
        
    def new_block(self):
        # Creates a new Block and adds it to the chain
        pass
    
    def new_transaction(self):
        # Adds a new transaction to the list of transactions
        pass
    
    @staticmethod
    def hash(block):
        # Hashes a Block
        pass

    @property
    def last_block(self):
        # Returns the last Block in the chain
        pass
```
`Blockchain` 类负责管理链式数据，它会存储交易并且还有添加新的区块到链式数据的`Method`。

一个区块`block`包含有索引、时间戳、事务列表、工作量证明、前一个块的散列。
```
block = {
    'index': 1,
    'timestamp': 1506057125.900785,
    'transactions': [
        {
            'sender': "8527147fe1f5426f9dd545de4b27ee00",
            'recipient': "a77f5cdfa2934df3954a5c7c7da5df1f",
            'amount': 5,
        }
    ],
    'proof': 324984774000,
    'previous_hash': "2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"
}
```

### 2.对区块链进行实例化

当我们的`Blockchain`被实例化后，我们需要将创世区块（一个没有前导区块的区块）添加进去进去。我们还需要向我们的起源块添加一个证明，这是挖矿的结果(或工作证明)。

除了在构造函数中创建创世区块外，我们还会补全`new_block()`、`new_transaction()`和`hash()`函数。详情可见源程序


### 3.使用flask创建API接口
### 4.实现节点一致性

## 注意事项
我这里实验的难度是哈希值的前面四位是0，0的位数固定不变的，但在实际的比特币难度值是在动态变化的，在全网算力不断变化，需要维持平均10分钟出一个区块，难度值必须根据全网算力的变化进行调整。
