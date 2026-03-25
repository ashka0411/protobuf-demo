# Protocol Buffers (Proto3) Serialization Demo

This project is a technical deep-dive into **Google Protocol Buffers (protobuf)** using **Spring Boot 4.0.3** and **Java 21**. The primary goal is to demonstrate the automated generation of high-performance Java classes from structured `.proto` definitions.

## 🛠 Tech Stack & Versions
* **Java:** 21 (LTS)
* **Spring Boot:** 4.0.3
* **gRPC:** 1.77.1
* **Protobuf-Java:** 4.33.4
* **Spring gRPC:** 1.0.2

---

## 📄 The Schema: `employee.proto`
The core of this demo is the `Employee` message, which demonstrates complex data types including collections (**repeated**) and key-value pairs (**maps**).

---

## ⚙️ How Code Generation Works
In this project, the Java classes are not written manually. They are "compiled" from the `.proto` file using the `protobuf-maven-plugin`.

### **1. The Generation Process**
When you run the Maven lifecycle, the plugin reads the schema and generates a highly optimized Java class that includes:
* **Builders:** For type-safe object creation.
* **Getters/Setters:** Following the Protobuf naming conventions.
* **Serialization/Deserialization:** Methods to convert the object to `byte[]` for network transmission.

### **2. Triggering the Build**
To generate the classes, run:
```bash
mvn clean compile
```
The generated source code will be located in:
`target/generated-sources/protobuf/java/`

---

## 🧪 What this Demo Proves
* **Schema Evolution:** How adding or removing fields in the `.proto` file automatically updates the Java API.
* **Type Safety:** Ensuring that `int32` in Proto maps correctly to `int` in Java, and `repeated` maps to a `List`.
* **Zero-Copy Serialization:** A look into how Protobuf is significantly faster and smaller than JSON for microservices.

---

## 📝 Learning Journey
This project was created to master the **Serialization Layer** of modern distributed systems. By decoupling the data contract from the application code, we achieve:
1.  **Language Interoperability:** The same `.proto` could be used to generate Python or C++ code.
2.  **Performance:** Binary format reduces CPU usage and network bandwidth.
3.  **Strict Typing:** Eliminating runtime errors associated with dynamic JSON parsing.
