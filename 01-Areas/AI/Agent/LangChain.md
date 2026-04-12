
provider 模型提供商，提供专门的`langchain-<provider>`包，实现了langchain的标准接口，可在不改变上层业务代码的情况下切换不同模型



如何初始化模型？
1. 通过`init_chat_model`函数
	- 初始化后会得到一个模型对象
2. 