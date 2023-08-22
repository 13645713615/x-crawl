# [v8.0.0](https://github.com/coder-hxl/x-crawl/compare/v7.1.3...v8.0.0) (2023-08-22)

### 🚨 Breaking Changes

- update dependencies

  - puppeteer from 19.10.0 to 21.1.0.
  - https-proxy-agent upgraded from 5.0.1 to 7.0.1.

- XCrawlConfig.crawlPage's launchBrowser option renamed to puppeteerLaunch .

---

### 🚨 重大改变

- 更新依赖

  - puppeteer 从 19.10.0 升至 21.1.0 。
  - https-proxy-agent 从 5.0.1 升至 7.0.1 。

- XCrawlConfig.crawlPage 的 launchBrowser 选项更名为 puppeteerLaunch 。

# [v7.1.3](https://github.com/coder-hxl/x-crawl/compare/v7.1.2...v7.1.3) (2023-07-02)

### 🐞 Bug fixes

- The crawlData API writes the correct data to the request body and processes the response body.

---

### 🐞 漏洞修复

- crawlData API 将正确的 data 写入请求体以及处理响应体。

# [v7.1.2](https://github.com/coder-hxl/x-crawl/compare/v7.1.1...v7.1.2) (2023-06-25)

### 🐞 Bug fixes

- Data parameter option conversion issue for crawlData API.

---

### 🐞 漏洞修复

- crawlData API 的 data 参数选项转换问题。

# [v7.1.1](https://github.com/coder-hxl/x-crawl/compare/v7.1.0...v7.1.1) (2023-06-21)

### 🐞 Bug fixes

- Correctly handle the header of the post method configured by the crawlData API.

---

### 🐞 漏洞修复

- 正确处理 crawlData API 配置 post 方法的 header 。

# [v7.1.0](https://github.com/coder-hxl/x-crawl/compare/v7.0.1...v7.1.0) (2023-05-15)

### 🚀 Features

- The flexibility of crawlFile API has been upgraded again, mainly adjusting fileName, storeDir, and extension.
  - The storeDir and extension of the advanced writing method (CrawlFileAdvancedConfig) are changed to storeDirs and extensions respectively, and the type is string or (string | null)[], and the fileNames option is added, and the type is (string | null)[] . If it is an array, it will be assigned to the crawling targets in order.
  - The fileName of the detailed target notation (CrawlFileDetailTargetConfig) adds a null type, which is used to use the default file name instead of the fileName corresponding to the advanced notation (CrawlFileAdvancedConfig) fileNames.

---

### 🚀 特征

- crawlFile API 灵活度再次升级，主要对 fileName、storeDir、extension 进行调整。
  - 进阶写法 (CrawlFileAdvancedConfig) 的 storeDir 和 extension 分别更改为 storeDirs 和 extensions ，类型为 string 或者 (string | null)[]，同时新增 fileNames 选项，类型为 (string | null)[] 。如果是数组则会按顺序分配给爬取目标。
  - 详细目标写法 (CrawlFileDetailTargetConfig) 的 fileName 新增 null 类型，用于使用默认文件名，不使用进阶写法 (CrawlFileAdvancedConfig) fileNames 对应的 fileName 。

# [v7.0.1](https://github.com/coder-hxl/x-crawl/compare/v7.0.0...v7.0.1) (2023-05-04)

### 🐞 Bug fixes

- The params configuration option for the crawlData API is not working.

---

### 🐞 漏洞修复

- crawlData API 的 params 配置选项不起作用。

# [v7.0.0](https://github.com/coder-hxl/x-crawl/compare/v6.0.1...v7.0.0) (2023-04-26)

### 🚨 Breaking Changes

- Fingerprint upgrade:
  - The fingerprint of the advanced writing method is renamed to fingerprints, which is an array writing method, which stores objects of the DetailTargetFingerprintCommon type, which is convenient for customization. Internally, the objects inside will be randomly assigned to the target.
  - Adjustment of crawlPage fingerprint options: the maximum width and height of the fingerprint configuration of advanced writing and detailed target writing are changed to optional.
