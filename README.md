[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=Fec16_tutorial-1&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=Fec16_tutorial-1)
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=Fec16_tutorial-1&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=Fec16_tutorial-1)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=Fec16_tutorial-1&metric=coverage)](https://sonarcloud.io/summary/new_code?id=Fec16_tutorial-1)

# Tutorial 1

**Nama** : **Jason Kent Winata** <br/>
**NPM** : **2206081313** <br/>

## Modul 1
## Refleksi 1: Clean Code and Secure Coding
1. You already implemented two new features using Spring Boot, if you find any mistake in your source code, please explain how to improve your code! <br>
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
1. List the code quality issue(s) that you fixed during the exercise and explain your strategy on fixing them.
- JUnit5 test classes and methods should have default package visibility (Intentionality)<br/>
   Solution: Remove the 'public' modifier.
- Add at least one assertion to EshopApplicationTests (Adaptability)<br/>
Solution: Make a new test 'mainMethodDoesNotThrowException' to increase code Adaptability

2. Look at your CI/CD workflows (GitHub)/pipelines (GitLab). Do you think the current implementation has met the definition of Continuous Integration and Continuous Deployment? 
- My current CI/CD workflow implementation seems to have met the basic definition of Continuous Integration and Continuous Deployment. The CI workflows focus on testing code changes to ensure they check for code quality issues, vulnerabilities, and don't break existing features. <br/>
- By using GitHub workflows, the project automates CI processes such as running tests and CD processes like deployment whenever code changes are pushed to the repository. Each push triggers tests defined in the ci.yml file and code scans using SonarCloud. Once the code is deemed satisfactory, it's merged into the main branch, triggering deployment to the Koyeb platform and security checks using the scorecard.yml action. These actions collectively form an automated workflow within the Software Development Lifecycle.

## Modul 3
1. Explain what principles you apply to your project! <br>
These are the SOLID Principles I applied to the project:
- Single Responsibility Principle: Each class is responsible for one thing. Previously, the CarController class was nested within the ProductController class, so they needed to be separated. Additionally, the Product constructor used to assign UUIDs to Product objects, but this functionality has been moved to the 'create' method in the ProductRepository.
- Open Closed Principle: The CarController class uses the CarService interface instead of CarServiceImpl, allowing for extension without modifying existing code.
- Liskov Substitution Principle: The CarController class does not need to extend ProductController, and the CarService attribute uses the CarService interface.
- Interface Segregation Principle: By changing the CarService attribute, ProductServiceImpl and CarServiceImpl are not required to implement methods from the interface they implement.
- Dependency Inversion Principle: Removed redundant 'public' modifier for interface members. Previously, CarController used CarServiceImpl but was changed to use the CarService interface implemented by CarServiceImpl.

2. Explain the advantages of applying SOLID principles to your project with examples! <br>
**Advantages**: Generally, adhering to SOLID principles enhances the maintainability of a program.
- **Single Responsibility Principle** ensures that each class has its own function, making it easy to create test cases and debugging.
- **Open/Closed Principle** makes the program more scalable because we can add features without modifying existing code (which could potentially introduce new errors).
- **Liskov Substitution Principle** ensures that existing subclasses have the same characteristics as their parent, minimizing errors.
- **Interface Segregation Principle** ensures that a class doesn't have to implement unused methods from its interface, improving readability.
- **Dependency Inversion Principle** ensures that high-level modules don't depend on low-level modules, but both depend on abstractions like interfaces, so changes to low-level modules won't potentially disrupt high-level modules. Example: If there's an error in CarController, I'll know where to debug because its features are in its own class, namely CarController itself (SRP).

3. Explain the disadvantages of not applying SOLID principles to your project with examples! <br>
**Disadvantages**: Meanwhile, not following SOLID principles reduces the maintainability and readability of a codebase. 
- For example, if there's an interface named Service containing all methods that should be in CarService and ProductService, the implementation in CarServiceImpl must implement methods like `public Product create(Product product);` that aren't used.

## Modul 4
## Refleksi
1. Reflect based on Percival (2017) proposed self-reflective questions (in “Principles and Best Practice of Testing” submodule, chapter “Evaluating Your Testing Objectives”), whether this TDD flow is useful enough for you or not. If not, explain things that you need to do next time you make more tests. <br>
- Correctness:
  - Do I have enough functional tests to reassure myself that my application really works, from point of view of the user? _Yes._
  - Am I testing all edge cases thoroughly? _Yes._
  - Do I have tests that check whether all my components fit together properly? Could some integrated tests do this, or are functional tests enough? _Yes. Functional tests are enough, but through integrated tests it will be more thoroughly checked._

- Maintainability:
  - Are my tests giving me the confidence to refactor my code, fearlessly and frequently? _Yes._
  - Are my tests helping me to drive out a good design? If I have a lot of integration tests but less unit tests, do I need to make more unit tests to get better feedback on my code design? _Yes. If those better feedbacks are actually helping the code design, why not?_

- Production workflow:
  - Are my feedback cycles as fast as I would like them? When do I get warned about bugs, and is there any practical way to make that happen sooner? _Yes. As of now, the feedback cycles have satisfied my expectation._
  - Is there some way that I could write faster integration tests that would give me feedback quicker? _Regularly review and refactor tests._
  - Can I run a subset of the full test suite when I need to? _Yes._
  - Am I spending too much time waiting for tests to run, and thus less time in a productive flow state? _No._

2. You have created unit tests in Tutorial. Now reflect whether your tests have successfully followed F.I.R.S.T. principle or not. If not, explain things that you need to do the next time you create more tests. <br>
- I have successfully followed F.I.R.S.T principle:
  - My tests run as soon as possible and does not interrupt my workflow.
  - My tests are separated into unit tests and functional tests.
  - My tests do not interfere and change function states or dependent on other test cases.
  - My tests are consistent on repeated runs.
  - My tests are self-validating because they have strict assertions.
  - My tests cover all happy, unhappy paths, and all possible errors or results.
  - I implemented dummy, mocks, setUp, and tearDown to avoid duplication and clean up objects.
  - If my function involves calling other functions, then Test Double techniques is used. 

