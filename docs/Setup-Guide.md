# ShopSphere Setup Guide

## Requirements

- JDK 17 or newer
- Apache Maven 3.8 or newer
- Apache Tomcat 11
- MySQL Server 8

## Database setup

1. Start MySQL and create the application database:

   ```sql
   CREATE DATABASE shopsphere_app;
   ```

2. Import `docs/database.sql` into `shopsphere_app`.
3. Configure the database connection with environment variables:
   - `DB_URL`: defaults to `jdbc:mysql://localhost:3306/shopsphere_app`
   - `DB_USER`: MySQL application account
   - `DB_PASSWORD`: application account password; configure this outside the source code
4. Grant the application account `SELECT`, `INSERT`, `UPDATE`, and `DELETE` on
   `shopsphere_app`. Import the schema using a database administrator account.

The SQL dump drops and recreates its tables. Review it before importing, and
never run it against a database whose existing data must be preserved.

## Build and deploy

From the project root, build the WAR:

```powershell
mvn clean package
```

Copy `target\webapp.war` to Tomcat 11's `webapps` directory and start Tomcat.
If using `catalina.bat run`, start it from a terminal where the database
environment variables are available.

Open <http://localhost:8080/webapp/>.

The products, account, cart, and order pages require a running MySQL server and
the imported schema. `MOCK_ONLINE` is a simulated payment option, not a real
payment gateway.
