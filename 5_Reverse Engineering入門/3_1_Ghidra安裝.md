# 1.Ghidra 

```
Ghidra is a software reverse engineering (SRE) suite of tools 
developed by NSA’s Research Directorate in support of the Cybersecurity mission.

Ghidra is open-source.
```
```
Ghidra: NSA Reverse Engineering Software
Ghidra is a software reverse engineering (SRE) framework developed by NSA's Research Directorate. 

This framework includes a suite of full-featured, high-end software analysis tools 
that enable users to analyze compiled code on a variety of platforms including Windows, Mac OS, and Linux. 

Capabilities include disassembly, assembly, decompilation, graphing, and scripting, 
along with hundreds of other features. 

Ghidra supports a wide variety of process instruction sets and executable formats 
and can be run in both user-interactive and automated modes. 
Users may also develop their own Ghidra plug-in components and/or scripts using the exposed API.

In support of NSA's Cybersecurity mission, Ghidra was built to solve scaling 
and teaming problems on complex SRE efforts, 
and to provide a customizable and extensible SRE research platform. 

NSA has applied Ghidra SRE capabilities to a variety of problems that involve analyzing malicious code and generating deep insights for NSA analysts 
who seek a better understanding of potential vulnerabilities in networks and systems.
```
# 安裝ghidra
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
# 執行 Ghidra ==> 圖形介面(GUI Mode)
```
切換到安裝目錄 ==> 執行 ghidraRun 啟動
```

```
could not find decompiler executable decompile #1495
https://github.com/NationalSecurityAgency/ghidra/issues/1495

不支援32 位元
```
# 使用Ghidra解CTF
```
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

