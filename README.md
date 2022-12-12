# tssv2Gui
Tssv2Gui Basics of running tool. needs work but works 

TSSv2GUI User Guide.


#1 The Tool is easy to kick logs off 
#2 The First GUI page has the primary Ways to stop collection secton
If you had been playing around with the tool, it may seem to stop working. This is likely because you kicked off a persistent job earlier. Its likely running and generating logs.
The option you want to choose is KILLLOGS. This will set you back to a baseline state. 
NOTE: You may have to choose stop or stopautologger before finally running the Killlogs to stop all collection 
Killlogs runs this command .\TSSv2.ps1 -Stop -noBasiclog -noXray

 


#3 The Collections that have to do with clustering are frequently SHA_XXXX where X is the service or process for the cluster, Hyper-v or other topic. 

![image](https://user-images.githubusercontent.com/79279019/206972792-c800d489-595c-454d-9b85-a56c125d5fe3.png)

#4 The Tssv2Gui Script must be located in a folder inside the Tssv2 Folder. More precicely, it needs to be one level deeper then the tssv2.ps1 script. The dependency is on the reletive path- one level higher then the gui script. That’s where it expects to find tssv2.ps1


#5 You can run the Tssv2Gui in Powershell ISE and it will try to spin an admin window. However this is not 100% reliable. But I overcame some of the issue in some degree

#6 not all combinations are valid and I will eventually work to address that. 

#7  The Monitoring GUI is the most advanced. If you were to complete the last text box with the deeper complexity switch 0:5:0 etc… it would work. I am limiting the complexity for the moment. 

On this note- if you want to change the way the script runs, you could just grab the strings by searching for these lines in each function:
Start-Process -FilePath "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -ArgumentList "-NoProfile -NoLogo -noexit -ExecutionPolicy Bypass `"$script:finalog`" -ErrorAction Stop" 

Look at the $script variable. In this case Finalog is defined above this command (in script)  and is nothing more then the powershell command switchs added together with a + sign. You can use a plus sign and add any additional items as hard code- to send to customers to use. 

#8 the limitations of this gui is that it only allows you to select one log componebt at a time. This is easily overcome by running scearios or log collection. 

#9. The Get-SDDC is located under collectlog 
SHA_Cluster
SHA_Hyp
SHA_VM

