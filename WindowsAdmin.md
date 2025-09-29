# Notes for Windows Administration


## Windows built-in virtualization
"Hyper V" is a virualization software (kind of like VirtualBox) that's built into windows  
Hyper V can be enabled through Windows Control Panel  
When setting up Hyper V Manager, you can set up a "Virtual Switch Manager" to have a customized network configuration.  
"Quick Create" allows you to create a new session based on previous configurations  
When attaching an ISO to the newly created virtual machine, make sure the Firmware Boot order is configured correctly  
It is a good practice to rename the device name to the virtual machine name as, by default, they are not the same.  
Checkpoints are not backups, so ensure backups are made consistently. Checkpoints are good for minor changes, backups are essential for major changes.  
Deleting the VM in Hyper V does not delete Hard disk file of the VM. This hard disk file can be used in a future VM by selecting it during the "connect Virtual hard disk" step of VM creation. Otherwise, delete the hard disk file through file explorer.

Windows Sandboxes are a much simpler version of a VM, but can only run Windows OS. It can also be enabled in the Windows Control Panel.
The Linux alternative is "Windows Subsystem for Linux" which is also enabled in Windows Control Panel. You can choose the linux distro through the Windows store, install it, and run 

## Group Policy
Can be enabled through Settings -> Apps & Features -> Optional Features -> RSAT: Group Policy Management Tools
Enterprise updates can be affected in Group Policy Management in Computer configuration -> policies -> administrative templates-> Windows components -> Windows Update
You can save a lot of bandwidth setting up a WSUS server, or a server that hosts windows updates for your enterprise. In the above group policy, you can find "Specify Intranet Microsoft Update Service Location", put in the wsus server url in the options (will need a port number in the URL), and specify the Statistics server (can be the same server).

##PowerShell
ISE is beginner friendly and shows cmdlets that you can use to help you get used to PS7. The file format for PowerShell scripts  are .ps1 files.  
Devices inately restrict using Powershell scripts, so you will have to unrestrict before executing, then restrict it again after you are finished executing the script(s) by using "Set-ExecutionPolicy Unrestricted"

## Command Line Rosetta Stone

| Language | help | dir | tasks | kill | read file | search | network info |
|---|---|---|---|---|---|---|---|
| Bash | man | ls | ps | kill | cat | grep | ifconfig|
| CMD | help | dir | tasklist | taskkill | type | findstr | ipconfig |
| PowerShell | Get-Help | Get-ChildItem | Get-Process | Stop-Process | Get-Content | Select-String | Get-NetIPConfiguration|

## Linux Command-line cheat sheet

| Purpose | Code |
|---|---|
|Search for pattern1 and pattern2 in the same line | egrep 'pattern1,*pattern2 \| pattern2.*pattern1' in_file(s) |
|Print value of field number (or column) in_file | awk -F '<delim' '{print $field_num}' in_file|
|Replace ALL occurrences of find with replace | sed 's/find/replace/g' in_file > out_file |
|Record a terminal session; flush output after each write | script -af out_file |
