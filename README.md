# Belajar Nginx

## Build Nginx from Source

- Download Source Nginx di https://nginx.org/en/download.html
```
wget https://nginx.org/download/nginx-1.18.0.tar.gz
```

- Extract Sourcenya.
```
tar -xzvf nginx-1.18.0.tar.gz
```

- Masuk Ke Folder Nginx.
```
cd nginx-1.18.0/
```

- Sebelum melakukan compiling, diharapkan menginstal alat compilingnya terlebih dahulu.
```
sudo apt update
```
```
sudo apt install build-essential
```
```
sudo apt install libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev
```

- Setelah itu lakukan Konfigurasi.
```
./configure --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-pcre --pid-path=/run/nginx.pid --with-http_ssl_module
```

- Lalu compile hasil konfigurasi tadi.
```
sudo make
```

- Setelah itu install
```
sudo make install
```

- Untuk menjalan nginx, cukup ketik nginx diterminal lalu enter.
```
sudo nginx
```

- Berikut adalah cara menggunakan dan melihat versi nginx.
```
sudo nginx -h
```
```
sudo nginx -V
```

## Adding Nginx Systemd Service File
- Apabila Nginx masih running, dihentikan terlebih dahulu.
```
sudo nginx -s stop
```

- Masuk ke website https://www.nginx.com/resources/wiki/start/topics/examples/initscripts/
- Setelah itu pilih "NGINX systemd service file"
- Lalu buat file sesuai yang ada pada https://www.nginx.com/resources/wiki/start/topics/examples/systemd/
```
sudo vim /lib/systemd/system/nginx.service
```
- Masukan scriptnya, lalu save.
```
[Unit]
Description=The NGINX HTTP and reverse proxy server
After=syslog.target network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t
ExecStart=/usr/sbin/nginx
ExecReload=/usr/sbin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

- Cek apakah nginx systemd servicenya terdeteksi.
```
sudo systemctl status nginx
```

- Berikut untuk menjalankan nginxnya.
```
sudo systemctl start nginx
```

- Berikut untuk memuat ulang nginxnya.
```
sudo systemctl restart nginx
```

- Berikut untuk menghentikan nginxnya.
```
sudo systemctl stop nginx
```

- Berikut adalah perintah agar nginx selalu berjalan pada saat os booting.
```
sudo systemctl enable nginx
```
