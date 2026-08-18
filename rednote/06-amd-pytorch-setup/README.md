# AMD显卡如何跑PyTorch？一篇搞定

## 标题

AMD显卡如何跑PyTorch？一篇搞定

## 正文

“好多人抱怨：A卡实在太折腾，装个ROCm、装个PyTorch都费劲。”

这段时间听到不少人这么说😂

AMD显卡可以装PyTorch, 其实命令本身不难，但你需要知道真正容易卡住的是：PyTorch、ROCm、gfx和系统版本没对上。

🧹 安装前先别急着复制命令

先查清楚显卡对应的gfx，再确认系统和Python版本。之前装过其他版本的话，建议先把旧包卸干净，避免不同来源的包打架。

🐧 Linux有5条路可以选

- 显卡gfx明确：选AMD multi-arch
- 想尝试新版本：选Nightly，记得补ROCm runtime
- 怕弄乱本机环境：直接用Docker
- 已经确定ROCm版本：选AMD manylinux
- 想按固定版本矩阵安装：选PyTorch ROCm 7.2源

具体命令和版本都放在配图里，直接找到适合自己的那一组。

🪟 Windows用户看这里

目前支持列表内的部分Radeon显卡和Ryzen处理器，已经可以在Windows原生安装PyTorch。

安装前需要对好显卡、Windows、驱动和Python版本，再依次安装ROCm组件及PyTorch wheels。

不过要注意：目前是PyTorch可以原生运行，不代表整套ROCm软件栈都能在Windows使用。设备暂时不在支持范围内，可以再看看WSL2方案。

✅ 装完先跑这条命令

python -c "import torch; print(torch.__version__, torch.cuda.is_available())"

看到版本号和True，说明PyTorch已经识别到AMD GPU。

ROCm版仍然沿用torch.cuda接口，所以看到cuda不用怀疑，跑的还是A卡。

再碎碎念一句：gfx要对应，三个PyTorch包别乱配，不同ROCm发布线也别混装。很多“装完不认卡”，问题就出在这里。

你现在是在Windows还是Linux上折腾PyTorch？

在下面扣个W/L带上显卡型号，也可以说说自己卡在哪一步🙋

我们来自AMD个人工程师团队，后面还会继续整理更多干货内容。
