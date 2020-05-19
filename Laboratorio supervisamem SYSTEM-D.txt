cd /opt/scripts
chmod 700 supervisamem
 chmod 700 iniciar-supervisamem
/etc/init.d/ iniciar-supervisamem
-------------------------------------------------------- 
cd /etc/systemd/system
vi supervisamem.service

[Unit]
Description=Daemon of axample
[Service]
ExecStart=/etc/init.d/iniciar-supervisamem start
ExecStop=/etc/init.d/iniciar-supervisamem stop
Type=forking
[Install]
WantedBy=multi-user.target
------------------------------------------------
systemctl daemon-reload
systemctl start supervisamem.service
tail -f /var/log/supervisamem.log
systemctl stop supervisamem

systemctl enable suspervisamem.service