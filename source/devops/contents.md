## 运行状态机

agent是一个工作流解释器。类似aws的step function。工作流由扩展过的yaml语言描述。由多个task组成。

```yaml
- "name": "test task"
  "type": "task"
  "resource": ""
  "fail_action": ""
  "input": ""
  "output": ""
  "when": ""
  "timeout": "30"
```

resource是去gitlab拉取最新代码执行。

每个task都会自动保存log，不用再去写保存日志的代码。

agent会自动获取环境信息作为上下文content，可以在工作流中直接调用。

外部参数可以通过固定json文件的方式输入，在工作流中调用。

agent在运行前会自动更新。

agent是被动agent，平时不会运行，等待被唤醒。运行结束后就停止。



## 运维开发标准化建设

URI结构：gitlab仓库地址:gitlab brunch:plugin name:function name

建设好gitlab仓库，master分支要严格保护，经过测试的代码才可以合并进来

plugin基于base plugin开发

单元测试

测试环境

跨环境：aws azure

多版本支持： 11.1 11.2

跨python版本：python2 python3

跨os：windows,linux



## jenkins新环境部署



## 环境升级