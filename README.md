# Restful API Testing Collection 🚀

This repository contains an automated API test suite for the **Restful API** service built using **Postman**. The collection covers full CRUD (Create, Read, Update, Delete) operations with test assertions for functionality, response status codes, and data validation.

---

## 🛠️ Tools & Technologies Used

* **API Client:** Postman
* **Protocol:** HTTP / RESTful API
* **Data Format:** JSON

---

## 📌 Covered API Endpoints

The collection includes test suites for the following requests:

* **GET** `/objects` - Fetch all objects list.
* **GET** `/objects/{id}` - Fetch single object details by ID.
* **POST** `/objects` - Add a new object.
* **PUT** `/objects/{id}` - Fully update an existing object.
* **PATCH** `/objects/{id}` - Partially update an existing object.
* **POST** `/objects` - Create another object/payload instance.
* **DELETE** `/objects/{id}` - Delete a specific object.

---

## 🧪 Test Coverage & Assertions

Automated JavaScript tests are written in Postman for each request to verify:
* ✅ **Status Codes:** Validating `200 OK`, `201 Created`, `204 No Content`, etc.
* ⏱️ **Response Time:** Ensuring requests complete within acceptable performance thresholds (< 2000ms).
* 📄 **JSON Schema:** Validating keys, values, and data types in the response body.

---

## 🚀 How to Run the Tests

1. **Clone or Download** this repository.
2. Open **Postman**.
3. Click on the **Import** button in Postman and select the `restful.postman_collection.json` file.
4. Run the collection using the **Postman Collection Runner** or via **Newman CLI**:

```bash
newman run restful.postman_collection.json
