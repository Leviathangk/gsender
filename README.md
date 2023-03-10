# galarm

一个消息发送合集，有以下模块

- EmailSender：邮件发送
- DingTalkSender：钉钉群聊机器人

# EmailSender

有以下参数

- receiver：接收者（可以是列表）
- content_text：邮件内容
- content_html：邮件内容（html 形式）
- files：文件路径（可以是列表）

【示例】

```
sender = EmailSender(user='xxx', pwd='xxx')
sender.send(receiver='', content_text='这是一封测试邮件')
```

# DingTalkSender

支持钉钉所有消息类型消息发送  
了解链接：https://open.dingtalk.com/document/group/message-types-and-data-format#topic-2098229

【示例】

```
d = DingTalkSender(secret=DING_TALK_SECRET, access_token=DING_TALK_ACCESS_TOKEN)

d.send_text(content='测试消息', at_all=True)

d.send_text(content='测试消息', at_mobiles='xxx')

d.send_markdown(title='test', text='测试消息')

d.send_link(title='test', text='测试消息', message_url="https://www.baidu.com/")

d.send_feed_card(links=[
    {
        "title": "时代的火车向前开1",
        "messageURL": "https://www.dingtalk.com/",
        "picURL": "https://img.alicdn.com/tfs/TB1NwmBEL9TBuNjy1zbXXXpepXa-2400-1218.png"
    },
    {
        "title": "时代的火车向前开2",
        "messageURL": "https://www.dingtalk.com/",
        "picURL": "https://img.alicdn.com/tfs/TB1NwmBEL9TBuNjy1zbXXXpepXa-2400-1218.png"
    }
])

d.send_action_card_only(**{
    "title": "乔布斯 20 年前想打造一间苹果咖啡厅，而它正是 Apple Store 的前身",
    "text": "![screenshot](https://img.alicdn.com/tfs/TB1NwmBEL9TBuNjy1zbXXXpepXa-2400-1218.png) \n\n #### 乔布斯 20 年前想打造的苹果咖啡厅 \n\n Apple Store 的设计正从原来满满的科技感走向生活化，而其生活化的走向其实可以追溯到 20 年前苹果一个建立咖啡馆的计划",
    "btn_orientation": 0,
    "btns": [
        {
            "title": "内容不错",
            "actionURL": "https://www.dingtalk.com/"
        },
        {
            "title": "不感兴趣",
            "actionURL": "https://www.dingtalk.com/"
        }
    ]
})
```