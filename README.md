# Running on Windows 10 and WSL2 Ubuntu

1. Allow __inbound__ and __outbound__ traffic in your Windows Firewall on port `19000`

2. In PowerShell terminal of your WSL2 user find IP address:
```powershell
bash.exe -c "ifconfig eth0 | grep 'inet '"
```

3. Run new PowerShell window as admin :
```powershell
Start-Process powershell -verb runas
```
4. Set up port forwarding using `<WSL2_IP_ADDRESS>` from pt. 2
```powershell
netsh interface portproxy add v4tov4 listenport=19000 listenaddress=0.0.0.0 connectport=19000 connectaddress=<WSL2_IP_ADDRESS>
```

6. In the Linux terminal run:
```bash
export REACT_NATIVE_PACKAGER_HOSTNAME=$(netsh.exe interface ip show address "Wi-Fi" | grep 'IP Address' | sed -r 's/^.*IP Address:\W*//')
```

7. Run app with:
```
npm start
```

8. Using provided QR code load app on your phone through `Expo Go` app.
