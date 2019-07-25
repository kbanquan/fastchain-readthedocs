Java
=================

如果使用maven，可以加入如下依赖::

	<dependency>
	    <groupId>com.kbanquan</groupId>
	    <artifactId>chain-sdk</artifactId>
	    <version>1.0</version>
	</dependency>

如果使用gradle，可以加入如下依赖::
	
	compile group: 'com.kbanquan', name: 'chain-sdk', version: '1.0'

初始化客户端
------------------

::

	FabricClient client = new FabricClient();
	// 设置子节点名称
	client.setOrgName("peerOrg1");
	//设置智能合约
	client.setChaincodeName("mycc");
	//设置通道
    client.setChannelID("mychannel");
    //设置智能合约版本
    client.setVersion("1.0");


客户端初始化完成后即可调用客户端中的方法发送请求

发起交易
------------------

::

	CreateTransPayload payload = new CreateTransPayload();
	// 设置存证ID
	payload.setBusinessId("0000702BD0C942DFB2AFF06CE1590A09");
	// 设置存证Hash
    payload.setHash("ff2d5960e239692c834c35307223f45542f35330235009d5a6aec5f7bc19f1fb");
	// 调用hash上链接口，如果成功则返回交易ID，如果失败则返回失败消息
	try {
		CreateTransResponse response = client.sendTransaction(payload);
		System.out.println(response.getData().getTxID());
	} catch (ServerException e) {
		System.out.println(e.getMessage());
	}





