## 运行状态机

状态机是一个工作流。任务是工作流中的一种状态，工作流的每个步骤都是一种状态。

状态机用json描述：

```json
{
    "Comment": "this is a state machine",
    "StartAt": "Hello1",
    "States":{
        "Hello1":{
            "Type": "Pass",
            "Result": "hello world",
            "End": true
        }
    }
}
```



不断执行下一个状态直到系统达到最终状态。