- Proxy upgrade: create a crawler instance, change the proxy of the advanced writing method and the detailed target writing method to the object writing method, with three attributes: urls, switchByHttpStatus and switchByErrorCount, urls can set multiple proxy URLs, and the internal default uses the first one first, switchByHttpStatus Set which non-compliant response status codes need to switch the proxy, and switchByErrorCount sets how many times the proxy needs to be switched when errors such as timeouts arrive. The proxy rotation feature needs to be used with error retries.
- Return value type adjustment: CrawlCommonRes, CrawlPageSingleRes, CrawlDataSingleRes and CrawlFileSingleRes are renamed to CrawlCommonResult, CrawlPageSingleResult, CrawlDataSingleResult and CrawlFileSingleResult respectively

### 🚀 Features

- It is possible to cancel the configuration of the upper-level unified setting by setting null in the option.
- The userAgent option in DetailTargetFingerprintCommon overrides the object notation and allows customization of the maximum and minimum values of the major version, minor version, and revision number inside. Each crawl target gets a new userAgent .
- A new proxyDetails property is added to the crawling results to record the proxy status.
- Added 'random' attribute value to mobile option of fingerprint configuration, allowing internal randomization.
- Terminal prompts are simplified and color adjusted.

### 🐞 Bug fixes

- Unable to create multiple levels of non-existent folders on linux systems.

---

### 🚨 重大改变

- 指纹升级：
  - 进阶写法的 fingerprint 改名为 fingerprints ，为数组写法，里面存放 DetailTargetFingerprintCommon 类型的对象，方便定制。内部会将里面的对象随机分配给目标。
  - crawlPage 的指纹选项调整：进阶写法和详细目标写法的指纹配置的最大宽高改为可选项。
- 代理升级：创建爬虫实例、进阶写法以及详细目标写法的 proxy 更改为对象写法, 拥有 urls、switchByHttpStatus 以及 switchByErrorCount 这三个属性，urls 可以设置多个代理 URL ，内部默认先采用第一个，switchByHttpStatus 设置遇到哪些不符合的响应状态码需要切换代理，switchByErrorCount 设置像超时等错误时到达多少次需要切换代理。该代理轮换功能需要配合错误重试才能使用。
- 返回值类型调整：CrawlCommonRes、CrawlPageSingleRes、CrawlDataSingleRes 以及 CrawlFileSingleRes 分别更名为 CrawlCommonResult、CrawlPageSingleResult、CrawlDataSingleResult 以及 CrawlFileSingleResult

### 🚀 特征

- 可以通过在选项设置为 null 取消上级统一设置的配置。
- DetailTargetFingerprintCommon 里的 userAgent 选项改写对象写法，并允许定制里面的主版本、次版本以及修订号的最大值和最小值。每个爬取目标都会获取一个新的 userAgent 。
- 爬取结果新增 proxyDetails 属性，记录代理状态。
- 指纹配置的 mobile 选项添加 'random' 属性值，允许由内部随机决定。
- 终端提示信息进行简化以及颜色调整。

### 🐞 漏洞修复

- 在 linux 系统上无法创建多级不存在的文件夹。

# [v6.0.1](https://github.com/coder-hxl/x-crawl/compare/v6.0.0...v6.0.1) (2023-04-21)

### 🚀 Features

- Perfect documentation.

---

### 🚀 特征

- 完善文档。

# [v6.0.0](https://github.com/coder-hxl/x-crawl/compare/v5.1.0...v6.0.0) (2023-04-19)

### 🚨 Breaking Changes

- About the result processing of each crawling target: it will start processing after a single target is completed, saving time and improving performance. Originally, it waited for all targets to be completed before processing, and there would be free time during the crawling process.
- About the execution timing of the second parameter callback function of the crawlPage, crawlData, and crawlFile APIs: it will be executed at the end, and the result obtained is the same as the result of the Promise method.
- About the type: PageRequestConfig, DataRequestConfig and FileRequestConfig are changed to CrawlPageDetailTargetConfig, CrawlDataDetailTargetConfig and CrawlFileDetailTargetConfig respectively, the purpose is to not only add the configuration of the request, but also expand more, called detailed target usage. CrawlPageConfigObject, CrawlDataConfigObject, and CrawlFileConfigObject changed to CrawlPageAdvancedConfig, CrawlDataAdvancedConfig, and CrawlFileAdvancedConfig respectively, named Advanced Usage.
- Configuration options in fileConfig of crawlFile: can be set directly in the root object configuration. The beforeSave lifecycle function changed to onBeforeSaveItemFile.
- About the object results of crawlPage, crawlData and crawlFile: remove the crawlCount attribute, and get the number of times by retryCount + 1. errorQueue was renamed to crawlErrorQueue.

