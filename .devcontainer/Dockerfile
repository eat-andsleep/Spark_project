FROM ubuntu:22.04

# 安装基础依赖
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    openjdk-17-jdk \
    python3 \
    python3-pip \
    git \
    && apt-get clean

# 设置工作目录
WORKDIR /workspace

# 安装 Spark（版本可根据需要修改）
RUN wget https://dlcdn.apache.org/spark/spark-3.5.0/spark-3.5.0-bin-hadoop3.tgz  && \
    tar -xzf spark-3.5.0-bin-hadoop3.tgz && \
    mv spark-3.5.0-bin-hadoop3 /opt/spark

# 设置环境变量
ENV SPARK_HOME=/opt/spark
ENV PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin
ENV PYTHONPATH=$SPARK_HOME/python:$SPARK_HOME/python/lib/py4j-0.10.9.5-src.zip:$PYTHONPATH
ENV PYSPARK_PYTHON=python3
ENV PYSPARK_DRIVER_PYTHON=python3

# 安装 pip 依赖（后续会在 devcontainer.json 中再执行一次 pip install）
RUN pip3 install --upgrade pip