# internlm下载指南

## ‌一、环境准备
### 系统配置
> -  服务器：鲲鹏服务器
> -  操作系统：Huawei Cloud EulerOS 2.0 64bit
> - CPU: 4vCPUs 或更高
> - RAM: 16GB 或更大
> - Disk: 至少 40GB
### 更新系统

```bash
sudo yum update -y  
```

### 安装conda创建python环境
```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-aarch64.sh

bash Miniconda3-latest-Linux-aarch64.sh

#若安装后无法识别 conda 命令，手动添加路径：
echo 'export PATH="~/miniconda3/bin:$PATH"' >> ~/.bashrc    
source ~/.bashrc  

#创建环境
conda create --name flair python=3.9
```

### 安装flair
```bash
git clone https://github.com/flairNLP/flair.git
cd flair
```
### 修改requirements.txt文件中pytorch版本
```bash
# torch>=1.5.0,!=1.8  改为
torch==1.11.0
```
### 安装依赖
```bash
pip install -r requirements.txt
pip install gensim
```

### 下载预训练模型
```bash
mkdir models
cd models/
wget https://nlp.informatik.hu-berlin.de/resources/models/ner/en-ner-conll03-v0.4.pt
```

### 使用Hugging Face的国内镜像下载token分词器
```bash
export HF_ENDPOINT=https://hf-mirror.com
huggingface-cli download distilbert-base-uncased
```

### 安装gradio库
```bash
pip install gradio
```
