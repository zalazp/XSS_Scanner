# XSS_Scanner

XSS_Scanner 是 Burp Suite 的 XSS 自动化检测插件，支持反射 / DOM 型 XSS 扫描，集成 Payload 注入校验与 AI 判定，高效发现 XSS 漏洞。

## 下载

1.右方 Releases处,下载XSS_Scanner.zip文件夹压缩包,并解压

2.将 阿里云百炼的API Key 加入 系统环境变量(参考阿里云百炼网站文档详情)

https://bailian.console.aliyun.com/cn-beijing?tab=doc#/doc

![image-20260413160208569](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413160208569.png)

3.进入XSS_Scanner/XSS_Scanner_AI文件夹 执行

```
pip install -r requirements.txt
```

## 快速开始

### 1.将 XSS_Scanner.jar手动导入 burp extensions

- 自定义payload(添加配置自定义payload)
- 对自定义payload进行URL编码
- 加载/重新加载payload

![image-20260413161113022](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413161113022.png)

### 2.启用payload注入检测(Python服务器)

- 启用payload注入检测(Python服务器)![image-20260413161128188](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413161128188.png)

- 进入XSS_Scanner/XSS_Scanner_AI文件夹 执行

  ```
  python XSS_Scanner_AI.py
  ```

  ![image-20260413161344437](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413161344437.png)

- 点击"测试连接"

  ![image-20260413161531997](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413161531997.png)

### 3.测试网站抓包发送到XSS_Scanner插件

https://xssjs.com/yx/level1.php?name=test

![image-20260413163936393](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413163936393.png)

![image-20260413164259557](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413164259557.png)![image-20260413170719471](https://github.com/zalazp/XSS_Scanner/blob/main/imgs/image-20260413170719471.png)

该功能可通过AI 识别XSS的payload是否注入成功,

### 4.与传统插件相比优势,与手工注入相比的优势

| **特性**         | **传统插件（xssValidator）** | **XSS_Scanner**                        |
| ---------------- | ---------------------------- | -------------------------------------- |
| **Payload 类型** | 仅 `alert()` 等简单弹窗      | 支持鼠标/点击/悬停/DOM 等复杂 Payload  |
| **WAF 绕过能力** | 弱（容易被拦截）             | 强（避免常见关键字，模拟真实用户行为） |
| **用户交互模拟** | 不支持                       | 支持（点击、悬停、键盘输入等）         |
| **误报率**       | 高（静态匹配）               | 低（动态校验 + AI 判定）               |
| **适用场景**     | 简单反射型 XSS               | 反射型 + DOM 型 + 交互型 XSS           |

| 维度     | 手动测试            | AI 插件           | 优势总结                       |
| -------- | ------------------- | ----------------- | ------------------------------ |
| 效率     | 逐个发包，速度慢    | 多线程并发处理    | 速度极快，批量秒级完成         |
| 验证逻辑 | 肉眼查看特征        | AI 智能上下文分析 | 精准判断能否执行，大幅降低误报 |
| 结果判断 | 人工观察弹窗 / 报错 | AI 自动判定       | 全自动输出结果，无需值守       |
| 覆盖范围 | 仅测常用 payload    | 全量检测注入点    | 覆盖全面，不易遗漏漏洞         |
