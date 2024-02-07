# Tutorial 1

**Nama** : **Jason Kent Winata** <br/>
**NPM** : **2206081313** <br/>

## Refleksi 1: Clean Code and Secure Coding
Saya sudah mengimplementasikan dua fitur baru menggunakan Spring Boot. Setelah meninjau ulang source code, saya mengevaluasi standar penulisan kode yang telah saya pelajari dalam modul ini. Berikut adalah prinsip-prinsip penulisan clean code dan secure coding practices yang telah saya terapkan dalam kode saya:

1. **Meaningful Name**: Saya menggunakan nama variabel yang deskriptif dan bermakna, seperti productRepository dan productService, untuk meningkatkan keterbacaan kode.
2. **Function**: Metode-metode dalam kelas saya memiliki tanggung jawab yang terpisah, mengikuti prinsip Single Responsibility Principle. Selain itu, nama Function menerapkan prinsip clean code dan panjang Function tidak melebihi layar.
3. **Comment**: *Comments do not make up for bad code.* Saya meminimalisir penggunaan comment dan menerapkan meaningful names pada variable dan function, sehingga kode menjadi jelas dan self-explanatory.
4. **Objects and Data Structure**: Objects dibuat private agar terenkapsulasi dan terlindungi sehingga tidak mudah dimanipulasi. Lalu, ada Interface service yang mempermudah pengembangan kode.
5. **Error Handling**: Masih harus diperbaiki karena tidak semua error ter-handle dengan baik contoh productName yang kosong dan productQuantity yang kurang dari 0.