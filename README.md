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
 




 
