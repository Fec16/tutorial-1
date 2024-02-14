# Tutorial 1

**Nama** : **Jason Kent Winata** <br/>
**NPM** : **2206081313** <br/>

## Modul 1
## Refleksi 1: Clean Code and Secure Coding
Saya sudah mengimplementasikan dua fitur baru menggunakan Spring Boot. Setelah meninjau ulang source code, saya mengevaluasi standar penulisan kode yang telah saya pelajari dalam modul ini. Berikut adalah prinsip-prinsip penulisan clean code dan secure coding practices yang telah saya terapkan dalam kode saya:

1. **Meaningful Name**: Saya menggunakan nama variabel yang deskriptif dan bermakna, seperti productRepository dan productService, untuk meningkatkan keterbacaan kode.
2. **Function**: Metode-metode dalam kelas saya memiliki tanggung jawab yang terpisah, mengikuti prinsip Single Responsibility Principle. Selain itu, nama Function menerapkan prinsip clean code dan panjang Function tidak melebihi layar.
3. **Comment**: *Comments do not make up for bad code.* Saya meminimalisir penggunaan comment dan menerapkan meaningful names pada variable dan function, sehingga kode menjadi jelas dan self-explanatory.
4. **Objects and Data Structure**: Objects dibuat private agar terenkapsulasi dan terlindungi sehingga tidak mudah dimanipulasi. Lalu, ada Interface service yang mempermudah pengembangan kode.
5. **Error Handling**: Masih harus diperbaiki karena tidak semua error ter-handle dengan baik contoh productName yang kosong dan productQuantity yang kurang dari 0.

## Refleksi 2: Unit and Functional Tests
1. Setelah menulis unit test dan menjalankannya lalu berhasil, saya merasakan kepuasan telah menyelesaikan Module 1. Namun, memiliki Code Coverage 100% tidak menjamin bahwa kode tersebut bebas dari bug atau kesalahan. Bisa saja terdapat error-error yang tidak terdeteksi dan kode berjalan lancar namun outputnya salah.
2. Menggunakan kembali prosedur dan variabel contoh dari rangkaian tes fungsional yang ada dapat menjaga konsistensi, tetapi risiko keberagaman setup dan variabel instance meningkat seiring penambahan tes.
    - Semakin banyaknya test yang ditambahkan dapat menyebabkan keragaman pada prosedur setup dan variabel instance, yang berpotensi memerlukan variabel dan setup yang berbeda, sehingga diperlukan perbaruan pada setup baru.
    - Penambahan rangkaian tes yang baru bisa menghasilkan duplikasi kode jika variabel contohnya sama dengan rangkaian tes yang sudah ada.
    - Bisa saja beberapa nama Test Case kurang deskriptif, sehingga sulit dipahami. 

## Modul 2
1. - JUnit5 test classes and methods should have default package visibility (Intentionality)<br/>
   Solution: Remove the 'public' modifier.
   - Add at least one assertion to EshopApplicationTests (Adaptability)<br/>
   Solution: Make a new test 'mainMethodDoesNotThrowException' to increase code Adaptability

2. - My current CI/CD workflow implementation seems to have met the basic definition of Continuous Integration and Continuous Deployment. The CI workflows focus on testing code changes to ensure they check for code quality issues, vulnerabilities, and don't break existing features. <br/>
   - By using GitHub workflows, the project automates CI processes such as running tests and CD processes like deployment whenever code changes are pushed to the repository. Each push triggers tests defined in the ci.yml file and code scans using SonarCloud. Once the code is deemed satisfactory, it's merged into the main branch, triggering deployment to the Koyeb platform and security checks using the scorecard.yml action. These actions collectively form an automated workflow within the Software Development Lifecycle.