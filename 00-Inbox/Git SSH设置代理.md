
配置`~/.ssh/config`:
```txt
Host github.com
  HostName github.com
  User git
  ProxyCommand nc -x 127.0.0.1:7897 %h %p
  ServerAliveInterval 60
  ServerAliveCountMax 5
```

解释：

| 选项                                      | 说明                                    |
| --------------------------------------- | ------------------------------------- |
| Host github.com                         | 匹配 GitHub                             |
| HostName github.com                     | 实际要连接的主机                              |
| User git                                | SSH 用户                                |
| ProxyCommand nc -x 127.0.0.1:7890 %h %p | 使用 `nc`（netcat）通过 SOCKS5 代理连接 `%h:%p` |

# ProxyCommand 是什么
`ProxyCommand`是SSH的一个配置项，用来告诉SSH：
> 连接目标主机之前，不直接走网络，而是通过一个命令/代理转发流量