### 🚀 Features

- Added device fingerprint to avoid identifying and tracking us from different locations through fingerprint recognition. You can use the default with a switch, and if you need to specify it, you can set it uniformly for all crawling targets in the advanced usage, or you can specify the settings through the detailed target usage.
- Adding multiple attributes for each advanced usage can be configured in an advanced way to set the object uniformly, without having to set it repeatedly for each target configuration. The new onCrawlItemComplete lifecycle function will be executed after each crawling goal is completed, and the result of the crawling goal will be passed to the callback function.
- Added crawlPage in the configuration of creating a crawler application, you can set the configuration of creating a browser in the crawlPage.launchBrowser option (type is PuppeteerLaunchOptions from Puppeteer).
- crawlPage adds viewport option, which is used to set the viewport of the page.

---

### 🚨 重大改变

- 关于对每个爬取目标的结果处理：将会在单个目标完成后就开始进行处理，节省时间，提高性能。原先是等所有目标完成再处理，在爬过程中会有空闲时间。
- 关于 crawlPage、crawlData 以及 crawlFile 这三个 API 的第二个参数回调函数的执行时机：将移到最后执行，获取的结果跟 Promise 方式的结果相同。
- 关于类型：PageRequestConfig、DataRequestConfig 以及 FileRequestConfig 分别更改为 CrawlPageDetailTargetConfig、CrawlDataDetailTargetConfig 以及 CrawlFileDetailTargetConfig ，目的是为了不单单可以加请求的配置，也可以扩展更多，名为详细目标用法。CrawlPageConfigObject、 CrawlDataConfigObject 以及 CrawlFileConfigObject 分别更改为 CrawlPageAdvancedConfig、CrawlDataAdvancedConfig 以及 CrawlFileAdvancedConfig ，名为进阶用法。
- 关于 crawlFile 的 fileConfig 里面的配置选项：可以直接在根对象配置中设置。beforeSave 生命周期函数更改为 onBeforeSaveItemFile。
- 关于 crawlPage、crawlData 以及 crawlFile 的对象结果：移除 crawlCount 属性，可通过 retryCount + 1 获取次数。errorQueue 更名为 crawlErrorQueue。

### 🚀 特征

- 新增设备指纹，可避免通过指纹识别从不同位置识别并跟踪我们。可以通过一个开关使用默认的，如果需指定则可在进阶用法中为所有爬取目标统一设置，也可以通过详细目标用法指定设置。
- 每个进阶用法新增多个属性可以在进阶方式配置对象统一设置，不必为每个目标配置重复设置一遍。新增 onCrawlItemComplete 生命周期函数，将在每个爬取目标完成后执行，并且把爬取目标的结果传入回调函数。
- 在创建爬虫应用的配置新增 crawlPage ，可以在 crawlPage.launchBrowser 选项中设置创建浏览器的配置（类型为 PuppeteerLaunchOptions 来自 Puppeteer）。
- crawlPage 新增 viewport 选项，用于设置页面的视口。

# [v5.1.0](https://github.com/coder-hxl/x-crawl/compare/v5.0.2...v5.1.0) (2023-04-12)

### 🚨 Breaking Changes

- The beforeSave lifecycle function of crawlFile needs to return a Promise and resolve is a Buffer .

### 🚀 Features

- The description, characteristics and type of the document change.

### 🐞 Bug Fixes

- Incorrect type hints and type restrictions, using overloaded functions instead.

---

### 🚨 重大改变

- crawlFile 的 beforeSave 生命周期函数需要返回一个 Promise 并且 resolve 是 Buffer 。

### 🚀 特征

- 文档的描述、特征和类型发生变化。

### 🐞 漏洞修复

- 错误的类型提示和类型限制，改用重载函数。

# [v5.0.2](https://github.com/coder-hxl/x-crawl/compare/v5.0.1...v5.0.2) (2023-04-10)

### 🚀 Features

- When a retry is added, the number of retry batches is displayed in print.

---

### 🚀 特征

- 新增重试时，重试批次数将显示在打印中。

