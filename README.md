# trialchain
启动过程:

1. 修改配置文件信息
  - 设置钱包的公私钥
  - 添加EtherScan api token
  
2. cd compose

3. ./start-master.sh
  - 这会启动平台的主服务
  - 服务在本地的5000端口提供服务
  
4. ./start-explorer.sh 
  - Print the logs for the MultiChain Explorer container to get the node key, then log into the Web Portal (port 5000) and go to Admin->Add Node to grant permissions. Then restart the Explorer container. 

5. ./start-nifi.sh
  - 这会启动NIFi服务，通过网络连接到TrialChain，在本地8000端口提供服务
  - 可选：也可以上传NiFi的模版nifi/TrialChain.xml进行流的控制
 
 
 
 组织框架：
 webportal：提供了一个web界面,flask做的
 multichian：将数据运行在本机的私有区块链上面
 geth：将本机的私有区块链打包发送到共有链上面，也就是以太坊的公网。
 
 
 数据的完整性：
 主要是理论的东西，在代码里面是体现不出来。
 
- 数据的完整性：
主要是介绍理论的东西，把你用的方法介绍一下，加密算法，椭圆曲线。这种方法保证了数据的完整性。仿真出来的。
你要去强调一下，你的算法是可以保证数据的完整性的。例如：一个定理一样，这个定理肯定是对的。
用你的加密算法，证明她肯定是完整的，直接是理论证明。
proof：这样的一个证明，就保证了数据是完整的。            
在你保证数据是完整的情况下，你才可以去写程序，去实现一个系统。这个系统可以用到你说的方法。
 
- 对于程序来说：
有之前的证明，你才可以写程序。实现你的密码学的东西，和区块链的东西。
在scripts文件夹里面，存放的就是完整性验证的实现算法，简单的来说，就是对文件进行一个hash。这样就验证了完整性。

- 区块链是核心
你对文件取了hash之后，你怎么保证这个hash没有被篡改？？？？？
这个时候就可以用区块链，去中心化的账本，数据一旦被写入，就不能修修改。
我们提供了一个web界面，可以通过以太坊提供的api去查询数据。也就是去查询这个hash值。web界面可以调用的。



 