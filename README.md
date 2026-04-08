to add the databse you will have to go on terminal and type this in what i wrote after the semi colon below
hameemkhan@Hameems-MBP local retail new new %: python3 database_app.py

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
