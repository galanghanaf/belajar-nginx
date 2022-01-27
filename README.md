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
make
```

- Setelah itu install
```
make install
```

- Untuk menjalan nginx, cukup ketik nginx diterminal lalu enter.
```
nginx
```

- Berikut adalah cara menggunakan dan melihat versi nginx.
```
nginx -h
```
```
nginx -V
```
```
nginx -s stop
```
