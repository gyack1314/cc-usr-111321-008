# 业务资料约定

所有数量是件数，day为整数日；known_at表示系统接收日。opening是原登记期初库存，调整另表保存。sold_out_early为现场确认提前售罄，unserved_complete说明未满足请求是否完整登记。

每行id在该表内唯一，文件顺序不代表业务事件顺序。清单schema=1，各表登记文件名、字节长度、SHA256、行数及完整字段集合，未知版本或内容变化应重新登记。金额及测量数值均为独立资料，不代表任何现实机构的经营数据。

- daily：id、part、day、opening、issued、receipts、open_hours、sold_out_early、unserved_known、unserved_complete、known_at。
- parts：id、family、lead_days。
- adjustments：id、part、day、kind、quantity、known_at。

normal与boundary是相互独立的资料包，不能直接拼接重复id。引用字段按本项目domain.py的REFERENCES登记。读取检查只检查完整性、身份及这些直接引用，不替代领域分析中的可识别性、时点可见性或可行性判断。
