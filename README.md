# ShopSphere

ShopSphere is a Java web application built with Jakarta Servlets, JSP, JDBC,
MySQL, and Maven.

## Requirements

- JDK 17 or newer
- Apache Maven 3.8 or newer
- Apache Tomcat 11
- MySQL 8

## Run locally on Windows

1. Create the `shopsphere_app` database in MySQL:

   ```sql
   CREATE DATABASE shopsphere_app;
   ```

2. Import [`docs/database.sql`](docs/database.sql) into `shopsphere_app`. The
   dump drops and recreates its tables, so do not import it into a database
   whose existing data must be preserved.
3. Create a MySQL application user with `SELECT`, `INSERT`, `UPDATE`, and
   `DELETE` privileges on `shopsphere_app` and set `DB_URL`, `DB_USER`, and
   `DB_PASSWORD` in the environment used to start Tomcat. `DB_URL` defaults to
   `jdbc:mysql://localhost:3306/shopsphere_app`; set the user and password to
   the application account credentials.
4. Build the deployable WAR from the project root:

   ```powershell
   mvn clean package
   ```

5. Copy `target\webapp.war` into Tomcat 11's `webapps` directory and start
   Tomcat. Alternatively, start Tomcat from the same terminal in which the
   database environment variables are set:

   ```powershell
   & 'C:\path\to\apache-tomcat-11\bin\catalina.bat' run
   ```

6. Open <http://localhost:8080/webapp/>.

See [`docs/Setup-Guide.md`](docs/Setup-Guide.md) for additional setup notes.
