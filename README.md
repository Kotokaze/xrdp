# xrdp

## GUI Apps on Ubuntu (WSL)  with XRDP

## Install XRDP  
`sudo apt update && sudo apt -y upgrade`  
`sudo apt -y install xfce4`  
  → Default display Manager は `gdm3` を選択
`sudo apt -y install xrdp`  


## デフォルトポート番号などを変更  
`sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak`  
`sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini`  
`sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini`  
`sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini`  
`echo xfce4-session > ~/.xsession`  

## startwm.shを編集  
`sudo nano /etc/xrdp/startwm.sh`  
最後の二行をコメントアウトし、 `startxfce4` を追記  
```
#!/bin/sh
# xrdp X session start script (c) 2015, 2017 mirabilos
# published under The MirOS Licence
・
・
・
if test -r /etc/profile; then
        . /etc/profile
fi
# **************************************************
# ここから下を編集

# test -x /etc/X11/Xsession && exec /etc/X11/Xsession
# exec /bin/sh /etc/X11/Xsession

# xfce
startxfce4
```  

## Start  
`bash ~/path/to/xrdp/startRDP.sh`  

## Stop  
`bash ~/path/to/xrdp/stopRDP.sh`  
