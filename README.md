1. The exact line that creates the .db file
DB_NAME = "retail_system.db"

def get_connection():
    return sqlite3.connect(DB_NAME)
👉 THIS is the key:
sqlite3.connect(DB_NAME)
What happens here:
If retail_system.db does NOT exist → ✅ it gets created automatically
If it already exists → ✅ Python just connects to it
🏗️ 2. Where tables are created
def create_tables():
    connection = get_connection()
    cursor = connection.cursor()
👉 This line:
connection = get_connection()
→ creates the database file (if needed)
Then these create tables inside it:
CREATE TABLE IF NOT EXISTS categories
CREATE TABLE IF NOT EXISTS products
CREATE TABLE IF NOT EXISTS customers
▶️ 3. When does this actually run?
At the bottom:
if __name__ == "__main__":
    create_tables()
👉 This means:
When you run:
python database_app.py
It will:
Create retail_system.db (if not already there)
Create all tables
📦 4. Where data gets inserted
These lines:
add_product("Oranges", 1, 2.99, 30, "fruits")
add_customer("greeshma@gmail.com", "Greeshma", "Halesh", "Bangalore", "India")
What they do:
Insert rows into:
products
customers
🔁 Full flow of YOUR code
Run database_app.py
   ↓
sqlite3.connect("retail_system.db")  ← creates file
   ↓
create_tables()                      ← creates tables
   ↓
add_product(...)                     ← inserts data
   ↓
add_customer(...)                    ← inserts data
⚠️ Small issue in your code (important)
You wrote:
add_product("Oranges", 1, ...)
But:
category_id = 1
You never added a category
👉 This can break your foreign key relationship (or give empty joins later)
Fix:
Uncomment this:
add_category("groceries", "salads&veggies")
Run once first.
👀 What your DB now contains
After running, your database has:
🟣 categories
id	name	description
🟢 products
| id | name | category_id | price | stock |
🔵 customers
| id | email | first_name | last_name |
🔥 Final simple answer
👉 Your retail_system.db appears because of this line:
sqlite3.connect("retail_system.db")
👉 And it actually gets created when this runs:
create_tables()
👍 What to do next
Run:
python database_app.py
Open the DB with SQLite Viewer
Check:
customers
products
categories
