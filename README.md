# DNoiSe
DNS noise generator that looks at your network activity and blends in. Requires [pi-hole](https://pi-hole.net) to run.

## Why bother?
1. Does your DNS provider log your queries? If it does, you should change your DNS provider. But if you can't, this will make it harder for them to profile you based on your DNS requests. Not impossible, but harder.
2. Plausible deniability.

## Dependencies
```
pip install pandas (raspberry pi users should use 'sudo apt-get install python-pandas' instead)
pip install requests
pip install dnspython
```

## Recommended setup
1. Run this on the same machine that hosts your pi-hole instance.
2. Put this in your `crontab -e` to make it run after reboot
`@reboot /usr/bin/python /home/pi/DNoiSe.py`
3. That's all there is to it. The script will sample network activity every minute and add 10% extra DNS queries made randomly to Cisco's top 1M domain list.
