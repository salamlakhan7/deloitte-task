# Deloitte Forage – Data Transformation Task

## 📌 Overview

This project is part of the **Deloitte Australia Virtual Experience Program (Forage)**.

The goal was to simulate a real-world backend/data engineering problem where different systems produce telemetry data in **inconsistent formats**, and we need to **standardize them into a unified schema**.

---

## 🧠 Problem Statement

Daikibo Industrials uses IIoT (Industrial Internet of Things) devices across its factories.

However:

* Half of the devices send telemetry data in **Format 1**
* The other half send data in **Format 2**

These differences make it difficult to process and analyze data consistently.

👉 The task was to:

> Convert both formats into a **single unified format**

---

## 📂 Input Formats

### 🔹 Format 1

* Flat structure
* Location stored as a **single string**
* Uses:

  * `operationStatus`
  * `temp`

### 🔹 Format 2

* Nested structure
* Location split into multiple fields
* Uses:

  * `device.id`, `device.type`
  * ISO timestamp format (`YYYY-MM-DDTHH:MM:SSZ`)

---

## 🎯 Target Output Format

Both inputs must be converted into:

* Standard field names:

  * `deviceID`
  * `deviceType`
* Structured location object:

  * `country`, `city`, `area`, `factory`, `section`
* Unified data object:

  * `status`, `temperature`
* Timestamp in:

  * **milliseconds since epoch**

---

## ⚙️ Solution Approach

Two transformation functions were implemented:

* `convertFromFormat1(jsonObject)`
* `convertFromFormat2(jsonObject)`

### Key transformations:

* Split location string into structured fields
* Map inconsistent keys to standardized names
* Convert ISO timestamps to epoch milliseconds
* Normalize nested and flat JSON structures

---

## 🧪 Testing

The project includes unit tests using Python’s `unittest` module.

To run tests:

```bash
python main.py
```

### ✅ Expected Output:

```
----------------------------------------------------------------------
Ran 3 tests

OK
```

---

## 🐞 Challenges Faced

* **Encoding Issue (UTF-8 vs cp1252)**
  Resolved by explicitly setting:

  ```python
  encoding="utf-8"
  ```

* **Timestamp Conversion**
  Converted ISO format to milliseconds using:

  ```python
  int(datetime.timestamp() * 1000)
  ```

---

## 🚀 Key Learnings

* Data normalization across multiple formats
* Handling nested JSON structures
* Working with timestamps and time formats
* Debugging real-world encoding issues
* Writing and validating code with unit tests

---

## 📁 Project Structure

```
deloitte-task/
│
├── data-1.json
├── data-2.json
├── data-result.json
└── main.py
```

---

## 👨‍💻 Author

**Abdul Salam**

* GitHub: https://github.com/salamlakhan7
* LinkedIn: https://www.linkedin.com/in/abdul-salam-501b2025b/

---

## ⭐ Final Result

✔ Successfully transformed both input formats into the required unified structure
✔ All unit tests passed
✔ Ready for submission and real-world application
