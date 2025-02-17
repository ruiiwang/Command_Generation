# 指令数据集生成

使用GPT-4生成不同意图的指令，验证它们与原始意图的语义相似度，同时包括正样本和负样本。将验证通过的指令作为数据集，方便进行下一步训练。

## 项目结构

├── README.md</br>
├── config.yaml                                             // 配置文件，包含模型设置和指令列表</br>
├── environment.yml                                         // 环境需求</br>
├── generation.ipynb                                        // 数据集生成代码</br>
├── IntentDatasetCreation.ipynb                             // 包含OPENAI_API_KEY和调试结果的数据集生成代码</br>
├── prompts.yaml                                            // 用于生成和评分的模板提示词</br>
└── intent_dataset_outputs/                                 // 生成的数据集输出目录</br>
    ├── {instruction}_variations_{timestamp}.xlsx</br>
    ├── {instruction}_scores_{timestamp}.xlsx</br>
    ├── {instruction}_validated_{timestamp}.xlsx</br>
    └── ......xlsx</br>


## 文件内容

### 1. 配置文件 (config.yaml)
包含所有配置设置：
- 模型配置（GPT-4的生成和评分设置）
- 生成参数（数量、迭代次数、阈值）
- 指令列表

### 2. 提示词模板 (prompts.yaml)
- 正样本生成、评分
- 负样本生成、评分

### 3. 数据集生成代码 (generation.ipynb)
Jupyter Notebook:
- 加载配置，生成指令，对指令评分
- 输出文件处理
- 支持正样本和负样本生成


## 输出文件

每个指令生成三种Excel文件：
1. `{instruction}_variations_{timestamp}.xlsx`: 所有生成指令
2. `{instruction}_scores_{timestamp}.xlsx`: 评分结果
3. `{instruction}_validated_{timestamp}.xlsx`: 最终验证通过的指令
同时对每个分类生成正样本和负样本文件（带有negative）


## 使用方法

1. 在 `config.yaml` 中配置设置：
   - 设置模型参数
   - 定义指令列表
   - 调整生成数量和阈值

2. 运行Jupyter Notebook

3. 结果将保存在 `intent_dataset_outputs` 目录中


## 指令类别
当前支持的指令类别：
- photo: 相机/拍照指令
- video: 视频录制指令
- media: 媒体播放控制
- volume: 音量调节
- calling: 电话呼叫指令
- battery: 电池状态检查
- photo_chat: 视觉分析查询
