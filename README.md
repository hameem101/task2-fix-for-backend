to add the databse you will have to go on terminal and type this in what i wrote after the semi colon below
hameemkhan@Hameems-MBP local retail new new %: python3 database_app.py (you can also run terminal)
to restart the database use: rm retail_system.db
then run the terminal again and the retail_system.DB will be there so it keeps clean

NOTE THIS MAY BE IRRELEVENT:to install pydantic open your terminal and run: pip install pydantic.
if you have used fastAPI using: pip install fastapi then that will also work.


When you run python3 database_app.py in the terminal, Python executes your file from top to bottom, and when it reaches sqlite3.connect("retail_system.db"), it checks if the database file exists—if it doesn’t, it automatically creates it; then your create_tables() function runs and creates the tables (categories, products, customers), and any sample data functions (like add_category, add_product, add_customer) insert data into those tables; once this process finishes, a new file called retail_system.db appears in your project folder, and in VS Code it shows up with a pink database icon, meaning your database has been successfully created and is ready to use.

The system works in layers where each part connects to the next: the **database (`retail_system.db`)** is at the bottom and stores all your data (customers, products, categories); **`database_app.py`** sits above it and contains functions that run queries to insert or retrieve that data; **`api_app.py` (FastAPI)** acts as the backend server that calls those database functions and exposes endpoints like `/products` or `/customers`; **`app.js`** in the frontend sends requests (using fetch) to those API endpoints to get or send data; and finally **`index.html`** is what the user sees in the browser, where the data returned from the backend is displayed on the page—so the full flow is database → backend logic → API → JavaScript → HTML.

once completed use fetch 
fetch() is a built-in JavaScript function that lets your web page communicate with a server over HTTP or HTTPS. You give it a URL (like a FastAPI endpoint) and optional options such as the method ("GET", "POST", etc.), headers (like "Content-Type": "application/json"), and a body for sending data. For example, fetch("http://127.0.0.1:8000/products") sends a GET request to FastAPI, which returns JSON; .then(response => response.json()) converts it to a JavaScript object, and .then(data => ...) lets you use it in your page. You can also send data, e.g., registering a customer: fetch("http://127.0.0.1:8000/customers", { method: "POST", headers: {"Content-Type": "application/json"}, body: JSON.stringify(customerData) }). fetch() is asynchronous, so it doesn’t block the page while waiting for the server, and you must use the backend API URL, not the HTML page URL. Essentially, your front-end sends a request, FastAPI processes it, and the response is delivered back to your page.

how to use and download fetch
install uvicorn on your current python terminal:python3 -m pip install uvicorn
verify installation:python3 -m uvicorn --version
if it doesnt work use: python3 -m uvicorn api_app:app --reload
once installed run the server using:python3 -m uvicorn api_app:app --reload

one that is finished running it will show something like this on the terminal; INFO: Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
use that URL on javascript fetch() which is the yellow circle one 
it will look something like this
fetch("http://127.0.0.1:8000/customers", { method: "POST", headers: {"Content-Type": "application/json"}, body: JSON.stringify(customerData) })
This sends the customer data to your FastAPI app and receives a JSON response, completing the setup.
this will be the finished outcome when finished properly 

IMPORTANT: forgot to install fastAPI so you must do this:python3 -m pip install fastapi
then run backend again: python3 -m uvicorn api_app:app --reload

IMPORTANT NOTE: the terminal is the same across your whole project and is not linked to the file you are currently viewing; you can run commands for any Python file (like database_app.py or api_app.py) from the same terminal, as long as you are in the correct project folder.

IMPORTANT NOTE if the pyton version does not work use BUT YOU MAY NOT NEED TO USE IT BECAUSE IT WILL WORK:
from typing import Optional
description: Optional[str] = None

IMPORTANT NOTE: for app.js(javascript) you do not need to add anything else to the terminal.

after installing uvicron it should pop up something like this:
hameemkhan@Hameems-MBP localretailprototypenew % python3 -m uvicorn api_app:app --reload
INFO:     Will watch for changes in these directories: ['/Users/hameemkhan/Desktop/localretailprototypenew']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [42671] using StatReload
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
ANOTHER VERSION STEP BY STEP SAME BUT CLEANER 
Step 1:
Open your terminal and make sure you are inside your project folder (you can use cd your_folder_name if needed). Install the required packages by running:
python3 -m pip install fastapi
python3 -m pip install uvicorn
python3 -m pip install pydantic
(use this format instead of pip install if pip does not work on your system).

