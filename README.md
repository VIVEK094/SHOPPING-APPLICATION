# 🛍️ Shop Management System (Tkinter + MySQL)

A simple but stylish **desktop Shop Management application** built with **Python Tkinter** for the UI and **MySQL** for data storage.

It lets you:
- ✅ **Add products** to the database
- ✅ **Delete products** by product name
- ✅ **View all products**
- ✅ **Create a new customer bill** and generate a bill using quantities entered by the user
- ✅ Store sales into a `sale` table

---

## ✨ Tech Stack
- **Python**
- **Tkinter** (GUI)
- **MySQL** (database)
- **mysql-connector-python** (Python MySQL driver)

---

## 📦 Requirements
### 1) Python packages
Install the MySQL connector:

```bash
pip install mysql-connector-python
```

> The app will exit with a clear error message if `mysql.connector` is missing.

### 2) MySQL Server
You must have MySQL running locally.

This project expects the following credentials (as hardcoded in the script):
- **MySQL user:** `root`
- **MySQL password:** `root`
- **Host:** `localhost`

---

## 🗄️ Database Setup (Auto + What It Creates)
When you run the app, it will:
1. Create a database named **`Shop`** (if it doesn’t exist)
2. Create a table **`products`**
3. Create a table **`sale`**

### Tables created
#### `products`
- `date` : `VARCHAR(10)`
- `prodName` : `VARCHAR(20)`
- `prodPrice` : `VARCHAR(50)`

#### `sale`
- `custName` : `VARCHAR(20)`
- `date` : `VARCHAR(10)`
- `prodName` : `VARCHAR(30)`
- `qty` : `INTEGER`
- `price` : `INTEGER`

> Note: Product price is inserted as a string into `products.prodPrice`, but the bill converts it to `int` when calculating totals.

---

## ▶️ How to Run
Run the main file:

```bash
python "shopManagement (1).py"
```

You’ll see a main window with 4 options:
- **Add a Product**
- **Delete a Product**
- **View Products**
- **New Customer**

---

## 🧠 How Each Feature Works

### 1) Add a Product
Click **Add a Product** and fill:
- Date
- Product Name
- Product Price

Then click **ADD**.

✅ On success, the product is inserted into `products` and you get a success message.

---

### 2) Delete a Product
Click **Delete a Product** and enter the **Product Name**.

Then click **DELETE**.

✅ The application deletes rows where product name matches **case-insensitively** using:
`LOWER(prodName) = 'entered_name_lower'`

---

### 3) View Products
Click **View Products** to display all products stored in `products`.

---

### 4) New Customer (Generate Bill)
Click **New Customer** and enter:
- Date
- Customer Name

Then the UI shows up to **3 products** (based on the first three rows returned from `products`).

For each displayed product, enter the quantity you want.

Click **Generate Bill**.

✅ For every quantity entered:
- The app calculates `quantity * product_price`
- Displays the line item on the bill window
- Inserts the sale into `sale`

Finally, it shows the **total bill**.

---

## 🧪 Important Notes / Assumptions
- The **bill UI currently supports up to 3 products** (it reads `res[0]`, `res[1]`, `res[2]`).
- Product price is expected to be numeric (convertible to `int`).
- Sales are appended; previous sales are not replaced.
- The app connects to MySQL using the credentials:
  - `root/root`

---

## 🔧 Troubleshooting
### `mysql.connector not found`
Install dependencies:
```bash
pip install mysql-connector-python
```

### MySQL connection errors
- Ensure MySQL is running
- Ensure user/password `root/root` are correct
- Ensure host is `localhost`

---

## 📌 Future Improvements (Optional)
- Add support for **more than 3 products** in billing
- Validate inputs (price numeric, quantity positive)
- Replace SQL string concatenation with parameterized queries
- Add search/filter in “View Products”

---

## 🧾 Author
Built for demonstration and learning purposes: **Tkinter UI + MySQL persistence**.

