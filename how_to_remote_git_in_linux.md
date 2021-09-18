## 1. Membuat Key SSH
jalankan perintah ssh-keygen pada terminal. Kemudian inputkan id (identitas) SSH anda. untuk passpharse dikosongkan saja. 
* pada terminal panggil direktori : $ cd ~/.ssh

* Kemudian ketikkan code pada terminal $ ssh-keygen
perintah ini berfungsi untuk meng-generate public/private rsa key. 
* agar file yang terbentuk menjadi rsa_id.pub dan rsa_id. pada "/home/user/.ssh/id_rsa" ketika ssh-keygen dijalankan tekan enter saja tanpa mengisi keterangan apapun. sampai muncul baris akhir SHA256. 
* Maka didalam directory ~/.ssh $ ls akan muncul file id_rsa.pub, id_rsa, dan known_hosts.

## 2. Jalankan SSH Agent dan Load SSH Key
* Untuk memastikan apakah SSH Agent sudah berjalan atau tidak, gunakan perintah :
> $ ps -e | grep [s]sh-agent

kalau hasilnya seperti "1654 ? 00:00:00 ssh-agen", berarti SSH agent sudah berjalan. 

## 3. Tambahkan SSH key ke Github
Sebelumnya ambil dulu Key public yang sudah anda buat, gunakan perintah cat. 
> cat id_anda.pub     (jika sudah di directory ~/.ssh $ contoh : $ cat id_rsa.pub)

* copy semua text yang ditampilkan 

* Lalu masuk ke "Setting>SSH and GPG Keys" Buat kunci baru dengan mengetik new SSH Key. lalu masukkan key yang sudah dibuat. 

## 4. Uji Konektivitas
Ketik perintah berikut untuk menguji konektivitas SSH ke Github
> $ ssh -T git@github.com

jika hasilnya seperti " Hi user! You've succesfully authenticated, but GitHub does not provide shell acces.

Coba clone sebuah repository dengan SSH dan lakukan push.
* contoh  : git@github.com:galangadira/IoT_Platform.git


* Itulah cara menggunakan SSH di GitHub. Kita hanya perlu membuat public key, kemudian mendaftarkannya di akun GitHub.

* Referensi : 
* https://www.petanikode.com/github-ssh/ 
* https://help.github.com/articles testing-your-ssh-connection/
* https://jhooq.com/github-permission-denied-publickey/ 
* https://www.niagahoster.co.id/blog/cara-menggunakan-ssh/ 

