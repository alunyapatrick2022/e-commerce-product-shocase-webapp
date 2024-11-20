# e-commerce-product-shocase-webapp

Here’s the complete set of commands for generating a Maven project, from setting up the project structure to building and deploying the WAR file.

---

### **1. Generating the Maven Project**

To generate a Maven project, you can use **Maven's command line tool**. Follow these steps:

#### **Step 1: Install Maven**
If you haven’t installed **Maven** yet, follow the installation steps from the [official Maven documentation](https://maven.apache.org/install.html).

#### **Step 2: Generate a New Maven Project**

Open your terminal or command prompt and use the following command to generate a new Maven web project:

```bash
mvn archetype:generate -DgroupId=com.ecommerce -DartifactId=ecommerce-web-app -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

Explanation of parameters:
- `-DgroupId=com.ecommerce`: The group ID of the project (can be your domain or project name).
- `-DartifactId=ecommerce-web-app`: The artifact ID, which will be the name of the project folder and the base name for the generated WAR file.
- `-DarchetypeArtifactId=maven-archetype-webapp`: Specifies that the project is a web application.
- `-DinteractiveMode=false`: Disables interactive mode to skip questions during setup.

This will generate a basic web application project with a `pom.xml` file and the default `src` folder structure.

---

### **2. Adding Dependencies to `pom.xml`**

After generating the project, open the `pom.xml` file and modify it to include the necessary dependencies.

Here’s an example of the dependencies for **Servlet**, **JSP**, **SQLite**, and other libraries:

```xml
<dependencies>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>4.0.1</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>org.apache.tomcat</groupId>
        <artifactId>tomcat-jdbc</artifactId>
        <version>9.0.45</version>
    </dependency>
    <dependency>
        <groupId>org.sqlite</groupId>
        <artifactId>sqlite-jdbc</artifactId>
        <version>3.34.0</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>5.3.10</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-web</artifactId>
        <version>5.3.10</version>
    </dependency>
</dependencies>
```

After modifying the `pom.xml` file, save it.

---

### **3. Compiling and Building the Project**

Once your project is set up, compile and package it into a WAR file using the following Maven command:

```bash
mvn clean package
```

This command will:
- Clean up any previously compiled code (`clean`).
- Compile the project, resolve dependencies, and create a WAR file (`package`).

After the build completes, the WAR file will be located in the `target` folder. The WAR file will be named like `ecommerce-web-app-1.0-SNAPSHOT.war`.

---

### **4. Deploying to Apache Tomcat Server**

#### **Step 1: Copy WAR to Tomcat Webapps Folder**

Once the WAR file is generated, copy it to the **webapps** folder of your Apache Tomcat server. Assuming that your Tomcat is installed in `/opt/tomcat/`, use the following command:

```bash
cp target/ecommerce-web-app-1.0-SNAPSHOT.war /opt/tomcat/webapps/
```

#### **Step 2: Start Tomcat Server**

To start the Tomcat server, run:

```bash
/opt/tomcat/bin/startup.sh
```

For **Windows**, use:

```bash
/opt/tomcat/bin/startup.bat
```

#### **Step 3: Access the Application**

After Tomcat starts, your application will be accessible from your browser at:

```
http://localhost:8080/ecommerce-web-app-1.0-SNAPSHOT/
```

If everything is set up correctly, you should see the homepage of your e-commerce application.

---

### **5. Summary of Commands**

Here’s a summary of the key commands used in the project:

1. **Generate Maven project**:

```bash
mvn archetype:generate -DgroupId=com.ecommerce -DartifactId=ecommerce-web-app -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

2. **Add necessary dependencies** to `pom.xml`.

3. **Build the project** (compile and package):

```bash
mvn clean package
```

4. **Copy the WAR file** to the Tomcat webapps folder:

```bash
cp target/ecommerce-web-app-1.0-SNAPSHOT.war /opt/tomcat/webapps/
```

5. **Start Tomcat server**:

```bash
/opt/tomcat/bin/startup.sh
```

6. **Access the app** in your browser:

```
http://localhost:8080/ecommerce-web-app-1.0-SNAPSHOT/
```

---

### **6. Conclusion**

This guide helps you generate, set up, and deploy an e-commerce Maven project with **Java Servlets**, **JSP**, **SQLite**, and other required technologies. After following these steps, you should have a fully functional e-commerce web application deployed on a **Tomcat server**. Let me know if you need further assistance!