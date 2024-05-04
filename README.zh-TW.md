# Cloudflare Worker 2 Vless 和 Sub

這是一個基於 Cloudflare Worker 平台的腳本，在原版的基礎上修改了顯示 VLESS 設定資訊轉換為訂閱內容。使用該腳本，你可以方便地將 VLESS 設定資訊使用線上設定轉換到 Clash 或 Singbox 等工具。

-   基礎部署影片教學：<https://www.youtube.com/watch?v=LeT4jQUh8ok>
-   快速部署影片教學：<https://www.youtube.com/watch?v=59THrmJhmAw>**_最佳推薦!!!_**
-   進階使用視角教學：<https://www.youtube.com/watch?v=s91zjpw3-P8>

Telegram交流群：[@CMLiussss](https://t.me/CMLiussss)

# 免責聲明

本免責聲明適用於 GitHub 上的 “edgetunnel” 專案（以下簡稱“該專案”），專案連結為：<https://github.com/cmliu/edgetunnel>

### 用途

該項目被設計和開發僅供學習、研究和安全測試目的。它旨在為安全研究者、學術界人士和技術愛好者提供一個了解和實踐網路通訊技術的工具。

### 合法性

用戶在下載和使用該項目時，必須遵守當地法律和規定。使用者有責任確保他們的行為符合其所在地區的法律、規章以及其他適用的規定。

### 免責

1.  作為該計畫的作者，我（以下簡稱「作者」）強調該計畫應僅用於合法、道德和教育目的。
2.  作者不鼓勵、不支持也不促進任何形式的非法使用該項目。如果發現該項目被用於非法或不道德的活動，作者將強烈譴責這種行為。
3.  作者對任何人或團體使用該項目進行的任何非法活動不承擔責任。使用者使用該項目時產生的任何後果由使用者本人承擔。
4.  作者不對使用該項目可能引起的任何直接或間接損害負責。
5.  透過使用該項目，使用者表示瞭解並同意本免責聲明的所有條款。如果使用者不同意這些條款，應立即停止使用該項目。

作者保留隨時更新本免責聲明的權利，且不另行通知。最新的免責聲明版本將會在該專案的 GitHub 頁面上發布。

## 風險提示

-   透過提交虛假的節點配置給訂閱服務，避免節點配置資訊外洩。
-   另外，您也可以選擇自行部署[WorkerVless2sub 訂閱生成服務](https://github.com/cmliu/WorkerVless2sub)，這樣既可以利用訂閱產生器的便利性。

## Workers 部署方法[影片教學](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  部署 Cloudflare Worker：
    -   在 Cloudflare Worker 控制台中建立一個新的 Worker。
    -   將[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)的內容貼到 Worker 編輯器中。
    -   將第 7 行`userID`修改成你自己的**通用唯一識別符**。

2.  存取訂閱內容：
    -   訪問`https://[YOUR-WORKERS-URL]/[UUID]`即可取得訂閱內容。
    -   例如`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`就是你的通用自適應訂閱地址。
    -   例如`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64訂閱格式，適用PassWall,SSR+等。
    -   例如`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash訂閱格式，適用OpenClash等。
    -   例如`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox訂閱格式，適用singbox等。

3.  給 workers綁定 自訂網域：
    -   在 workers控制台的`触发器`選項卡，下方點選`添加自定义域`。
    -   填入你已轉入 CloudFlare 域名解析服務的次級域名，例如:`vless.google.com`後 點擊`添加自定义域`，等待證書生效即可。
    -   **如果你是小白，現在可以直接起飛，不用再往下看了！ ！ ！**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  使用自己的`优选域名`/`优选IP`的訂閱內容：
    -   如果你想使用自己的優選網域或是自己的優選IP，可以參考[WorkerVless2sub GitHub 倉庫](https://github.com/cmliu/WorkerVless2sub)中的部署說明自行搭建。
    -   打開[工人.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)文件，在第 12 行找到`sub`變量，將其修改為你部署的訂閱生成器位址。例如`let sub = 'sub.cmliussss.workers.dev';`，注意不要帶https等協議資訊和符號。
    -   注意，如果您使用了自己的訂閱位址，要求訂閱產生器的`sub`域名 和`[YOUR-WORKER-URL]`的域名 不同屬一個頂級域名，否則會出現異常。您可以在`sub`變數賦值為 workers.dev 分配到的網域名稱。

</details>

## Pages 上傳 部署方法**最佳推薦!!!**[影片教學](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  部署 Cloudflare Pages：
    -   下載[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)文件，並點上 Star !!!
    -   在 Cloudflare Pages 控制台中選擇`上传资产`後，為你的專案取名後點擊`创建项目`，然後上傳你下載好的[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)文件後點擊`部署站点`。
    -   部署完成後點選`继续处理站点`後，選擇`设置`>`环境变量`>**製作**為生產環境定義變數 >`添加变量`。
        變數名稱填寫**通用唯一識別符**，值則為你的UUID，後點選`保存`即可。
    -   返回`部署`選項卡，在右下角點擊`创建新部署`後，重新上傳[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)文件後點擊`保存并部署`即可。

2.  存取訂閱內容：
    -   訪問`https://[YOUR-PAGES-URL]/[YOUR-UUID]`即可取得訂閱內容。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`就是你的通用自適應訂閱地址。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64訂閱格式，適用PassWall,SSR+等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash訂閱格式，適用OpenClash等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox訂閱格式，適用singbox等。

<details>
<summary><code><strong>「 我自己有域名！我要绑定自己的域名！我已经熟练的掌握域名解析！ 」</strong></code></summary>
   
3. 给 Pages绑定 CNAME自定义域：[视频教程](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
   - 在 Pages控制台的 `自定义域`选项卡，下方点击 `设置自定义域`。
   - 填入你的自定义次级域名，注意不要使用你的根域名，例如：
     您分配到的域名是 `fuck.cloudns.biz`，则添加自定义域填入 `lizi.fuck.cloudns.biz`即可；
   - 按照 Cloudflare 的要求将返回你的域名DNS服务商，添加 该自定义域 `lizi`的 CNAME记录 `edgetunnel.pages.dev` 后，点击 `激活域`即可。
   - **如果你是小白，那么你的 pages 绑定`自定义域`之后即可直接起飞，不用再往下看了！！！**
   - 
</details>
<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>
   
4. 使用自己的`优选域名`/`优选IP`的订阅内容：
   - 如果你想使用自己的优选域名或者是自己的优选IP，可以参考 [WorkerVless2sub GitHub 仓库](https://github.com/cmliu/WorkerVless2sub) 中的部署说明自行搭建。
   - 在 Pages控制台的 `设置`选项卡，选择 `环境变量`> `制作`> `编辑变量`> `添加变量`；
   - 变量名设置为`SUB`，对应的值为你部署的订阅生成器地址。例如 `sub.cmliussss.workers.dev`，后点击 **保存**。
   - 之后在 Pages控制台的 `部署`选项卡，选择 `所有部署`> `最新部署最右的 ...`> `重试部署`，即可。
   - 注意，如果您使用了自己的订阅地址，要求订阅生成器的 `SUB`域名 和 `[YOUR-PAGES-URL]`的域名 不同属一个顶级域名，否则会出现异常。您可以在 `SUB` 变量赋值为 Pages.dev 分配到的域名。

</details>

## Pages GitHub 部署方法[影片教學](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  部署 Cloudflare Pages：
    -   在 Github 上先 Fork 本項目，並點上 Star !!!
    -   在 Cloudflare Pages 控制台中選擇`连接到 Git`後，選取`edgetunnel`項目後點擊`开始设置`。
    -   在`设置构建和部署`頁面下方，選擇`环境变量（高级）`後並`添加变量`變數名稱填寫**通用唯一識別符**，值則為你的UUID，後點選`保存并部署`即可。

2.  存取訂閱內容：
    -   訪問`https://[YOUR-PAGES-URL]/[YOUR-UUID]`即可取得訂閱內容。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`就是你的通用自適應訂閱地址。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64訂閱格式，適用PassWall,SSR+等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash訂閱格式，適用OpenClash等。
    -   例如`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox訂閱格式，適用singbox等。

3.  給 Pages綁定 CNAME自訂域：[影片教學](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   在 Pages控制台的`自定义域`選項卡，下方點選`设置自定义域`。
    -   填入你的自訂次級域名，注意不要使用你的根域名，例如：
        您指派的網域名稱是`fuck.cloudns.biz`，則新增自訂網域填入`lizi.fuck.cloudns.biz`即可；
    -   依照 Cloudflare 的要求將會回到你的網域DNS服務商，新增 這個自訂網域`lizi`的 CNAME記錄`edgetunnel.pages.dev`後，點擊`激活域`即可。
    -   **如果你是小白，那麼你的 pages 綁定`自定义域`之後即可直接起飛，不用再往下看了！ ！ ！**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  使用自己的`优选域名`/`优选IP`的訂閱內容：
    -   如果你想使用自己的優選網域或是自己的優選IP，可以參考[WorkerVless2sub GitHub 倉庫](https://github.com/cmliu/WorkerVless2sub)中的部署說明自行搭建。
    -   在 Pages控制台的`设置`選項卡，選擇`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   變數名設定為`SUB`，對應的值為你部署的訂閱產生器位址。例如`sub.cmliussss.workers.dev`，後點選**儲存**。
    -   之後在 Pages控制台的`部署`選項卡，選擇`所有部署`>`最新部署最右的 ...`>`重试部署`，即可。
    -   注意，如果您使用了自己的訂閱位址，要求訂閱產生器的`SUB`域名 和`[YOUR-PAGES-URL]`的域名 不同屬一個頂級域名，否則會出現異常。您可以在`SUB`變數賦值為 Pages.dev 指派的網域名稱。

</details>

### 變數說明

| 變數名      | 範例                                                                                                                                                             | 備註                                                             | 油田                                                        |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------------------- |
| 通用唯一識別符  | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -NoExit -命令“[指導]&#x3A;:NewGuid()"                   | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| 代理伺服器的IP | proxyip.fxxk.dedyn.io                                                                                                                                          | 備選作為存取CloudFlareCDN站點的代理節點(支援多ProxyIP, ProxyIP之間使用`,`或 換行 作間隔) | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| 襪子5      | 用戶：[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                        | 優先作為存取CloudFlareCDN站點的SOCKS5代理                                 | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| 子系統      | sub.cmliussss.workers.dev                                                                                                                                      | 內建域名、IP節點資訊的訂閱產生器位址                                            | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| 子API     | api.v1.mk                                                                                                                                                      | clash、singbox等 訂閱轉換後端                                          | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| 子配置      | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash、singbox等 訂閱轉換設定檔                                         | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| 代理IP     | 錯誤的                                                                                                                                                            | 設為 true 即可強制取得訂閱器分配的ProxyIP(需訂閱器支援)                            | [影片](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02       | <https://t.me/CMLiussss>                                                                                                                                       | 首頁302跳轉(支援多url, url之間使用`,`或 換行 作間隔, 小白別用)                      |                                                           |
| 網址       | <https://t.me/CMLiussss>                                                                                                                                       | 首頁偽裝(支援多url, url之間使用`,`或 換行 作間隔, 亂設容易觸發反詐)                     |                                                           |

## Star 星星走起

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## 已適配自適應訂閱內容

-   [v2rayN](https://github.com/2dust/v2rayN)
-   衝突.元（[衝突邊緣修訂版](https://github.com/clash-verge-rev/clash-verge-rev)，[衝突尼安帕蘇](https://github.com/keiko233/clash-nyanpasu)，~[衝突邊緣](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX元）
-   唱箱（SFI）

# 感謝

[紫菀](https://github.com/zizifn/edgetunnel)、[對其進行消毒](https://github.com/3Kmfi6HP/EDtunnel)、[史丹利寶貝](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[謝格斯1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
