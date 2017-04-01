# 微吉风

在经历 BBS、Wiki、Blog、公众号的失败后，我转身投入了小程序。或许，这是在校最后一次干自己喜欢的事了。


## 功能

- [x] 课表
- [ ] ……

当 XX 转型主打聊天交友后，我再也没用过课表软件。

除了课表，不知道还有啥功能需求。


## 截图

![示例](/Screenshots.jpg)


## 更新记录

### v0.1.0 (2017-04-01)

- 项目发布


## 说明

### courseTop 计算方法「[/pages/index/index.js](/pages/index/index.js#L7)」

| 第几节 | style.top / 单位 rpx            | 即                  |
|:------:|:--------------------------------|:--------------------|
| 1      | (1-1) * 200                     | (1-1) * 210         |
| 2      | (2-1) * 200 + 10                | (2-1) * 210         |
| 3      | (3-1) * 200 + 10 + 15           | (3-1) * 210 + 5     |
| 4      | (4-1) * 200 + 10 + 15 + 10      | (4-1) * 210 + 5     |
| 5      | (5-1) * 200 + 10 + 15 + 10 + 15 | (5-1) * 210 + 5 + 5 |


### 服务器返回的课程数据格式

一维天数：对应周一至周日。

二维节数：对应第一大节至第五大节；`1, 2`、`3, 4`、`5, 6`、`7, 8`、`9, 10`；第五大节一般是 `9, 10`，但有的课程会是 `9, 10, 11`，~~丧心病狂~~。

三维课程：有单双周课程之分时，此处有两个元素。

四维课程详细信息：按顺序分别是课程名称、周期、任课教师、教室；`1-16-0` 表示 `开始周-结束周-单双周`，其中单双周为 0 表示不区分，1 表示单，2 表示双。

```
Array
(
    [1] => Array
        (
            [1] => Array
                (
                    [0] => Array
                        (
                            [0] => 哲学
                            [1] => 1-16-0    // 第 1 周至第 16 周 每周都上
                            [2] => 张三
                            [3] => 101
                        )
                )
            [3] => Array
                (
                    ……
                )
            ……
        )
    [2] => Array
        (
            [1] => Array
                (
                    [0] => Array
                        (
                            [0] => 心理学
                            [1] => 1-15-1    // 第 1 周至第 15 周 单周上
                            [2] => 李四
                            [3] => 102
                        )
                    [1] => Array
                        (
                            [0] => 文学
                            [1] => 2-16-2    // 第 2 周至第 16 周 双周上
                            [2] => 王五
                            [3] => 103
                        )
                )
            ……
        )
    ……
)
```


## 许可

WTFPL.