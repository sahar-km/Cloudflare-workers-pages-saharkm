# Preferred subscription generator WorkerVless2sub

### This is a VLESS node subscription content generator built through Cloudflare Workers that automatically generates preferred lines.[\[Implementation principle\]](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=70s)

Telegram communication group:[@CMLiussss](https://t.me/CMLiussss)

# Pages deployment method[Video tutorial](https://www.youtube.com/watch?v=p-KhFJAC4WQ&t=509s)

### 1. Deploy Cloudflare Pages:

-   Fork this project on Github and click Star!!!
-   Select in the Cloudflare Pages console`连接到 Git`After that, select`WorkerVless2sub`Click after the item`开始设置`。

### 2. Bind a custom domain to Pages:

-   In the Pages console`自定义域`tab, click below`设置自定义域`。
-   Fill in your custom secondary domain name, be careful not to use your root domain name, for example:
    The domain name you are assigned is`fuck.cloudns.biz`, then add a custom field to fill in`sub.fuck.cloudns.biz`That’s it;
-   According to Cloudflare's requirements, your domain name DNS service provider will be returned and the custom domain will be added.`sub`CNAME record of`WorkerVless2sub.pages.dev`After that, click`激活域`That’s it.

### 3. Modify the quick subscription entrance and add built-in Vless node information:

For example, the domain name of your pages project is:`sub.fuck.cloudns.biz`；

-   Add to`TOKEN`Variable, quick subscription access entrance, default value is:`auto`, get the default node subscription address of the subscriber, that is,`/auto`,For example`https://sub.fuck.cloudns.biz/auto`
-   Add to`HOST`variables such as`edgetunnel-2z2.pages.dev`；
-   Add to`UUID`variables such as`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   Add to`PATH`variables such as`/?ed=2048`；

### 4. Add your own preferred route:

-   Add variables`ADD`/`ADDNOTLS`Local static preferred line, if there is no port number, the default port for TLS is 443 / the default port for noTLS is 80, and the # number is followed by a remark alias, for example:
        icook.tw:2053#优选域名
        cloudflare.cfgo.cc#优选官方线路

-   Add variables`ADDAPI`/`ADDNOTLSAPI`for**Preferred IP address txt file**URL. For example:
    ```url
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesipv6api.txt
    ```

<details>
<summary><code><strong>「 我不是小白！我有IP库！我知道IPtest是什么！我也有csv测速文件！ 」</strong></code></summary>

-   Add variables`ADDCSV`for**iptest speed test result csv file address**URL. For example:
    ```js
    https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv
    ```
-   Add variables`DLS`,means`ADDCSV`IPs that meet the minimum speed requirements and do not meet the modified value will not be added to the preferred subscription content. Note: The unit is not considered, only the numerical value is considered. Please refer to your speed test results. For example:

    ```js
    8
    ```

    </details>

# Workers deployment method[Video tutorial](https://youtu.be/AtCF7eq0hcE)

### 1. Deploy Cloudflare Worker:

-   Create a new Worker in the Cloudflare Worker console.
-   Will[worker.js](https://github.com/cmliu/WorkerVless2sub/blob/main/_worker.js)Paste the contents into the Worker editor.

### 2. Modify the quick subscription entrance and add built-in Vless node information:

For example, the domain name of your workers project is:`sub.cmliussss.workers.dev`；

-   Add to`TOKEN`Variable, quick subscription access entrance, default value is:`auto`, get the default node subscription address of the subscriber, that is,`/auto`,For example`https://sub.cmliussss.workers.dev/auto`
-   Add to`HOST`variables such as`edgetunnel-2z2.pages.dev`；
-   Add to`UUID`variables such as`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   Add to`PATH`variables such as`/?ed=2048`；

### 3. Add your own preferred route:

**3.1 Example of modifying addresses parameter**

-   Revise`addresses`Parameters add a local static preferred line. If there is no port number, the default is 443. Generating non-TLS subscriptions is not supported. The # number is followed by a comment alias, for example:
    ```js
    let addresses = [
    	'icook.tw:2053#优选域名',
    	'cloudflare.cfgo.cc#优选官方线路',
    	'185.221.160.203:443#电信优选IP',
    ];
    ```
    This method only recommends adding preferred domain names. Preferred domain names that change frequently are recommended through`addressesapi`to fulfill.

**3.2 Example of modifying addressesapi parameters**

-   Revise`addressesapi`Parameters, set in the script`addressesapi`The variable is**Preferred IP address txt file**URL. For example:
    ```js
    let addressesapi = [
    	'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt',
    	'https://addressesapi.090227.xyz/CloudFlareYes',
    ];
    ```
    Can be referenced[addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt)Content format is built by yourself.

<details>
<summary><code><strong>「 我不是小白！我有IP库！我知道IPtest是什么！我也有csv测速文件！ 」</strong></code></summary>

**3.3 Example of modifying addressescsv parameters**

-   Revise`addressescsv`Parameters, set in the script`addressescsv`The variable is**iptest speed test result csv file address**URL. For example:

    ```js
    let DLS = 4;//速度下限
    let addressescsv = [
    	'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
    		'https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv',
    ];
    ```

    `DLS`IPs that do not meet the minimum speed requirements will not be added to the preferred subscription content. Note: The unit is not considered, only the numerical value is considered. Please refer to your speed test results.

    </details>

# Subscription generator usage[Video tutorial](https://youtu.be/OjqCKeEY7DQ)

For example, the domain name of your workers project is:`sub.cmliussss.workers.dev`；

### 1. Quick subscription

-   Add to`TOKEN`Variable, quick subscription access entrance, default value is:`auto`, get the default node subscription address of the subscriber, that is,`/auto`,For example:
    ```url
    https://sub.cmliussss.workers.dev/auto
    ```

### 2. Custom subscription

-   **Custom subscription format**`https://[你的Workers域名]/sub?host=[你的Vless域名]&uuid=[你的UUID]&path=[你的ws路径]`
-   **host**: Your VLESS disguised domain name, e.g.`edgetunnel-2z2.pages.dev`；
-   **uuid**: your VLESS client UUID, e.g.`30e9c5c8-ed28-4cd9-b008-dc67277f8b02`；
-   **path**(optional): WS path of your VLESS (leave blank if none), e.g.`/?ed=2048`。
-   The custom subscription address is as follows:
    ```url
    https://sub.cmliussss.workers.dev/sub?host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```
-   Note that the path must contain "/sub".

### 3. Specify clash and singbox configuration files

-   Add to`format=clash`Key value, get clash subscription configuration, for example:
    ```url
    https://sub.cmliussss.workers.dev/auto?format=clash
    https://sub.cmliussss.workers.dev/sub?format=clash&host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```
-   Add to`format=singbox`Key value, get singbox subscription configuration, for example:
    ```url
    https://sub.cmliussss.workers.dev/auto?format=singbox
    https://sub.cmliussss.workers.dev/sub?format=singbox&host=edgetunnel-2z2.pages.dev&uuid=30e9c5c8-ed28-4cd9-b008-dc67277f8b02&path=/?ed=2048
    ```

### Variable description

| variable name | Example                                                                                                                                                        | Remark                                                                                                                                       |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| TOKEN         | auto                                                                                                                                                           | Quickly subscribe to the subscription path address of the built-in node /auto (supports multiple elements, used between elements`,`interval) |
| HOST          | edgetunnel-2z2.pages.dev                                                                                                                                       | Quickly subscribe to the fake domain name of the built-in node                                                                               |
| UUID          | Bahaasaa-4f0-4496-90bas-1saaaaaa4904                                                                                                                           | Quickly subscribe to the UUID of a built-in node                                                                                             |
| PATH          | /?ed=2560                                                                                                                                                      | 快速订阅内置节点的路径信息                                                                                                                                |
| ADD           | icook.tw:2053#Official preferred domain name                                                                                                                   | correspond`addresses`Field (supports multiple elements, used between elements`,`interval)                                                    |
| ADDAPI        | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressesapi.txt)                                        | correspond`addressesapi`Field (supports multiple elements, used between elements`,`interval)                                                 |
| ADDNOTLS      | icook.hk:8080# Official preferred domain name                                                                                                                  | 对应`addressesnotls`Field (supports multiple elements, used between elements`,`interval)                                                       |
| ADDNOTLSAPI   | [https://raw.github.../addressesapi.txt](https://raw.githubusercontent.com/cmliu/CFcdnVmess2sub/main/addressesapi.txt)                                         | correspond`addressesnotlsapi`Field (supports multiple elements, used between elements`,`interval)                                            |
| ADDCSV        | [https://raw.github.../addressescsv.csv](https://raw.githubusercontent.com/cmliu/WorkerVless2sub/main/addressescsv.csv)                                        | correspond`addressescsv`Field (supports multiple elements, used between elements`,`interval)                                                 |
| DLS           | 8                                                                                                                                                              | `addressescsv`Speed ​​measurement results meet the lower speed limit                                                                         |
| NOTLS         | false                                                                                                                                                          | Change to`true`, no domain name judgment will be performed and noTLS node will always be returned.                                           |
| TGTOKEN       | 6894123456:XXXXXXXXXX0qExVsBPUhHDAbXXXXXqWXgBA                                                                                                                 | Robot token for sending TG notifications                                                                                                     |
| YOU DO        | 6946912345                                                                                                                                                     | Account digital ID to receive TG notifications                                                                                               |
| subapi        | api.v1.mk                                                                                                                                                      | clash, singbox, etc. subscription conversion backend                                                                                         |
| SUBCONFIG     | [https://raw.github.../ACL4SSR_Online_Full_MultiMode.ini](https://raw.githubusercontent.com/cmliu/ACL4SSR/main/Clash/config/ACL4SSR_Online_Full_MultiMode.ini) | clash, singbox, etc. Subscription conversion profiles                                                                                        |
| SUBNAME       | WorkerVless2sub                                                                                                                                                | Subscription generator name                                                                                                                  |
| PS            | 【Please do not measure speed】                                                                                                                                  | Node name remark message                                                                                                                     |

## Star stars rise

[![Stargazers over time](https://starchart.cc/cmliu/WorkerVless2sub.svg?variant=adaptive)](https://starchart.cc/cmliu/WorkerVless2sub)

# grateful

My own imagination,[Sakura-bow](https://github.com/SAKURA-YUMI)，[EzSync](https://github.com/EzSync)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR/tree/master/Clash/config)、[fat sheep](https://github.com/youshandefeiyang/sub-web-modify)
