# Cara Pemakaian

## Kebutuhan
- 2 vm/server
- 1 untuk master
- 1 untuk node

## Sebelum mulai
jalankan di vm/server node
- buat file src di vm/server node pada ``` /media/src ```
- paste file index.html ke folder src yang sudah di buat tadi

## Cara menjalankan
jalankan di vm/server master
- ``` kubectl create -f volume.yml ```
- ``` kubectl create -f deployment.yml ```

## Melihat di browser
buka localhost:30999