# [v5.0.1](https://github.com/coder-hxl/x-crawl/compare/v5.0.0...v5.0.1) (2023-04-08)

### 🚀 Features

- New adjustments to the document.

---

### 🚀 特征

- 文档新的调整。

# [v5.0.0](https://github.com/coder-hxl/x-crawl/compare/v4.0.1...v5.0.0) (2023-04-06)

### 🚨 Breaking Changes

- For configuration, major changes have been made to each crawling API configuration, and the same API supports more crawling configuration methods, each of which has its own significance.
- For the result, the result of each request will be wrapped in an object, which provides information about the result of this request, such as: id, result, success, maximum retry, number of retries, collected error information, etc. . Automatically determine whether the return value is wrapped in an array according to the configuration method you choose, and the type is perfectly matched in TS.
- For obtaining results through the callback function, the callback is no longer executed after a single request is completed like the v4.x version, but will be executed sequentially after the crawling is completed, which will not block subsequent crawling.

### 🚀 Features

- Added a retry mechanism, which can be set for all crawling requests, for a single crawling request, and for a single request.
- A new priority queue is added to use priority crawling according to the priority of a single request.
- For more configurations that may be reused, you can set the baseConfig settings passed in when requesting configuration, API crawling configuration, and generating crawler instances, such as: timeout, proxy, intervalTime, etc., and the weight is: requestConfig > APIConfig > baseConfig.
- For crawlFile API, file path, name, suffix and other information can be set individually for each file. Added the beforeSave life cycle function before saving the file. You can get the file data of the Buffer type, and you can perform operations such as compression on the data in the callback. The returned new Buffer data will replace the original data and write it into the file.
- Update the output of crawling on the console, and collect the error information generated by crawling into an error queue. After the crawling is completed, you can get the error message queue through the return value.

---

### 🚨 重大改变

- 对于配置，每个爬取 API 配置发生重大改变，同一个 API 支持更多爬取配置方式，每种方式都有其存在的意义。
- 对于结果，每个请求的结果将统一使用对象包裹着，该对象提供了关于这次请求结果的信息，比如：id、结果、是否成功、最大重试、重试次数、收集到错误信息等。自动根据你选用的配置方式决定返回值是否包裹在一个数组中，在 TS 中类型完美适配。
- 对于通过回调函数方式获取结果，该回调不再像 v4.x 版本在单个请求完成后执行，而是将会在爬取完成后按顺序执行，这将不会阻塞后续的爬取。

### 🚀 特征

- 新增失败重试，可针对所有爬取的请求设置，针对单次爬取的请求设置，针对单个请求设置进行失败重试。
- 新增优先队列，根据单个请求的优先级使用优先爬取。
- 对更多可能复用的配置可以在请求配置、API 爬取配置、生成爬虫实例时传入的 baseConfig 设置，比如：timeout、proxy、intervalTime 等，权重为：requestConfig > APIConfig > baseConfig。
- 对 crawlFile API 可单独为每个文件设置文件路径、名字、后缀等信息。新增 beforeSave 文件保存前生命周期函数，可拿到 Buffer 类型的文件数据，可在回调内对数据进行压缩等操作，返回新的 Buffer 数据会替代原先的数据写入文件中。
- 对爬取在控制台的输出更新，对爬取产生的报错信息分别收集到一个的错误队列中，爬取完成后可通过返回值拿到该错误信息队列。

# [v4.0.1](https://github.com/coder-hxl/x-crawl/compare/v4.0.0...v4.0.1) (2023-03-30)

### 🐞 Bug Fixes

- The page is not closed when there is an error in the crawlPage API

# [v4.0.0](https://github.com/coder-hxl/x-crawl/compare/v3.3.0...v4.0.0) (2023-03-27)

### 🚨 Breaking Changes

- The crawlPage API can add batch requests.
- The crawlPage API remove JSDOM.

### 🚀 Features

- Document updates.

# [v3.3.0](https://github.com/coder-hxl/x-crawl/compare/v3.2.12...v3.3.0) (2023-03-24)

### 🚀 Features

- The crawlerPage API crawling page allows to carry Cookies (for login and other operations).

# [v3.2.12](https://github.com/coder-hxl/x-crawl/compare/v3.2.11...v3.2.12) (2023-03-23)

### 🐞 Bug Fixes

- Document jump fix

