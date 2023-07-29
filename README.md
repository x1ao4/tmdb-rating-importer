# tmdb-rating-importer
使用 tmdb-rating-importer 可以通过读取文本文件中的评分数据，使用 TMDb API 将评分上传到 [TMDb](https://www.themoviedb.org/) 网站，把评分数据导入 TMDb 账号。

## 功能演示
假设您有一个名为 `ratings.txt` 的文本文件，其中包含一些电影/电视节目的评分数据。

`ratings.txt` 的内容如下：
```
肖申克的救赎 (1994): 5
这个杀手不太冷 (1994): 4
阿甘正传 (1994): 5
霸王别姬 (1993): 5
美丽人生 (1997): 4
```
您希望将这些评分数据导入到您的 TMDb 账号中。

运行 tmdb-rating-importer.py 脚本后，脚本会自动读取文本文件中的评分数据，并使用 TMDb API 将评分上传到 TMDb 网站，使用您的账号将这些影片评价为对应的星级。

## 运行条件
- 安装了 Python 3.0 或更高版本。
- 安装了必要的第三方库：requests 和 BeautifulSoup。
- 有可用的 TMDb 账号。
- 有可用的 TMDb API。（TMDb API 可在 TMDb 账号设置中免费申请）

## 使用方法
1. 将仓库克隆或下载到计算机上的一个目录中。
2. 在脚本中设置您的 TMDb API 密钥、用户名和密码，将 `api_key`、`username` 和 `password` 变量的值更改为您的 TMDb API 密钥、用户名和密码。
3. 将评分数据整理为功能演示中的提供的格式，保存为 `ratings.txt` 文件，并放在与脚本相同的目录中。
4. 修改 `start.command (Mac)` 或 `start.bat (Win)` 中的路径，以指向您存放 `tmdb-rating-importer.py` 脚本的目录。
5. 双击运行 `start.command` 或 `start.bat` 脚本以执行 `tmdb-rating-importer.py` 脚本。
6. 脚本将开始读取文本文件中的评分数据，并使用 TMDb API 将评分上传到 TMDb 网站。
7. 在脚本运行过程中，您可以在控制台中看到每部影片的名称和评分以及上传状态。
8. 脚本运行完成后，您可以在 TMDb 网站上查看所有电影/电视节目的评分数据。

## 注意事项
- 由于 TMDb API 有速率限制，建议在脚本运行过程中不要进行其他与 TMDb API 相关的操作，以免触发速率限制。
- 评分数据需要按上文提供的格式进行整理。
- 脚本会在评分成功后删除文本文件中对应的数据，运行结束后，只有评分失败的数据会保留在文件中，在运行脚本之前，请备份原始的数据文件，以防数据丢失。
- 此脚本的初衷是将豆瓣评分数据导入 TMDb，由于豆瓣的评分数据是 5 分制，而 TMDb 是 10 分制，所以使用此脚本请提供 5 分制的数据，以免评分错误或异常。控制台显示的评价是星级不是分数。
- 若脚本在运行过程中由于网络不稳定等因素造成了运行中断，已经处理过的数据不会受到影响，重新运行脚本就会继续处理剩余数据。
- 如果您有大量的评分数据，脚本运行时间可能会较长，请耐心等待。
- 部分地区可能会由于网络原因造成 TMDb API 调用失败，无法运行脚本，请确保您的网络环境可以正常调用 TMDb API。

## 已知问题
- 脚本使用影片标题和年份进行匹配，如果文本文件中的标题或年份与 TMDb 数据库中的数据不匹配，可能会导致匹配失败或匹配错误。
- 若提供的数据不包含年份信息，可能会导致匹配错误。
- 对于只有一季的电视节目，脚本可能无法分辨它是电视节目还是电影，会根据标题和年份选择匹配度高或热门的项目进行匹配，有可能造成匹配错误。
- 若数据中存在同一个电视节目多季的数据，脚本会使用最小的年份进行匹配，若数据中包含年份信息但不包含第一季的数据会导致匹配失败；若包含第一季的数据，脚本会使用电视节目标题和第一季的年份进行匹配，并使用各季评分的平均值进行评分，评分成功后会删除文件内该电视节目所有季的数据。
<br>

# tmdb-rating-importer
tmdb-rating-importer is a Python script that can import rating data into a TMDb account by reading rating data from a text file and using the TMDb API to upload ratings to the [TMDb](https://www.themoviedb.org/) website.

## Demo
Suppose you have a text file named `ratings.txt` that contains rating data for some movies/TV shows.

The content of `ratings.txt` is as follows:
```
The Shawshank Redemption (1994): 5
Léon: The Professional (1994): 4
Forrest Gump (1994): 5
Farewell My Concubine (1993): 5
Life is Beautiful (1997): 4
```
You want to import this rating data into your TMDb account.

After running the tmdb-rating-importer.py script, the script will automatically read the rating data from the text file and use the TMDb API to upload ratings to the TMDb website, using your account to rate these movies as the corresponding number of stars.

## Requirements
- Installed Python 3.0 or higher.
- Installed necessary third-party libraries: requests and BeautifulSoup.
- Have an available TMDb account.
- Have an available TMDb API. (TMDb API can be applied for free in TMDb account settings)

## Usage
1. Clone or download the repository to a directory on your computer.
2. Set your TMDb API key, username, and password in the script by changing the values of the `api_key`, `username`, and `password` variables to your TMDb API key, username, and password.
3. Organize the rating data in the format provided in the demo, save it as a `ratings.txt` file, and place it in the same directory as the script.
4. Modify the path in `start.command (Mac)` or `start.bat (Win)` to point to the directory where you store the `tmdb-rating-importer.py` script.
5. Double-click to run the `start.command` or `start.bat` script to execute the `tmdb-rating-importer.py` script.
6. The script will start reading rating data from the text file and use the TMDb API to upload ratings to the TMDb website.
7. During script execution, you can see each movie/TV show’s name, rating, and upload status in the console.
8. After script execution is complete, you can view all movie/TV show rating data on the TMDb website.

## Notes
- Due to rate limits on the TMDb API, it is recommended not to perform other TMDb API-related operations during the script execution to avoid rate limit triggers.
- Rating data needs to be organized in the format provided above.
- After successfully rating a movie/TV show, the script will remove the corresponding data from the text file. After the script finishes running, only the data for which the rating failed will remain in the file. Before running the script, please back up the original data file to prevent data loss.
- The original intention of this script was to import Douban rating data into TMDb. Since Douban uses a 5-star rating system, while TMDb uses a 10-point rating system, please provide data in a 5-star format to avoid rating errors or anomalies. The displayed ratings in the console are in star format, not points.
- If the script is interrupted during execution due to unstable network conditions or other factors, the already processed data will not be affected. You can resume processing the remaining data by running the script again.
- If you have a large amount of rating data, script execution time may be long, please be patient.
- Some regions may experience TMDb API call failures due to network reasons. Ensure that your network environment can make TMDb API calls.

## Known Issues
- The script uses movie/TV show titles and release years for matching. If the titles or years in the text file do not match the data in the TMDb database, it may cause matching failures or errors.
- If provided data does not contain year information, it may cause matching errors.
- For TV shows with only one season, the script may not be able to distinguish whether it's a TV show or a movie. It will try to match based on the title and year, and choose the one with higher matching score or popularity, which may lead to matching errors.
- If the data includes ratings for multiple seasons of the same TV show, the script will use the lowest year for matching. If the data does not include the ratings for the first season, it will cause matching failure. If the data includes ratings for the first season, the script will use the title and year of the first season for matching and use the average ratings of all seasons for rating. After a successful rating, all data related to that TV show will be deleted from the file.
