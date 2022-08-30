# When running on WSL2

1. Open Windows firewall and allow inbound traffic on port `19000`

2. Then inside WSL2 Linux terminal run:
```bash
export REACT_NATIVE_PACKAGER_HOSTNAME=$(netsh.exe interface ip show address "Wi-Fi" | grep 'IP Address' | sed -r 's/^.*IP Address:\W*//')
```

3. Check IP with:
```bash
echo Meteor will use dev machine IP address: $REACT_NATIVE_PACKAGER_HOSTNAME
```

4. Run app with:
```
npm start
```

5. Using provided QR code load app on your phone through `Expo Go` app
