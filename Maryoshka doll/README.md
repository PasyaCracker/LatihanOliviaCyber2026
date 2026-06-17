Matryoshka doll
Forensics
30 pts

Deksripsi chalengge
Matryoshka doll merupakan chalengge berbasis forensik yang mengharuskan penantang untuk menemukan flag dari sebuah gambar dengan nama file: dolls.jpg
Petunjuk yang diberikan:
- sebuah file dapat disembunyikan dalam suatu file

Langkah penyelesaian

Menurut petunjuk yang diberikan yakni file yang tersembunyi di dalam file…. maka ini merupakan tantangan yang berkaitan dengan steganografi.
Untuk itu pertama tama saya mencoba menggunakan tools binwalk online untuk menganalisa file tersembunyi apa yang ada di dalam gambar

![binwalk online](bwo.png)
File tersembunyi ditemukan yang berupa file .zip, namun karena keterbatasan tools binwalk online jadi tidak bisa secara langsung melihat isi file zipnya, bisa untuk ekstrak namun tidak bisa melihat isi filenya… jadi saya langsung mencoba untuk menggunakan binwalk secara langsung via wsl dengan command: binwalk + direktori file dolls.jpg yang ada di windows.(binwalk /mnt/c/users/ASUS/Downloads/dolls.jpg

Setelah menggunakan binwalk ditemukan file zip yang tersembunyi dalam gambar dolls.jpg: base_images/2_c.jpg, ini sesuai petunjuk yang dimana terdapat file tersembunyi di dalam gambar ini, kemudian saya menggunakan command binwalk kembali dengan masuk terlebih dahulu kedalam direktori dolls.jpg menggunakan command: 
cd /mnt/c/users/ASUS/Downloads/

Setelah masuk kedalam direktori saya menggunakan command binwalk -e dolls.jpg untuk mengekstrak file zip yang tersembunyi dalam gambar

Hasil setelah command dijalankan, warning: one or more files failed to extract. Hal ini biasanya terjadi karena keterbatasan proses ekstraksi otomatis di lingkungan OS(WSL). oleh karena itu proses ekstraksi harus dilakukan secara manual dan saya menggunakan unzip untuk proses ekstraksinya, command: unzip dolls.jpg

Ditemukan file image baru didalamnya, kemungkinan ini akan memuat beberapa file zip tersembunyi dan tentunya dengan beberapa file image juga, jadi saya lanjutkan dengan masuk ke direktori base_images dan melakukan unzip kembali pada file 2_c.jpg: cd base_images
unzip 2_c.jpg

Ditemukan file 3_c.jpg, karena polanya mirip maka saya langsung mengulang command sebelumnya yang diganti hanya nama file jpgnya saja:
cd base_images, unzip 3_c.jpg

cd base_images, unzip 4_c.jpg

Setelah 3 kali memasuki direktori base_images dan melakukan unzip dari file dolls.jpg,2_c.jpg,3_c.jpg, dan 4_c.jpg, ditemukan file flag.txt yang kemungkinan besar berisi flag dari tantangan ini, jadi proses ekstrak manual berakhir dan saya menggunakan command cat untuk menampilkan isi dari flag.txt
Command: cat flag.txt

Flag pun ditemukan:
picoCTF{LL91b1dR4QbGe414iWCvGq9pdtwt7392}
