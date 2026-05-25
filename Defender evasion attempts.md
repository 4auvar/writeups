## Caldera Agent
Our initial objective was to establish the Caldera agent, enabling us to execute various adversarial actions. The Caldera agent functions as a reverse shell, however, the payload given by Caldera for setting up the agent/reverse shell was being detected by the defender. Hence, our work commenced with securing a reverse shell that evaded detection.

## A working reverse shell
At first, our efforts to locate .exe files which we could run directly, but those were caught by the defender's detections. Since .exe files didn't allow for modifications, we pivoted to a method where we could make changes and execute quickly, a PowerShell script. Although the PowerShell script we got was also flagged by the defender, after that we performed few modification in the script, and successfully obtained a functional reverse shell without detection.

- Original: https://github.com/yehia-mamdouh/Shell3er
- My Version: https://github.com/4auvar/writeups/blob/master/Reverse-shell.ps1

Apparently we have reverse shell but due to some reason we were not able to set that in caldera (Don't remember why).

## No-defender
The following day, a tweet appeared on my mobile, detailing how to disable a defender. To our surprise, implementing the instructions did indeed disable the defender. This enabled us to execute several malicious operations that went undetected by the defender.

- Link: https://github.com/es3n1n/no-defender

## PSRansom
Following that, we experimented with another tool, PSRansom, which facilitated a ransomware attack, and it operated smoothly without encountering any issues. This attack entails two PowerShell scripts: a C2 server, which we executed on an Ubuntu/Kali machine to evade detection by the Windows defender, and a client script running on victim’s windows machine responsible for encryption and transmission of files to the C2 server.

- Link: https://github.com/JoelGMSec/PSRansom

Shyam has performed actual attack and downloaded/encrypted 1.5 GB data of one of the client.

## FilelessPELoader:
We also experimented with a tool called FilelessPELoader, designed to facilitate the dynamic loading and execution of binaries. Initially, this tool was promptly flagged by the defender. However, upon examining the associated C++ file, we pinpointed several functions that triggered the detection. After investigating these functions briefly (not in depth), we determined that we could safely omit them by commenting out the corresponding code. Consequently, we obtained a functional binary capable of loading binaries on the fly. 

However, when we attempted to use this with Mimikatz, the Windows in-memory protection system detected and removed our binary. Despite this setback, we had at least successfully developed a working PE dynamic loader.

- Original: https://github.com/SaadAhla/FilelessPELoader
- My Version: https://github.com/Gaurav-Chaleit/DynamicPELoader/blob/main/README.mdConnect your Github account 
