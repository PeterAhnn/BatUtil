# Windows 11/10 Multilingual Distribution Creator

* This is a mini version that process install.wim file only

* Refer to README.md to see Requirements

## How To:

* Step 1
	> Create a directory on a partition with enough space on it (at least 15 GB), depending on the number of LPs you are adding (e.g. C:\MUIDVD), and extract this package to the directory your created.

* Step 2
	> Place language packs (cab/esd) files in "Langs" folder.  
	> Place ondemand packs (cab) files in "OnDemand\x86" or "OnDemand\x64" folder (based on architecture).

* Step 3
	> Place updates (msu/cab) files in "Updates" folder (you can add both architecture files together).  
edit Updates\W10UI.ini to change the updates options, but don't change Target or Repo (leave them blank)

* Step 4
	> Edit the script with notepad and adjust the following variables to suite your needs, or leave it as-is:

**WIMPATH**

Path for Windows 11/10 install.wim file (without quotation marks)

leave it blank if you want to use install.wim placed next to the script, or prompted to enter path.

**WINPE** (set 1 or 0)

when enabled "1":

require WinPE lang packs from ADK (Preinstallation Environment) to update winre.wim

when disabled "0":

winre.wim won't be updated

**SLIM** (set 1 or 0)

when disabled "0":

all applicable WinPE lang packs will be added to winre.wim

when enabled "1":

only necessary WinPE LPs will be added to winre.wim (Main, Setup, SRT)

**WINPEPATH**

optional, custom directory path for WinPE language packs files, in case you do not want to install whole ADK WinPE feature

you must keep the same directory hierarchy as original installed ADK

then you set the parent WinPE directory as path:  
`set WINPEPATH=C:\MUIDVD\WinPE`

leave it blank to auto detect the path for WinPE folder in the script current directory 

example:

x64 German files:  
`C:\MUIDVD\WinPE\amd64\WinPE_OCs\de-de`

x86 Arabic files:  
`C:\MUIDVD\WinPE\x86\WinPE_OCs\ar-sa`

**DEFAULTLANGUAGE**

culture code of the default language that will be set in the Windows images

leave it blank if you want to keep the current default language in install image.

**MOUNTDIR**

optional, set mount directory on another partition if available to speed integration, or leave it blank

* Step 5
	> Verify that all your settings are correct and that the required files are in the proper location. Then, execute the script as Administrator.

	> The process will take quite some time to finish depending on number of LPs to add, so WAIT. If all went OK, You will get the "Finished" message.

## Remarks:

* install.wim file will be modified and updated directly. Make sure it's not read-only (i.e. don't select a file directly from dvd or mounted iso, instead copy it next to the script)

* Build version will be determined based on install.wim file

* Language files, codes and architecture will be determined based on the detected files in "Langs" folder

* All detected files in "OnDemand" folder will be added as supplementary packges

* to spare yourself the trouble, keep the work directory path short, do not use spaces and do not use non-ASCII characters. 
