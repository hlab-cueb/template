# The Template for Hlab code

## Requirements(项目相关环境的要求，重要的在这个位置加以说明，其他的可以写入requirment)

- PyTorch 
- Python3 
- Numpy 

## 项目先关的说明和流程图（如果有图的话，可以加入流程图,下图为例子）
<p align="center">
<img src="./assert/sample.png" height = "360" alt="" align=center />
</p>

****
## Training （如果有模型的训练，加入的模型的训练方法，数据组成方式等，配置文件说明等）
### 1. 模型训练方式
参考 config.py查看相关的配置文件，如：
`python3 xx_train.py` 启动训练

### 2. Dataset
数据组织格式说明
数据组织例子（如有的话）(下面为例子)

```python
dataset = [{"input_key": [
  {"role": "user", "content": "Hello, how are you?"},
  {"role": "assistant", "content": "I'm doing great. How can I help you today?"},
  {"role": "user", "content": "I'd like to show off how chat templating works!"},
]}]

tokenizer.apply_chat_template(dataset[0]["input_key"], tokenize=False)

"<s>[INST] Hello, how are you? [/INST]I'm doing great. How can I help you today?</s> [INST] I'd like to show off how chat templating works! [/INST]"
```

### 3. 代码feature（列举代码相关的feature）
- [x] 完成初版的训练代码（完成）
- [x] 合并加入判别器和不加入判别器的训练方法（完成）
- [x] 拆分和dataset和配置文件（完成）
- [x] dataset的处理方法（完成），适合在在数据预处理中完成
- [x] 构建tensor的resize层，适应sync的部分
- [] 将对齐的方式加入到dataset中实时处理
- [] 对图像加入一些偏转的aug
- [] 提供的模型的确实判别器的权重，disc的权重

## Test（测试部分，测试集合和相关的指标说明）
`sh test.sh` 运行demo获取结果

### 项目补充说明部分
## 文件排布说明（这部分为例子，具体可以通过tree 当前目录得到）
```
|-train.py             #模型训练的代码
|-loss.py                         #训练loss的代码
|-dataset.py                      #加载数据部分代码
|-config.py                       #配置文件的代码
|-tools.py                        #相关的数据处理和存储文件的代码
|-weights                         #模型权重文件夹
|-test_inference_onnx.py          #测试onnx推理脚本
|-inference_onnx.py               #onnx推理脚本
|-inference_torch.py              #torch pth推理脚本
|
|-medels                          #网络文件
|  |-model.py                     #通用wav2lip网络结构   
|  |-conv.py                      #网络结构OP相关库
|
|-results                         #视频推理结果文件夹
|-utils.py                        #其他有用脚本——自定义函数脚本
|-README.md                       #说明文档

```
## Acknowledgement
Our implementation adapts [Time-Series-Library](https://github.com/thuml/Time-Series-Library) and [OFA (GPT4TS)](https://github.com/DAMO-DI-ML/NeurIPS2023-One-Fits-All) as the code base and have extensively modified it to our purposes. We thank the authors for sharing their implementations and related resources.
