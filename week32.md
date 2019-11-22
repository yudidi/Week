
# mysql ON DUPLICATE KEY UPDATE 引起自增ID变化的解决办法

https://blog.csdn.net/qq_33578832/article/details/87883371

# MathType的使用

# 礼券活动-数据库设计

https://www.google.com/search?q=%E7%A4%BC%E5%88%B8%E6%B4%BB%E5%8A%A8+%E6%95%B0%E6%8D%AE%E5%BA%93%E8%AE%BE%E8%AE%A1&oq=%E7%A4%BC%E5%88%B8%E6%B4%BB%E5%8A%A8+%E6%95%B0%E6%8D%AE%E5%BA%93%E8%AE%BE%E8%AE%A1&aqs=chrome..69i57j69i60.281j0j7&sourceid=chrome&ie=UTF-8


营销模块数据库表解析：优惠券功能
https://blog.csdn.net/zhenghongcs/article/details/99311734

优惠券的设计指南（一）：优惠券设计的整体框架
http://api.woshipm.com/pd/791895.html?sf=mobile/woshipm/791895?mobid=2YpIU

* 优惠券系统应该如何设计？

1. 使用跨职能流程图，表达主体业务逻辑

2. 数据分析

以下提供几个统计维度，仅供参考：

```
领取率：优惠券领取总量/优惠券发放总量；
使用率：优惠券已使用总量/优惠券已领取总量；
优惠总金额：使用该优惠券优惠的总金额；
用券总成交额：使用该优惠券的订单付款总金额；
优惠总金额：使用该优惠券的付款订单总数；
费效比：优惠总金额/用券总成交额；
用券笔单价：用券总成交额 / 使用该优惠券的付款订单总数；
拉新数：领取过优惠券的用户中，标记为新用户的数量/总用户数。
```

3. 数据分析页面

https://blog.csdn.net/varyall/article/details/81485435