# [v3.2.11](https://github.com/coder-hxl/x-crawl/compare/v3.2.10...v3.2.11) (2023-03-22)

### 🚀 Features

- Test updates, unit test all APIs

### 🐞 Bug Fixes

- Fix crawlPage API internal error

# [v3.2.10](https://github.com/coder-hxl/x-crawl/compare/v3.2.9...v3.2.10) (2023-03-21)

### 🚀 Features

- Update documents

# [v3.2.9](https://github.com/coder-hxl/x-crawl/compare/v3.2.8...v3.2.9) (2023-03-20)

### 🚀 Features

- Update dependency

# [v3.2.8](https://github.com/coder-hxl/x-crawl/compare/v3.2.7...v3.2.8) (2023-02-19)

### 🐞 Bug Fixes

- Internal type adjustment.
- Catch crawlPage API errors.

# [v3.2.7](https://github.com/coder-hxl/x-crawl/compare/v3.2.6...v3.2.7) (2023-03-14)

### 🚀 Features

- Update documents

# [v3.2.6](https://github.com/coder-hxl/x-crawl/compare/v3.2.5...v3.2.6) (2023-03-14)

### 🚀 Features

- Update documents

# [v3.2.5](https://github.com/coder-hxl/x-crawl/compare/v3.2.4...v3.2.5) (2023-03-12)

### 🚀 Features

- Update documents

# [v3.2.4](https://github.com/coder-hxl/x-crawl/compare/v3.2.3...v3.2.4) (2023-03-09)

### 🚀 Features

- Update documents

# [v3.2.3](https://github.com/coder-hxl/x-crawl/compare/v3.2.2...v3.2.3) (2023-03-08)

### 🚀 Features

- Update documents

# [v3.2.2](https://github.com/coder-hxl/x-crawl/compare/v3.2.1...v3.2.2) (2023-03-07)

### 🚀 Features

- Update documents

# [v3.2.1](https://github.com/coder-hxl/x-crawl/compare/v3.2.0...v3.2.1) (2023-03-07)

### 🚀 Features

- Update documents

# [v3.2.0](https://github.com/coder-hxl/x-crawl/compare/v3.1.1...v3.2.0) (2023-03-06)

### 🚀 Features

- crawlPage API return value update

### 🐞 Bug Fixes

- The result page of crawlPage API reported an error. Expose the browser and let the user decide to close the browser

# [v3.1.1](https://github.com/coder-hxl/x-crawl/compare/v3.1.0...v3.1.1) (2023-02-05)

### 🐞 Bug Fixes

- publish type is missing

# [v3.1.0](https://github.com/coder-hxl/x-crawl/compare/v3.0.0...v3.1.0) (2023-03-05)

### 🚀 Features

- The callback function adds a stopPolling parameter, which can be called to stop subsequent polling operations. The stop polling of the startPolling API is determined by the user

- Update documents

# [v3.0.0](https://github.com/coder-hxl/x-crawl/compare/v2.4.2...v3.0.0) (2023-03-04)

### 🚨 Breaking Changes

- The three APIs fetchPage, fetchData, and fetchFile are renamed to crawlPage, crawlData, and crawlFile respectively

### 🚀 Features

- Multiple ways of writing requestConfig options

- All types are exposed

# [v2.4.2](https://github.com/coder-hxl/x-crawl/compare/v2.4.1...v2.4.2) (2023-03-04)

### 🚀 Features

- Update documents

# [v2.4.1](https://github.com/coder-hxl/x-crawl/compare/v2.4.0...v2.4.1) (2023-03-04)

### 🐞 Bug Fixes

- Interval time doesn't work

# [v2.4.0](https://github.com/coder-hxl/x-crawl/compare/v2.3.0...v2.4.0) (2023-03-03)

### 🚀 Features

- Update documents

# [v2.3.0](https://github.com/coder-hxl/x-crawl/compare/v2.2.1...v2.3.0) (2023-03-02)

### 🚨 Breaking Changes

- fetchHTML API rename fetchPage

# [v2.2.1](https://github.com/coder-hxl/x-crawl/compare/v2.2.0...v2.2.1) (2023-03-01)

### 🚀 Features

- Update documents

# [v2.2.0](https://github.com/coder-hxl/x-crawl/compare/v2.1.0...v2.2.0) (2023-02-28)

