# 1.Ghidra 
```
NSA釋出逆向工程工具包及防供應鏈攻擊的軟體
美國國安局在RSA會議上開源逆向工程工具包Ghidra，以及可預防供應鏈攻擊的HIRS軟體
文/陳曉莉 | 2019-03-08發表
https://www.ithome.com.tw/news/129196

Ghidra是NSA多年來為解決當局各種棘手任務所開發的產品，為一支援客製化與擴充的軟體反向工程平台，
它包含各種軟體分析工具，可於不同的平台上分析編譯過的程式碼。
....
免費釋出Ghidra將有助於替網路安全專業人士提供公平的競爭環境，特別是那些業界新鮮人，
預期Ghidra也能用來強化學校或企業的網路安全教育。
```

```
Ghidra: NSA Reverse Engineering Software

Ghidra is a software reverse engineering (SRE) framework 
developed by NSA's Research Directorate. 

This framework includes a suite of full-featured, high-end software analysis tools 
that enable users to analyze compiled code 
on a variety of platforms including Windows, Mac OS, and Linux. 

Capabilities include disassembly, assembly, decompilation, graphing, and scripting, 
along with hundreds of other features. 

Ghidra supports a wide variety of process instruction sets and executable formats 
and can be run in both user-interactive and automated modes. 
Users may also develop their own Ghidra plug-in components 
and/or scripts using the exposed API.

In support of NSA's Cybersecurity mission, Ghidra was built to solve scaling 
and teaming problems on complex SRE efforts, 
and to provide a customizable and extensible SRE research platform. 

NSA has applied Ghidra SRE capabilities to a variety of problems 
that involve analyzing malicious code and generating deep insights for NSA analysts 
who seek a better understanding of potential vulnerabilities in networks and systems.
```
```
Ghidra是一個逆向工程工具,由美國國安局(NSA)在2019年3月5日的RSA安全會議中展示並免費釋出。
其框架內含完整功能的軟體分析工具,能適用於各種平台包含Windows,Mac和Linux, 
其主要功能包含反組譯,組譯,反編譯以及繪圖和腳本以及更多其它不及繁載的功能。
Ghidra也支援各種不同的指令及架構,以及可執行檔(PE,ELF…), 
在使用上則可以選擇使用者互動模式及自動模式。
若預設的功能無法完成使用者想要的結果,它也提供了公開的API允許使用者用以自行開發個人的插件及腳本

NSA逆向分析工具-Ghidra 使用心得與實例展示
https://secbuzzer.co/post/17
```
```
官方網址 https://ghidra-sre.org/
官方GITHUB : https://github.com/NationalSecurityAgency/ghidra
```
# 2_安裝ghidra
```
步驟一:將安裝步驟寫成一個bash shell script(run_ghidra.sh)  <== 腳本程式
步驟二:執行安裝 ==> bash run_ghidra.sh
```
## 步驟一:將安裝步驟寫成一個bash shell script(run_ghidra.sh)
```
使用最簡單的編輯器(gedit)撰寫 run_ghidra.sh
將安裝過程中的步驟逐行撰寫(如下)
```
```
mkdir Ghidra
cd Ghidra
wget https://ghidra-sre.org/ghidra_9.0.1_PUBLIC_20190325.zip
unzip ghidra_9.0.1_PUBLIC_20190325.zip
cd ghidra_9.0.1
sudo add-apt-repository ppa:openjdk-r/ppa 
sudo apt update 
sudo apt install openjdk-11-jdk 
sudo apt install openjdk-11-jre-headless
chmod +x ghidraRun
./ghidraRun
```
```
參考資料
Ghidra Installation on Ubuntu |18.04, 16.04, 14.04
Posted on March 26, 2019 by Yılmaz Cemalettin
https://www.ylmzcmlttn.com/2019/03/26/ghidra-installation-on-ubuntu-18-04-16-04-14-04/
```
```
安裝腳本程式的說明
mkdir Ghidra    <==建立Ghidra
cd Ghidra      <==切換到Ghidra目錄
wget https://ghidra-sre.org/ghidra_9.0.1_PUBLIC_20190325.zip <== 在Ghidra目錄下載安裝檔
unzip ghidra_9.0.1_PUBLIC_20190325.zip <== 解壓縮 安裝檔
cd ghidra_9.0.1 <== 切換到解壓縮後的目錄

          ==>底下是 安裝 ghidra 所需要的 JAVA 執行環境
sudo add-apt-repository ppa:openjdk-r/ppa  
sudo apt update 
sudo apt install openjdk-11-jdk 
sudo apt install openjdk-11-jre-headless

chmod +x ghidraRun <== 將 ghidraRun執行檔 設定成 可執行
./ghidraRun <== 執行
```
## 步驟二:執行安裝 ==> bash run_ghidra.sh
```
bash run_ghidra.sh

要一段時間 即可安裝成功
```
# 3_執行 Ghidra ==> 圖形介面(GUI Mode)
```
切換到安裝目錄 ==> 執行 ghidraRun 啟動
```

```
could not find decompiler executable decompile #1495
https://github.com/NationalSecurityAgency/ghidra/issues/1495

不支援32 位元
```
# 4_使用Ghidra解CTF
```
本課程將示範講解一個範例題
底下列出參考資料提供學員加強學習
```
```
主動學習 ==>參考底下文章練習 
NSA逆向分析工具-Ghidra 使用心得與實例展示
2019-03-11 陳尚文
https://secbuzzer.co/post/17
```
```
參考別人的解題技巧 ==> Sanitize 解題
https://github.com/ENOFLAG/writeups/blob/master/0ctf2019/sanitize.md
```
```
Ghidra and IDA - Solving a reverse engineering CTF crackme - AmIRootYet - Pranshu Bajpai
觀看次數：14,259次•2019年4月28日
https://www.youtube.com/watch?v=S06pgk4DjFQ
```
```
Reversing CrackMe with Ghidra (Part 1)
觀看次數：18,628次•2019年9月20日
https://www.youtube.com/watch?v=6p5Qviusskk&t=33s
```
```
Reversing CrackMe with Ghidra (Part 2)
觀看次數：6,032次•2019年10月9日
https://www.youtube.com/watch?v=Eu9YC1Jq1Do
```

