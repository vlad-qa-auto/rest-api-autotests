Automation tests of primitive RESTfull API service.

_Do you have any comments or questions? Welcome!_

---
**Technologies:**

Java 11 as latest LTS Java.

Building - **[Gradle 5.6](https://github.com/gradle/gradle)**.

Test running and assertions - **[TestNG 7.0](https://github.com/cbeust/testng)**.

Running and validation of HTTP requests - **[REST Assured 4.0](https://github.com/rest-assured/rest-assured)**.

SQL queries - **[JOOQ](https://github.com/jOOQ/jOOQ)**.

JSON objects - **[org.json](https://github.com/stleary/JSON-java)**.

SQLite database [venv/main.db](venv/main.db) connected by native JDBC.

Project was written in Intellij IDEA. 
Satellite IDEA-files are already in Git project.
For running tests, please use created Run/Debug configuration **testng.xml** or **testng.yaml** in IDEA.
For running directly in Gradle use configuration **gradle test** or command **`gradlew test`** in command line. 
Html report will be generated in /build/reports/tests/test/index.html

Tests are separated to three classes according to webservice functions/endpoints.
In case of no response from webservice, suite fails without running any test.
Test **testSaveDbError** fails for demonstration how failed tests looks.

All parameters for tests are managed by [testng.xml](testng.xml) file.

---
**RESTfull API service** [venv/superservice.py](venv/superservice.py) was writen on Python 
using *bottle* and *sqlalchemy* libraries.
Endpoints:
- **/ping/** - just returns code 200 on GET.
- **/authorize/** - returns authorization token (valid for 1 min) for user/password = supertest/superpassword.
- **/api/save_data/** - saves data to *venv/main.db* for authorized user (50% succeeded).

For runing *superservice*, please install Python and import libraries **bottle** and **sqlalchemy**. 
There is already created Run/Debug configuration **superservice** in IDEA for starting webservice.
In command line: start with parameter **run**. If need to create database, start with parameter **migrate**. 
Also can use already created executors **superservice run** and **superservice migrate**