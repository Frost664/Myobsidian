这个`run_test.sh`脚本的目的似乎是运行一个测试脚本 `test.py`，使用一个配置文件（例如 `./configs/k400/k400_test.yaml`）。以下是脚本的主要步骤：

1. 检查是否提供了配置文件作为参数，如果没有则输出错误信息并退出。
2. 从配置文件中提取网络类型（`type`）、网络架构（`arch`）、数据集（`dataset`）等信息。
3. 根据时间戳创建一个目录结构，例如 `exp/${type}/${arch}/${dataset}/${now}`。
4. 运行 `test.py` 脚本，并将输出日志保存到刚刚创建的目录中。

用这里来防止 找不到 pytorch/torch 包

```shell
source activate pytorchCLIP
# 加入了一行来启动配置的项目环境
```

新的报错

```error
Traceback (most recent call last):
  File "E:\ActionCLIP-master\test.py", line 159, in <module>
    main()
  File "E:\ActionCLIP-master\test.py", line 86, in main
    config = yaml.load(f)
TypeError: load() missing 1 required positional argument: 'Loader'
```

按意思是 不能使用这个函数，因为 yaml 的版本变得

将 test.py 第86行的
```python
config = yaml.load(f)
# 改为
config = yaml.safe_load(f)
```


改完后的报错
```error
wandb: ERROR api_key not configured (no-tty). call wandb.login(key=[your_api_key])  
Traceback (most recent call last):  
  File "E:\ActionCLIP-master\test.py", line 159, in <module>  
    main()  
  File "E:\ActionCLIP-master\test.py", line 89, in main  
    wandb.init(project=config['network']['type'],  
  File "D:\anaconda\envs\pytorchCLIP\lib\site-packages\wandb\sdk\wandb_init.py", line 1185, in init  
    raise e  
  File "D:\anaconda\envs\pytorchCLIP\lib\site-packages\wandb\sdk\wandb_init.py", line 1162, in init  
    wi.setup(kwargs)  
  File "D:\anaconda\envs\pytorchCLIP\lib\site-packages\wandb\sdk\wandb_init.py", line 306, in setup  
    wandb_login._login(  
  File "D:\anaconda\envs\pytorchCLIP\lib\site-packages\wandb\sdk\wandb_login.py", line 298, in _login  
    wlogin.prompt_api_key()  
  File "D:\anaconda\envs\pytorchCLIP\lib\site-packages\wandb\sdk\wandb_login.py", line 228, in prompt_api_key  
    raise UsageError("api_key not configured (no-tty). call " + directive)  
wandb.errors.UsageError: api_key not configured (no-tty). call wandb.login(key=[your_api_key])
```
没有配置 wandb 的API 无法使用


这里涉及到一个新的东西 wandb
[wandb使用教程(一)：基础用法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/493093033)
wandb是什么

配置步骤在[[wandb]]中，将api装好了

再来一次紧张刺激的 运行
嗯。。。。可以跑起来一部分了

