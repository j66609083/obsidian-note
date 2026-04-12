
Mac系统
1. 从官网下载并图形化安装
2. 命令行窗口关闭自动激活：
```bash
conda config --set auto_activate false
```
3. 设置channel为社区版本
```bash
conda config --remove channels defaults
conda config --add channels conda-forge
conda config --set channel_priority strict
```
4. 部分情况下要通过修改配置文件来修改channel