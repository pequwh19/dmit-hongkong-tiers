# 香港伺服器租用：免備案也有低延遲，搞懂 Tier 1／Eyeball／Premium 三條線路，從月付 $6.9 挑到對的方案

搜「香港伺服器租用」的人，卡住的地方往往不是規格表，而是線路。記憶體 2GB 還是 4GB 誰都看得懂，但一看到 CN2 GIA、CMI、RETN、Tier 1 這幾個詞，多半就開始滑手機了。

這篇以 DMIT 的香港節點為例，把選購邏輯拆開來講：三條線路各自適合誰、超量之後會發生什麼事、目前的完整套餐與價格長什麼樣。看完你應該能直接定位到自己要哪一台，而不是在購物車頁面來回比對半小時。

## 先確認一件事：你的訪客在哪裡

香港機房的賣點很單純——離中國大陸近、離東南亞近、不用備案。物理距離這件事沒有替代方案，洛杉磯節點再怎麼優化，也補不回那一萬公里。所以香港節點的實測延遲通常落在 40–60ms 這個區間，而不是 130ms 起跳。

但「香港伺服器」不等於「對大陸快」。同樣是香港機房，走國際線路跟走 CN2 GIA，電信用戶的體驗可以差到讓人以為買錯國家。所以下單前先回答三個問題：

1. **主要訪客在中國大陸嗎？** 是的話，國際線路直接排除。
2. **月流量大概多少？** 個人部落格和影片站的量級差兩個數量級。
3. **超量時你要限速還是要停機？** 這個決定比你想像的重要，下面會單獨講。

## Tier 1／Eyeball／Premium，差別其實只有一件事

DMIT 的香港節點跑三種路由設定，硬體平台差異不大，核心差別在「回程走哪條路」。

| 線路系列 | 定位 | 大陸訪問優化 | 超量處理 | 入門價 |
| --- | --- | --- | --- | --- |
| Tier 1（T1） | 國際互聯、亞歐之間的低延遲 | 無 | 降速繼續跑，不限流量 | $36.90/年 |
| Eyeball（EB） | 折衷方案，移動線路為主 | 中等（CMI 為主） | 超量暫停 | $29.90/月起 |
| Premium（Pro） | 旗艦，電信雙向 CN2 GIA | 高 | 超量暫停 | $39.90/月 |

Tier 1 接的是國際骨幹（包含 RETN），香港到歐洲的延遲明顯比一般線路低，對面向歐美或東南亞的業務很划算。代價是大陸訪問沒有專項優化，電信和聯通用戶可能會遇到比美國節點還高的延遲——這條線路買錯的人不少，不是因為方案不好，而是需求沒對上。

Premium 是反過來：電信去程與回程都走 CN2 GIA，聯通走 AS4837 加 AS10099，移動走 CMI 直連。三網都有安排，價格也是三條線裡最高的。

Eyeball 夾在中間，回程以 CMI 為主，移動用戶體感不錯，預算比 Premium 低一截。有一點要先講清楚：DMIT 官方把 Eyeball 標為 Beta 網路，路由仍在調整，官方本身也不建議把它放進穩定性要求高的生產環境。另外這條線的庫存常常是斷的，想買得碰運氣。

## 超量限速 vs 超量暫停：最容易踩的坑

把這句記下來：**Tier 1 流量用完不會斷線，Premium 和 Eyeball 會。**

Tier 1 的設計是達量後降速繼續跑。WEE 降到 50Mbps，TINY 和 STARTER 降到 100Mbps，MICRO 與 MEDIUM 是 200Mbps，LARGE 到 500Mbps，GIANT 保留 1Gbps，全部不限流量。對跑下載站、鏡像站或備份節點的人來說，這個設定等於買到一台「不限流量」的香港機器。

Premium 和 Eyeball 就是標準做法——流量到頂服務暫停，要嘛加購流量，要嘛等下個週期。挑方案時把這條算進去，很多「選哪台」的糾結會自己消失。

## DMIT 香港全套餐價格一覽

以下整理官網目前展示的香港方案。價格以美元計價，實際結帳金額與庫存請以訂購頁顯示為準。

### Tier 1（國際線路，超量降速不限流量）

