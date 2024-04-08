# 简介

## 什么是 x-crawl ?

x-crawl 是一个灵活的 Node.js AI 辅助爬虫库。灵活的使用方式和强大的 AI 辅助功能，使爬虫工作变得更加高效、智能和便捷。

它由两部分组成：

- 爬虫：由爬虫 API 以及各种功能组成，即使不依靠 AI 也能正常工作。
- AI：目前基于 OpenAI 提供的 AI 大模型，让 AI 简化很多繁琐的操作。

> 如果您觉得 x-crawl 对您有所帮助，或者您喜欢 x-crawl ，可以在 GitHub 上给 [x-crawl 存储库](https://github.com/coder-hxl/x-crawl) 点个 star 。您的支持是我们持续改进的动力！感谢您的支持！

## 特征

- **🤖 AI 辅助** - 强大的 AI 辅助功能，使爬虫工作变得更加高效、智能和便捷。
- **🖋️ 写法灵活** - 单个爬取 API 都适配多种配置，每种配置方式都各有千秋。
- **⚙️ 多种用途** - 支持爬动态页面、静态页面、接口数据以及文件数据。
- **⚒️ 控制页面** - 爬取动态页面支持自动化操作、键盘输入、事件操作等。
- **👀 设备指纹** - 零配置或自定义配置，避免指纹识别从不同位置识别并跟踪我们。
- **🔥 异步同步** - 无需切换爬取 API 即可进行异步或同步的爬取模式。
- **⏱️ 间隔爬取** - 无间隔、固定间隔以及随机间隔，决定是否高并发爬取。
- **🔄 失败重试** - 自定义重试次数，避免因短暂的问题而造成爬取失败。
- **➡️ 轮换代理** - 搭配失败重试，自定义错误次数以及 HTTP 状态码自动轮换代理。
- **🚀 优先队列** - 根据单个爬取目标的优先级可以优先于其他目标提前爬取。
- **🧾 爬取信息** - 可控的爬取信息，会在终端输出彩色字符串信息。
- **🦾 TypeScript** - 拥有类型，通过泛型实现完整的类型。

## 示例

```js
// 1.导入模块 ES/CJS
import { createCrawl } from 'x-crawl'

// 2.创建一个爬虫实例
const crawlApp = createCrawl({
  maxRetry: 3,
  intervalTime: { max: 2000, min: 1000 }
})

// 3.设置爬取任务
// 调用 startPolling API 开始轮询功能，每隔一天会调用回调函数
crawlApp.startPolling({ d: 1 }, async (count, stopPolling) => {
  // 调用 crawlPage API 来爬取页面
  const pageResults = await crawlApp.crawlPage({
    targets: [
      'https://www.airbnb.cn/s/*/experiences',
      'https://www.airbnb.cn/s/plus_homes'
    ],
    viewport: { width: 1920, height: 1080 }
  })

  // 通过遍历爬取页面结果获取图片 URL
  const imgUrls = []
  for (const item of pageResults) {
    const { id } = item
    const { page } = item.data
    const elSelector = id === 1 ? '.i9cqrtb' : '.c4mnd7m'

    // 等待页面元素出现
    await page.waitForSelector(elSelector)

    // 获取页面图片的 URL
    const urls = await page.$$eval(`${elSelector} picture img`, (imgEls) =>
      imgEls.map((item) => item.src)
    )
    imgUrls.push(...urls.slice(0, 6))

    // 关闭页面
    page.close()
  }

  // 调用 crawlFile API 爬取图片
  await crawlApp.crawlFile({ targets: imgUrls, storeDirs: './upload' })
})
```

运行效果:

![](https://raw.githubusercontent.com/coder-hxl/x-crawl/main/assets/run-example.gif)

::: warning
x-crawl 仅供合法用途，禁止使用该工具进行任何违法活动，请务必遵守目标网站的 robots.txt 文件规定。网站的类名可能随时发生变更，本例仅用于演示 x-crawl 的使用方法，并非针对特定网站。
:::
