FROM centos:7

USER root
# centos 7 更换阿里源
RUN rm -rf /etc/yum.repos.d/*
RUN curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo

# 安装 Python 3 和其他依赖
RUN yum -y groupinstall "Development Tools"
RUN yum -y install python3 python3-pip

# 安装必要的 Python 库
COPY requirements.txt /app/
RUN python3 -m pip install -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple --upgrade pip
RUN pip3 config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
RUN pip3 install -r /app/requirements.txt

# 安装 PyInstaller
RUN pip3 install pyinstaller
