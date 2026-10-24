# MCP 集成说明

## MCP Server

- 服务提供方：麦当劳中国
- 地址：https://mcp.mcd.cn
- 协议：Streamable HTTP
- 认证：Authorization Bearer Token
- 配置示例：mcp-config.example.json

## 设计用途

本项目使用麦当劳 MCP 提供的实时业务数据，
帮助用户进行预算内点餐规划，而不是依靠模型记忆猜测价格。

## 计划使用的工具

| Tool | 用途 |
|---|---|
| query-meals | 查询当前门店可售餐品 |
| query-meal-detail | 查询套餐组成和替换选项 |
| query-store-coupons | 查询当前门店可用优惠券 |
| calculate-price | 计算候选组合的价格与优惠 |

工具参数与返回字段以实际 MCP Tool Schema 为准。

## 调用流程

1. 获取用户的预算、口味、人数及用餐方式。
2. 确定查询所需的门店信息。
3. 调用 query-meals 获取候选餐品。
4. 按需要调用 query-meal-detail 查看套餐详情。
5. 按需要调用 query-store-coupons 查询可用优惠。
6. 对候选组合调用 calculate-price 获取实际价格。
7. 根据实际返回结果筛选预算内方案并解释推荐理由。
8. 输出数据范围、计算结果及未能确认的事项。

## 安全边界

本项目不在公开代码中保存 Token。
第一版不执行创建订单、取消订单、支付或领券等操作。

## 实际验证记录

提交前请填写以下内容，不要把计划中的功能写成已完成的测试：

- MCP 连接结果：
- 实际成功调用的 Tool：
- 测试日期：
- 测试场景：
- 结果摘要（不得包含 Token 或个人信息）：
- 已知限制：

只有在真实连接并成功调用后，才能将相应功能标记为已验证。
