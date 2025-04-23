salam kako

steps to run a gui and no vnc 


sudo apt update && sudo apt install -y xfce4 tightvncserver novnc


sudo apt update && sudo apt install -y tigervnc-standalone-server xfce4 xfce4-goodies

mkdir -p ~/.vnc
vncpasswd


cat > ~/.vnc/xstartup << 'EOF'
#!/bin/sh
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
exec /usr/bin/xfce4-session
EOF
chmod +x ~/.vnc/xstartup



vncserver :1 -geometry 1280x800 -depth 24 -SecurityTypes None


websockify --web /usr/share/novnc 6080 localhost:5901