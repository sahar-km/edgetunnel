# Cloudflare Worker 2 Vless & Sub

This is a script based on the Cloudflare Worker platform. Based on the original version, it is modified to display VLESS configuration information and convert it into subscription content. Using this script, you can easily convert VLESS configuration information into tools such as Clash or Singbox using online configuration.

-   Basic deployment video tutorial:<https://www.youtube.com/watch?v=LeT4jQUh8ok>
-   Quick deployment video tutorial:<https://www.youtube.com/watch?v=59THrmJhmAw>**_Best recommendation!!!_**
-   Advanced tutorial on using perspective:<https://www.youtube.com/watch?v=s91zjpw3-P8>

Telegram communication group:[@CMLiussss](https://t.me/CMLiussss)

# Disclaimer

This disclaimer applies to the “edgetunnel” project on GitHub (hereinafter referred to as the “project”), the project link is:<https://github.com/cmliu/edgetunnel>

### use

This project is designed and developed for learning, research and safety testing purposes only. It aims to provide security researchers, academics, and technology enthusiasts with a tool to understand and practice network communication technologies.

### legality

Users must comply with local laws and regulations when downloading and using this project. Users are responsible for ensuring that their actions comply with the laws, regulations and other applicable requirements of their region.

### Disclaimer

1.  As the author of this project, I (hereinafter referred to as the "Author") emphasize that this project should be used only for legal, ethical and educational purposes.
2.  The author does not encourage, support or promote any form of illegal use of this project. If this project is found to be used for illegal or unethical activities, the author will strongly condemn such behavior.
3.  The author is not responsible for any illegal activities carried out by any person or group using this project. Any consequences arising from the use of this project shall be borne by the user himself.
4.  The author is not responsible for any direct or indirect damages that may arise from the use of this project.
5.  By using this project, users indicate that they understand and agree to all the terms of this disclaimer. If the user does not agree to these terms, he should immediately stop using the project.

The author reserves the right to update this disclaimer at any time without prior notice. The latest version of the disclaimer will be published on the project's GitHub page.

## risk warning

-   Avoid leaking node configuration information by submitting false node configurations to the subscription service.
-   Alternatively, you can choose to deploy it yourself[WorkerVless2sub Subscription Generation Service](https://github.com/cmliu/WorkerVless2sub), so you can take advantage of the subscription generator.

## Workers deployment method[Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=83s)

1.  Deploy Cloudflare Worker:
    -   Create a new Worker in the Cloudflare Worker console.
    -   Will[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)Paste the contents into the Worker editor.
    -   Change line 7`userID`Modify it to your own**UUID**。

2.  Access subscription content:
    -   access`https://[YOUR-WORKERS-URL]/[UUID]`Subscription content is available.
    -   For example`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`This is your universal adaptive subscription address.
    -   For example`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 subscription format, suitable for PassWall, SSR+, etc.
    -   For example`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash subscription format, suitable for OpenClash, etc.
    -   For example`https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox subscription format, suitable for singbox, etc.

3.  Bind a custom domain to workers:
    -   In the workers console`触发器`tab, click below`添加自定义域`。
    -   Fill in the secondary domain name that you have transferred to the CloudFlare domain name resolution service, for example:`vless.google.com`After click`添加自定义域`, just wait for the certificate to take effect.
    -   **If you are a novice, you can take off directly now without looking further! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  use your own`优选域名`/`优选IP`Subscriptions for:
    -   If you want to use your own preferred domain name or your own preferred IP, you can refer to[WorkerVless2sub GitHub repository](https://github.com/cmliu/WorkerVless2sub)Build it yourself according to the deployment instructions in .
    -   Open[worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js)file, found on line 12`sub`variable and modify it to the address of your deployed subscription generator. For example`let sub = 'sub.cmliussss.workers.dev';`, be careful not to include protocol information and symbols such as https.
    -   Note that if you use your own subscription address, the subscription generator's`sub`domain name and`[YOUR-WORKER-URL]`The domain name does not belong to the same top-level domain name, otherwise an exception will occur. You can`sub`The variable is assigned the domain name assigned to workers.dev.

</details>

## Pages upload deployment method**Best recommendation!!!**[Video tutorial](https://www.youtube.com/watch?v=59THrmJhmAw)

1.  Deploy Cloudflare Pages:
    -   download[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)file and click Star!!!
    -   Select in the Cloudflare Pages console`上传资产`Finally, give your project a name and click`创建项目`, and then upload the downloaded[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Click after the file`部署站点`。
    -   After deployment is complete, click`继续处理站点`After that, select`设置`>`环境变量`>**make**Define variables for production >`添加变量`.
        Fill in the variable name**UUID**, the value is your UUID, then click`保存`That’s it.
    -   return`部署`tab, click in the lower right corner`创建新部署`Then re-upload[worker.zip](https://raw.githubusercontent.com/cmliu/edgetunnel/main/worker.zip)Click after the file`保存并部署`That’s it.

2.  Access subscription content:
    -   access`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Subscription content is available.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`This is your universal adaptive subscription address.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 subscription format, suitable for PassWall, SSR+, etc.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash subscription format, suitable for OpenClash, etc.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox subscription format, suitable for singbox, etc.

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

## Pages GitHub deployment method[Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=560s)

1.  Deploy Cloudflare Pages:
    -   Fork this project on Github and click Star!!!
    -   Select in the Cloudflare Pages console`连接到 Git`After that, select`edgetunnel`Click after the item`开始设置`。
    -   exist`设置构建和部署`At the bottom of the page, select`环境变量（高级）`merge later`添加变量`Fill in the variable name**UUID**, the value is your UUID, then click`保存并部署`That’s it.

2.  Access subscription content:
    -   access`https://[YOUR-PAGES-URL]/[YOUR-UUID]`Subscription content is available.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`This is your universal adaptive subscription address.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub`Base64 subscription format, suitable for PassWall, SSR+, etc.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash`Clash subscription format, suitable for OpenClash, etc.
    -   For example`https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb`singbox subscription format, suitable for singbox, etc.

3.  Bind CNAME custom domain to Pages:[Video tutorial](https://www.youtube.com/watch?v=LeT4jQUh8ok&t=851s)
    -   In the Pages console`自定义域`tab, click below`设置自定义域`。
    -   Fill in your custom secondary domain name, be careful not to use your root domain name, for example:
        The domain name you are assigned is`fuck.cloudns.biz`, then add a custom field to fill in`lizi.fuck.cloudns.biz`That’s it;
    -   According to Cloudflare's requirements, your domain name DNS service provider will be returned and the custom domain will be added.`lizi`CNAME record of`edgetunnel.pages.dev`After that, click`激活域`That’s it.
    -   **If you are a novice, then your pages binding`自定义域`You can take off directly after that, no need to look further! ! !**

<details>
<summary><code><strong>「 我不是小白！我真的真的不是小白！我要玩花活！我要开启高端玩法！ 」</strong></code></summary>

4.  use your own`优选域名`/`优选IP`Subscriptions for:
    -   If you want to use your own preferred domain name or your own preferred IP, you can refer to[WorkerVless2sub GitHub repository](https://github.com/cmliu/WorkerVless2sub)Build it yourself according to the deployment instructions in .
    -   In the Pages console`设置`tab, select`环境变量`>`制作`>`编辑变量`>`添加变量`；
    -   The variable name is set to`SUB`, the corresponding value is the address of the subscription generator you deployed. For example`sub.cmliussss.workers.dev`, then click**keep**。
    -   Then in the Pages console`部署`tab, select`所有部署`>`最新部署最右的 ...`>`重试部署`, that’s it.
    -   Note that if you use your own subscription address, the subscription generator's`SUB`domain name and`[YOUR-PAGES-URL]`The domain name does not belong to the same top-level domain name, otherwise an exception will occur. You can`SUB`The variable is assigned the domain name assigned to Pages.dev.

</details>

### Variable description

| variable name | Example                                                                                                                                                        | Remark                                                                                                                                      | YT                                                           |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| UUID          | 90SD4AH-141A-43SS-991B-08263SVISES10                                                                                                                           | Powershell -NoExit -Command "[guid]&#x3A;:NewGuid()"                                                                                        | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=72s)   |
| PROXYIP       | proxyip.fxxk.dedyn.io                                                                                                                                          | Alternative as a proxy node for accessing CloudFlareCDN site (supports multiple ProxyIPs, used between ProxyIPs`,`or line feed as interval) | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=166s)  |
| SOCKS5        | user:[password@127.0.0.1](mailto:password@127.0.0.1):1080                                                                                                      | Preferred as a SOCKS5 proxy for accessing CloudFlareCDN sites                                                                               | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=826s)  |
| SUB           | sub.cmliussss.workers.dev                                                                                                                                      | Subscription generator address with built-in domain name and IP node information                                                            | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1193s) |
| subapi        | api.v1.mk                                                                                                                                                      | clash, singbox, etc. subscription conversion backend                                                                                        | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1446s) |
| SUBCONFIG     | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash, singbox, etc. Subscription conversion profile                                                                                        | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1605s) |
| RPROXYIP      | false                                                                                                                                                          | Set to true to force the acquisition of the ProxyIP assigned by the subscriber (requires subscriber support)                                | [Video](https://www.youtube.com/watch?v=s91zjpw3-P8&t=1816s) |
| 02            | <https://t.me/CMLiussss>                                                                                                                                       | Home page 302 jump (supports multiple URLs, used between URLs)`,`Or line feed as a spacer, don’t use it if you are new to it)               |                                                              |
| URL           | <https://t.me/CMLiussss>                                                                                                                                       | Homepage disguise (supports multiple URLs, used between URLs)`,`Or line breaks as intervals, random settings can easily trigger anti-fraud) |                                                              |

## Star stars rise

[![Stargazers over time](https://starchart.cc/cmliu/edgetunnel.svg?variant=adaptive)](https://starchart.cc/cmliu/edgetunnel)

## Adapted adaptive subscription content

-   [v2rayN](https://github.com/2dust/v2rayN)
-   clash.meta（[clash-verge-rev](https://github.com/clash-verge-rev/clash-verge-rev)，[Clash Nyanpasu](https://github.com/keiko233/clash-nyanpasu)，~[clash-verge](https://github.com/zzzgydi/clash-verge/tree/main)~，ClashX Meta）
-   sing-box（SFI）

# grateful

[zizifn](https://github.com/zizifn/edgetunnel)、[Sterilize it](https://github.com/3Kmfi6HP/EDtunnel)、[Stanley-baby](https://github.com/Stanley-baby)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[Shegs1999](https://github.com/SHIJS1999/cloudflare-worker-vless-ip)