### 🚀 Features

- Parameter config name correction
- Update documents

# [v2.1.0](https://github.com/coder-hxl/x-crawl/compare/v2.0.0...v2.1.0) (2023-02-28)

### 🚀 Features

- The fetchHTML API results remove content options
- The fetchHTML API cancels the incoming header attribute
- The running mode of crawling is highlighted

# [v2.0.0](https://github.com/coder-hxl/x-crawl/compare/v1.1.1...v2.0.0) (2023-02-27)

### 🚨 Breaking Changes

- Create a crawler method, created by calling
- The fetchHTML API uses puppeteer to crawl HTML
- The fetchPolling API renamed to startPolling, removed year and month

# [v1.1.1](https://github.com/coder-hxl/x-crawl/compare/v1.1.0...v1.1.1) (2023-02-22)

### 🚀 Features

- Add jump to a detailed type

# [v1.1.0](https://github.com/coder-hxl/x-crawl/compare/v1.0.1...v1.1.0) (2023-02-21)

### 🚀 Features

- The fetchFile API uses async for save file operations and sorts errors
- The fetchFile API fileConfig can pass in non-existing path

# [v1.0.1](https://github.com/coder-hxl/x-crawl/compare/v1.0.0...v1.0.1) (2023-02-20)

### 🚀 Features

- Sorting of error messages and fetchData/fetchFile API results

# [v1.0.0](https://github.com/coder-hxl/x-crawl/compare/v0.4.0...v1.0.0) (2023-02-17)

### 🚨 Breaking Changes

- Added the method of getting the request result through the callback function, The result of each request can be obtained through the callback function, and the total result can be obtained through PromIse
- API internal refactoring

# [v0.4.0](https://github.com/coder-hxl/x-crawl/compare/v0.3.1...v0.4.0) (2023-02-16)

### 🚀 Features

- The fetchFile API config can provide the extension of the downloaded file

# [v0.3.1](https://github.com/coder-hxl/x-crawl/compare/v0.3.0...v0.3.1) (2023-02-10)

### 🚀 Features

- Update documents

# [v0.3.0](https://github.com/coder-hxl/x-crawl/compare/v0.2.0...v0.3.0) (2023-02-10)

### 🚨 Breaking Changes

- Rename the data object raw of fetchHTML return value to html

### 🚀 Features

- Add proxy option

# [v0.2.0](https://github.com/coder-hxl/x-crawl/compare/v0.1.5...v0.2.0) (2023-02-09)

### 🚀 Features

- Add polling function

# [v0.1.5](https://github.com/coder-hxl/x-crawl/compare/v0.1.4...v0.1.5) (2023-02-05)

### 🐞 Bug Fixes

- Fix fetchFile API file save is lost

# [v0.1.4](https://github.com/coder-hxl/x-crawl/compare/v0.1.3...v0.1.4) (2023-02-05)

### 🚀 Features

- Add chalk library

# [v0.1.3](https://github.com/coder-hxl/x-crawl/compare/v0.1.2...v0.1.3) (2023-02-05)

### 🚀 Features

- fetchHTML API exposes more content

# [v0.1.2](https://github.com/coder-hxl/x-crawl/compare/v0.1.1...v0.1.2) (2023-02-02)

### 🚀 Features

- Add requst mode option: async/sync
- Document adjustment

# [v0.1.1](https://github.com/coder-hxl/x-crawl/compare/v0.1.0...v0.1.1) (2023-01-31)

### 🚀 Features

- fetchHTML API parameter can be Object type

# [v0.1.0](https://github.com/coder-hxl/x-crawl/compare/v0.0.3...v0.1.0) (2023-01-30)

### 🚀 Features

- fetch API renamed to fetchData API
- fetchData and fetchFile request handling

# [v0.0.3](https://github.com/coder-hxl/x-crawl/compare/v0.0.2...v0.0.3) (2023-01-29)

### 🚀 Features

- Request Protocol
- Use jest test

# [v0.0.2](https://github.com/coder-hxl/x-crawl/compare/v0.0.1...v0.0.2) (2023-01-28)

### 🐞 Bug Fixes

- Add jsdom type

- Combined configuration when the basic configuration is not undefined will be processed

# v0.0.1 (2023-01-28)

### 🚀 Features

- Feat：First release of x-crawl
