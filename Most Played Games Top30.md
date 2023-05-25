# Steam游戏在线人数历史峰值Top30(Most Played Games TOP30)
## 准备数据
正如我在数据源介绍时所说，我们获取数据的首选SteamDB上的Steam游戏在线人数历史峰值榜单页面并没有提供直接下载为.csv文件的渠道，使用Selenium包以及Chrome Drive浏览器驱动模拟浏览器打开SteamDB并手动完成安全验证的尝试也以失败告终，另外，Steam Charts页面的Top Records榜单仅显示前十名的有关数据，因此Steam数据统计网成为了我们爬取数据的唯一选择。
### 爬取数据
在这里我选择使用Edge浏览器自带的检查工具辅助构造XPath并爬取Steam游戏在线人数历史峰值榜单TOP500（一页包含50行数据）的游戏和在线峰值两列特征至列表name_list和peak_list中。
### 数据预处理
然而，现在获得的数据是有问题的：首先，两列数据除文字信息外还含有大量的空格，其次在线峰值一列的数据含有逗号分隔符。我们需要对数据进行清洗，具体方法是使用.strip()和.replace(“,”,“”)方法分别删除空格和逗号。
### 转换数据
将清洗过后的数据name_list和peak_list整合为Pandas包的DataFrame结构存储到MongoDB中。