Step 2:
Create the database by running:
python3 database_app.py
When you run this, Python executes the file from top to bottom. It connects to SQLite using sqlite3.connect("retail_system.db"), and if the database file does not exist, it creates it automatically. Then the create_tables() function creates the tables (categories, products, customers), and the sample data functions (add_category, add_product, add_customer) insert data. After this, a file called retail_system.db will appear in your project folder, showing your database is ready.

Step 3:
If you need to reset the database (start fresh), delete it using:
rm retail_system.db
then run:
python3 database_app.py
again to recreate a clean database with fresh data.

Step 4:
Start the backend server (FastAPI) by running:
python3 -m uvicorn api_app:app --reload
If it works correctly, you will see a message like:
Uvicorn running on http://127.0.0.1:8000
This means your backend API is running.

step 5:
Open your index.html file in a browser. This is your frontend (what the user sees). It is connected to your JavaScript file (app.js).

Step 6:
The frontend communicates with the backend using fetch(), which is a built-in JavaScript function (you do NOT need to install it). It sends HTTP requests to your FastAPI server.
For example, to get products:
fetch("http://127.0.0.1:8000/products")
This sends a GET request and receives JSON data.
To send data (e.g., register a customer):
fetch("http://127.0.0.1:8000/customers", {
  method: "POST",
  headers: {"Content-Type": "application/json"},
  body: JSON.stringify(customerData)
})
this sends data to the backend and it receives a responce

Step 7:
Understand how the whole system works together. The database (retail_system.db) stores all data. database_app.py interacts with the database using SQL queries. api_app.py (FastAPI) acts as the backend server and provides endpoints like /products and /customers. app.js sends requests to these endpoints using fetch() and receives responses. Finally, index.html displays the data to the user.
👉 Full flow:
HTML → JavaScript → FastAPI → database functions → SQLite database → back to JavaScript → displayed on the page

Step 8 (Important Notes):
The terminal is shared across your whole project and is not linked to a specific file
You can run any Python file from the same terminal as long as you are in the correct folder
If pip does not work, always use python3 -m pip
You do NOT need to install anything for app.js or fetch()
If your Python version has issues with str | None, you can use:
from typing import Optional
description: Optional[str] = None
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
add orders 
step 1:add order table (database_app.py)
add this inside create_tables():
cursor.execute("""
CREATE TABLE IF NOT EXISTS orders (
    id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    product_id INTEGER,
    quantity INTEGER,
    created_at TEXT
)
""")

step 2: add order function (database_app.py)
add this under your other functions:
def add_order(customer_id, product_id, quantity):
    connection = get_connection()
    cursor = connection.cursor()

    cursor.execute("""
        INSERT INTO orders (customer_id, product_id, quantity, created_at)
        VALUES (?, ?, ?, ?)
    """, (customer_id, product_id, quantity, datetime.now().isoformat()))

    connection.commit()
    connection.close()

step 3: add API endpoint (api_app.py)
class Order(BaseModel):
    customer_id: int
    product_id: int
    quantity: int

@app.post("/orders")
def create_order(order: Order):
    database_app.add_order(
        order.customer_id,
        order.product_id,
        order.quantity
    )
    return {"message": "Order created"}

step 4: add frontend button on HTML
add this anywhere in your html on order section
<h2>Create Order</h2>

<input type="number" id="customerId" placeholder="Customer ID">
<input type="number" id="productId" placeholder="Product ID">
<input type="number" id="quantity" placeholder="Quantity">

<button id="orderBtn">Place Order</button>

step 5: add javascript
const orderBtn = document.getElementById("orderBtn");

orderBtn.addEventListener("click", function () {

    const orderData = {
        customer_id: document.getElementById("customerId").value,
        product_id: document.getElementById("productId").value,
        quantity: document.getElementById("quantity").value
    };

    fetch("http://127.0.0.1:8000/orders", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify(orderData)
    })
    .then(res => res.json())
    .then(data => {
        alert("Order placed successfully!");
    })
    .catch(error => console.error(error));

});







