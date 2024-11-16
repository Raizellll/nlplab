基于LLM的命名实体识别和摘要任务
模型:

- Owen2.5-0.5B-Instruct

- https://huggingface.co/Owen/Owen2.5-0.5B-Instruct

任务:通过设计 prompt 引导模型完成下游任务

- 命名实体识别任务

  - CHisIEC 古文命名实体识别数据集

  - https://github.com/tangxuemei1995/CHisIEC/blob/main/data/ner/test.txt


- 中文新闻摘要任务

  - CNewSum: A Large-scale Chinese News Summarization Dataset with Human-annotated Adequacy and Deducibility Level

    {

    ​		"article": ["庆阳市 气象台 2016年 7月 14 日 15 时 40 分 发布 雷电 黄色 预警 信号 : 预计 今天 下午 到夜间 我市 大部分 地方 将 有 雷电 活动 ，局地 伴有 短时 强降水 、阵性 大风 等 天气 ，请 注意 防范 。"，"图例标准 防御 指南 6 小时 内 可能 发生 雷电 活动 ，可能 会 造成 雷电 灾害 事故 。"，"1、政府 及 相关 部门 按照职责 做好 防雷 工作 ;2、密切 关注 天气 ，尽量 避免 户外活动 。"]，

    ​		"summary": "庆阳市 发布 雷电 黄色 预警 : 预计 今天 下午 到 夜间 我市 大部分 地方 将 有 雷电 活动 ，局地伴有……“

    }

- 必做1:

  •使用模型完成**命名实体识别**任务，并与原来的方法得到的结果进行对比（指标为F1-macro），要求分析各自的优劣

- 必做2:

  •使用模型完成**摘要**任务，使用不同指标（ROUGE-1，ROUGE-2）进行评价，并简单进行案例分析，说明完成的效果及提升的空间

- •选做：

  •使用更大规模模型、有条件可尝试微调、其他认为值得探索的要点

•提交文件：学号-姓名.ipynb





### How to use from the[Transformers](https://huggingface.co/docs/hub/transformers)library



Copy

```
# Use a pipeline as a high-level helper
from transformers import pipeline

messages = [
    {"role": "user", "content": "Who are you?"},
]
pipe = pipeline("text-generation", model="Qwen/Qwen2.5-0.5B")
pipe(messages)
```

Copy

```
# Load model directly
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("Qwen/Qwen2.5-0.5B")
model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen2.5-0.5B")
```