| 方案 | CPU／記憶體 | SSD | 月流量／頻寬 | 超量後 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- | --- |
| HKG.T1.WEE | 1 核／1GB | 20GB | 1TB @4Gbps | 50Mbps | $36.90／年 | [ 看 WEE 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.TINY | 1 核／1GB | 20GB | 2TB @4Gbps | 100Mbps | $6.90／月 | [ 看 TINY 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.STARTER | 1 核／2GB | 40GB | 4TB @10Gbps | 100Mbps | $12.90／月 | [ 看 STARTER 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.MINI | 2 核／2GB | 60GB | 8TB @10Gbps | 100Mbps | $21.90／月 | [ 看 MINI 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.MICRO | 4 核／4GB | 80GB | 16TB @10Gbps | 200Mbps | $32.90／月 | [ 看 MICRO 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.MEDIUM | 4 核／8GB | 160GB | 32TB @10Gbps | 200Mbps | $49.90／月 | [ 看 MEDIUM 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.LARGE | 8 核／16GB | 320GB | 64TB @10Gbps | 500Mbps | $99.90／月 | [ 看 LARGE 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |
| HKG.T1.GIANT | 8 核／24GB | 640GB | 128TB @10Gbps | 1Gbps | $199.90／月 | [ 看 GIANT 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier1&aff=12046) |

每一台都是 1 個 IPv4 加 1 個 IPv6 /64，KVM 虛擬化，跑 AMD EPYC 平台。

### Premium（AS3 平台，AMD EPYC 7003，三網 CN2 GIA）

| 方案 | CPU／記憶體 | SSD | 月流量／頻寬 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- |
| HKG.AS3.Pro.TINY | 1 核／1GB | 20GB | 500GB @1Gbps | $39.90／月 | [ 以 $39.90 入手 Premium](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.STARTER | 1 核／2GB | 40GB | 1000GB @1Gbps | $79.90／月 | [ 看 STARTER 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MINI | 2 核／4GB | 60GB | 1500GB @1Gbps | $126.90／月 | [ 看 MINI 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MICRO | 4 核／4GB | 80GB | 2000GB @1Gbps | $179.90／月 | [ 看 MICRO 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |
| HKG.AS3.Pro.MEDIUM | 4 核／8GB | 160GB | 2500GB @1Gbps | $239.90／月 | [ 看 MEDIUM 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=premium&aff=12046) |

### Premium（AN5 平台，AMD EPYC 9005 + DDR5）

| 方案 | CPU／記憶體 | SSD | 月流量／頻寬 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- |
| HKG.AN5.Pro.MINI | 4 核／4GB | 80GB | 1500GB @1Gbps | $149.90／月 | [ 看 AN5 MINI 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| HKG.AN5.Pro.MICRO | 4 核／4GB | 160GB | 2000GB @1Gbps | $199.90／月 | [ 看 AN5 MICRO 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| HKG.AN5.Pro.MEDIUM | 6 核／8GB | 160GB | 2500GB @1Gbps | $279.90／月 | [ 看 AN5 MEDIUM 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| HKG.AN5.Pro.LARGE | 8 核／16GB | 320GB | 3000GB @1Gbps | $359.90／月 | [ 看 AN5 LARGE 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| HKG.AN5.Pro.GIANT | 12 核／24GB | 640GB | 6000GB @1Gbps | $759.90／月 | [ 看 AN5 GIANT 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |

AN5 和 AS3 走的是同一套 CN2 GIA 路由，差別在硬體：AN5 換上 EPYC 9005 與 DDR5，同價位帶的 SSD 與記憶體也更大。如果你在意單核效能或資料庫回應速度，多付的那一點通常值得；單純放靜態網站，AS3 就夠了。

### Eyeball（AS3 平台，移動 CMI 為主）

| 方案 | CPU／記憶體 | SSD | 月流量／頻寬 | 價格 | 購買 |
| --- | --- | --- | --- | --- | --- |
| HKG.AS3.EB.TINY | 1 核／1GB | 20GB | 1TB @1Gbps | $29.90／月 | [ 看 EB TINY 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.STARTER | 1 核／2GB | 40GB | 2TB @2Gbps | $59.90／月 | [ 看 EB STARTER 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.MINI | 2 核／2GB | 60GB | 3TB @2Gbps | $89.90／月 | [ 看 EB MINI 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.MICRO | 4 核／4GB | 80GB | 4TB @4Gbps | $129.90／月 | [ 看 EB MICRO 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.MEDIUM | 4 核／8GB | 160GB | 6TB @4Gbps | $199.90／月 | [ 看 EB MEDIUM 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.LARGE | 8 核／16GB | 320GB | 12TB @4Gbps | $389.90／月 | [ 看 EB LARGE 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |
| HKG.AS3.EB.GIANT | 8 核／24GB | 640GB | 24TB @4Gbps | $789.90／月 | [ 看 EB GIANT 方案](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=eyeball&aff=12046) |

> Eyeball 目前補貨不固定，官網也把它標為 Beta 網路。要拿它跑正式業務前，建議先確認當下的庫存與路由說明，別只看價格。

## 所以你到底該點哪一台

把常見需求對到方案上，會清楚很多。

**外貿官網、跨境電商，客戶主要在歐美或東南亞：** Tier 1 就對了。$12.90/月的 STARTER 給 4TB 流量與 10Gbps 埠，超量降速不停機，放在國際線路上完全稱職。沒有必要為了「反正香港嘛」多付三倍錢買 CN2 GIA。

**部落格、企業站，訪客七成在大陸：** 從 HKG.AS3.Pro.TINY 起跳，$39.90/月。500GB 流量對一般圖文站很夠，真的撐不住再加購流量或直接升 STARTER。這是三條線裡唯一把電信、聯通、移動都安排好的檔位。

**主要用戶用移動網路，預算有限：** Eyeball 是合理選項，回程 CMI 對移動用戶友善，同價位流量給得比 Premium 多。前提是你能接受它的 Beta 標籤與斷貨頻率。

**跑下載、鏡像、備份或大流量中轉：** Tier 1 的 MICRO 以上。16TB 起跳的流量加上超量降速，等於一台降速版的不限流量香港機器，這在三條線裡是獨一份。

**需要大量 vCPU 跑資料庫或容器：** HKG.AN5.Pro.MEDIUM 的 6 核／8GB，或再往上的 LARGE 與 GIANT。AS3 平台的上限就到 MEDIUM 那一階，再上去要換到 AN5。

## 下單前先自己 ping 一次

DMIT 有公開的測試 IP，這是判定線路最直接的方法，比任何測評文章都準，因為你的 ISP 跟別人不一樣：

- Premium：`103.117.100.199`
- Eyeball：`154.12.188.3`
- Tier 1：`154.12.176.28`

在晚間 8 點到 11 點這段時間 ping 一輪，看平均延遲跟丟包率。電信用戶如果測 Tier 1 測出 200ms 以上，那是正常的，不是機器壞了——這條線路本來就沒有為大陸做優化。

香港節點部署在本地專業資料中心（官方說法是 Equinix HK2），節點本身沒有「便宜機房」那種品質問題，真正的變數只有線路和你的訪問位置。

## 付款、優惠碼與幾個實務細節

付款方式包含信用卡、PayPal、支付寶與微信支付，對兩岸三地的使用者來說門檻不高，官方也有中文客服。

至於優惠碼：目前沒有可確認仍然有效的公開優惠碼。DMIT 過去確實推過 Tier 1 年付 45% 的循環折扣碼，但活動頁面已經明確標示「HKG Tier 1 系列產品升級優惠活動已結束」。也就是說，現在官網上的 $36.90/年、$6.90/月 這類數字本身就是特價，不需要再去找碼。看到有人貼舊碼給你，先當作無效處理比較安全。

另外兩件值得先知道的事：**DMIT 香港全系列只提供 Linux 系統，沒有 Windows VPS**；IP 更換有官方規則與費用，如果你的業務對 IP 狀態很敏感，下單前把這部分看清楚。

## 常見問題

**香港伺服器真的免備案嗎？** 香港不在中國大陸的備案體系內，用香港節點放網站不需要 ICP 備案，這是很多人選它的第一個理由。但反過來說，若你的使用者主要在境內，沒有備案也可能影響部分推廣與 CDN 接入，這要看你自己的業務型態。

**Tier 1 便宜這麼多，是不是偷工減料？** 不是。硬體規格、EPYC 平台、SSD、KVM 架構都一樣，省下來的是大陸路由優化。你付的錢買的是回程走哪條路，不是 CPU。

**為什麼 Premium 常常缺貨？** 熱門檔位庫存本來就有限，CN2 GIA 資源也不是想加就加。想買的話，留意官方或第三方補貨通知會比每天刷頁面有效率。

**可以直接把 Eyeball 升成 Premium 嗎？** 不同線路系列之間不能直接切換，得重新購買。這也是為什麼選購前把需求想清楚比較省事。

**流量超了會怎樣？** 回去看上面那張對比表：Tier 1 降速繼續跑，Premium 與 Eyeball 暫停服務。

## 收尾

香港伺服器租用的決策鏈其實只有三層：訪客在哪、要多少流量、超量時能不能停機。這三題答完，Tier 1、Eyeball、Premium 誰該上場就決定了，剩下才是挑 CPU 和記憶體。

DMIT 的定位一直很明確——價格不算便宜，賣點是三網直簽的線路資源與不超售的硬體。如果你的業務剛好需要香港節點、又對大陸訪問速度有要求，它是值得放進比較清單的選項；如果你的訪客全在海外，那 Tier 1 的 $12.90/月 反而更划算。

先 ping 測試 IP，再決定要刷哪張卡。

👉 [前往 DMIT 查看香港節點最新方案與即時庫存](https://www.dmit.io/aff.php?aff=12046)
