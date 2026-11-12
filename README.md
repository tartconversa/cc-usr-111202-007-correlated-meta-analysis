# 相关实验效应的随机效应综合与敏感性

本项目保存虚构科学工程分析的合成输入与Python读取工具。当前工具仅解析输入并显示类型和条数，不执行参数拟合、统计分析、方程求解、优化或模型训练。所有仪器、实验、研究与专家身份均为虚构。

## 数据口径

每研究y、V、X的行顺序一致，V是同研究采样协方差；随机截距方差在整块上加tau2*ones，不能只加对角。coefficient_names给出X列名。

fixtures保存原始输入，src/meta_reader.py是当前读取器，material-index.json为文件内容摘要。研究计算输出可写到独立.workspace-output目录，输入不应被覆盖。

## 本地运行

Python 3.11及以上；已有读取工具仅依赖标准库，无第三方安装步骤。进入项目根目录执行：

    python -m src.meta_reader fixtures/studies.json

编译检查：

    python -m compileall -q src tests

输入契约验证：

    python -m unittest discover -s tests -v

## 固定容器

    docker build -t correlated-meta-analysis:local .
    docker run --rm correlated-meta-analysis:local

容器按完整镜像摘要固定，默认运行读取测试，不访问外部实验系统。
