
> Cargo is Rust's build system and package manager



目录在`~/.cargo`，可以通过环境变量`CARGO_HOME`修改

cargo命令在`~/.cargo/bin`

`~/.cargo/bin`目录下有cargo，rustc，rustup命令

### 创建Cargo项目
1. 使用cargo的新项目通过以下命令创建
```bash
# 如果是在已有git仓库执行以下命令，不会创建git相关的文件
cargo new project_name
# 即使是在已有git仓库执行，也会创建git相关的文件
cargo new --vcs=git project_name
```
2. 没有使用cargo的旧项目想使用cargo时，使用以下命令
```bash
# 该命令只会创建Config.toml和git相关文件，不会创建src目录，需要自己手动将代码移动进src目录
cargo init
```


### 常用命令
```bash
# 编译cargo项目，会生成target目录，里面包含可执行文件
cargo build

# 编译并运行项目
cargo run

# 检查项目是否能编译成功，并且不会产生可执行文件，比cargo build速度快，适合开发阶段
cargo check
```

