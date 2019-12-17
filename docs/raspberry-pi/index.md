# Raspberry Pi

Raspberry pi 中文稱作樹莓派，是基於 `Linux` 的單晶片電腦，由英國樹莓派基金會開放，目的是以低價硬體及自由軟體促進學校的基本電腦科學教育。

## OS

已知有一下幾種 OS
1. Raspbian（官方推薦OS）
2. LibreELEC
3. Ubuntu MATE
4. Ubuntu Core
5. Windows 10 loT
6. PiNet
7. RISC OS
8. Weather Station
9. lchigoJam RPi
10. recalbox（遊戲OS - 安裝容易，裝即玩）
11. retropie（遊戲OS - 安裝繁瑣，但是遊戲支持完整）

## Model

硬體規格

|Model | 1A | 1A+ | 1B | 1B+ | 2B | 3B | 3B+ | 3A+ | 4B      |
|------|----|-----|----|-----|----|----|-----|-----|---------|
|Price|$25 |$20  |$35 |$35  |$35 |$35 |$35  |$35  |$35/45/55|
|CPU|ARM1176JZF-S|ARM1176JZF-S|ARM1176JZF-S|ARM1176JZF-S|ARM Cortex-A7|ARM Cortex-A53 64位元|ARM Cortex-A53 64位元|ARM Cortex-A53 64位元|ARM Cortex-A72|
|GPU|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|Broadcom VideoCore IV|H.265 (4Kp60), H.264 (1080p60 / 1080p30) 
|RAM|256M|256M|256/512M|256/512M|1G|1G|1G|512M|1/2/4GB|
|USB 2.0|1|1|2|2|4|4|4|1|2|
|USB 3.0|0|0|0|0|0|0|0|0|2|
|輸出|HDMI|HDMI|HDMI|HDMI|HDMI|HDMI|HDMI|HDMI|HDMI|
|儲存|SD/MMC/SDIO|MicroSD|SD/MMC/SDIO|MicroSD|MicroSD|MicroSD|MicroSD|MicroSD|MicroSD|
|网络|/|/|10/100Mbps 乙太網介面|10/100Mbps 乙太網介面|10/100Mbps 乙太網介面|10/100Mbps 乙太網介面|10/100Mbps 乙太網介面|100/1000Mbps 乙太網介面|100/1000Mbps 乙太網介面|
|

***注意：3B,3B+ 目前的散热比 4B 好，如果要玩游戏，建议先使用 3B, 3B+***

***注意：如果想搞串流，架子和外壳可能要做好需要定制的准备***

## Server

如果想把 `raspberry pi` 当 server 也是可以的，利用 `Raspbian SSH` 的方法，流程如下：

1. 先下载 `Raspbian` 烧到 microSD 中（用 `balenaEther`）。
2. 安全退出 microSD 卡後，重新接回電腦。
3. 新的 microSD 卡一般會被更名為 `boot`，在 `boot` 中建立一個 `ssh` 的檔案。
4. 建立一個 `wpa_supplicant.conf` 裡面填寫 `WIFI` 資料。
5. 退出 microSD 卡，接到 `raspberry pi` 上。
6. 開機，等個一分鐘讓開機流程跑完。
7. 找到IP，進行連線。

[balenaEther](https://www.balena.io/etcher/)
[不外接螢幕也可以開啟 `Raspbian SSH` 的方法](https://medium.com/@Insidehand79/%E6%A8%B9%E8%8E%93%E6%B4%BE%E4%B8%8D%E7%94%A8%E5%A4%96%E6%8E%A5%E8%9E%A2%E5%B9%95%E4%B9%9F%E5%8F%AF%E4%BB%A5%E9%96%8B%E5%95%9Fraspbian-ssh%E7%9A%84%E6%96%B9%E6%B3%95-5d077daec309)

## 玩复古游戏

如果你和我一樣，搞 `raspberry pi` 是為了玩復古遊戲，建議選擇的 OS 有兩種 `recalBox` 及 `retropie` 兩種選擇，如果不是程序員，建議可以使用 `recalBox` 設定的東西比較少，且依據官網教程下載並匯入 `ROM` 後就可以開始享受遊戲帶來的樂趣了。 

### RecalBox

[官方網站](https://yaowen1978.blogspot.com/2015/04/recalboxos.html)

 - 添加 `ROM` 時候建議使用內網，透過 GUI 介面把遊戲添加進去。
 - 添加 `ROM` 时候请注意副档名，每个模拟器用的副档名都不同。
 - 每次添加 `ROM` 或是修改游戏讯息时候，记得先关闭模拟器，填写完后再开启，不然可能会有填写不进去的问题。

[recalBox 中文教程](https://yaowen1978.blogspot.com/2015/04/recalboxos.html)  
[ROM下載](https://romsmania.cc/)

### Retro-pi

[支持的模拟器列表](https://github.com/retropie/retropie-setup/wiki/Supported-Systems)  
[下载 ROMS](https://raspberrytips.com/download-retropie-roms/)

## Reference

[樹莓派](https://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE)  
[ROM](https://zh.wikipedia.org/wiki/%E5%94%AF%E8%AE%80%E8%A8%98%E6%86%B6%E9%AB%94)  
[游戏 ROMS 下载](https://www.downloadroms.io/)
