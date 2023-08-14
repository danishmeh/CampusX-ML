How to Fix the XAMPP MySQL Error "MySQL Shutdown Unexpectedly" 💡

I recently installed XAMPP on my system and was able to start Apache, but MySQL would not start and I received the following error:

8:07:32 AM [mysql] 💥 Error: MySQL shutdown unexpectedly.
8:07:32 AM [mysql] ⚠️ This may be due to a blocked port, missing dependencies, 
8:07:32 AM [mysql] 🔐 improper privileges, a crash, or a shutdown by another method.
8:07:32 AM [mysql] 🔎 Press the Logs button to view error logs and check
8:07:32 AM [mysql] 🔍 the Windows Event Viewer for more clues
8:07:32 AM [mysql] 💡 If you need more help, copy and post this
8:07:32 AM [mysql] 📃 entire log window on the forums>
I found that the solution to this error was to run services.msc and find the MYSQL80 service. This service was already running, so I stopped it and changed its startup type to Manual. After doing this, I was able to start MySQL without any problems.

Here are the steps on how to fix this error:

Open services.msc.
Find the MYSQL80 service.
🛑 Stop the service.
🔀 Change the startup type to Manual.
🚀 Start the service.
How to create a new database in XAMPP:

Open a web browser and go to localhost/phpmyadmin/.
Click on the 🆕 New button.
Enter a name for your new database.
Click on the 🗳️ Create button.
How to read a SQL dataset in VS Code:

Install the mysql.connector library.
Import the mysql.connector library.
🔐 Create a connection to the MySQL database.
Use the pd.read_sql_query() function to read the SQL dataset.
Here are some examples:

Python
import pandas as pd

# Read the JSON file into a Pandas DataFrame
df = pd.read_json("test.json")

# Get some information about the DataFrame
df.info()

# Specify the dtype of the `id` column
df = pd.read_json("test.json", dtype={'id': float})

# Read the JSON file in chunks
dfs = pd.read_json("train.json", lines=True, chunksize=50)

# Read the JSON data from an API
df = pd.read_json("https://api.exchangerate-api.com/v4/latest/INR")

# Import the MySQL connector library
import mysql.connector

# Create a connection to the MySQL database
conn = mysql.connector.connect(host='localhost', user='root', password='', database='world')

# Read the `CITY` table from the MySQL database
df = pd.read_sql_query("SELECT * FROM CITY", conn)

# Read the `CITY` table from the MySQL database where the `CountryCode` is USA
df = pd.read_sql_query("SELECT * FROM CITY WHERE CountryCode like 'USA'", conn)


following are example 
pd.read_json("test.json").info()
df = pd.read_json("test.json",dtype={'id':float})
dfs = pd.read_json("train.json",lines=True,chunksize=50)
pd.read_json("https://api.exchangerate-api.com/v4/latest/INR")
import mysql.connector
conn = mysql.connector.connect(host='localhost',user='root',password='',database='world')
pd.read_sql_query("SELECT * FROM CITY",conn)
pd.read_sql_query("SELECT * FROM CITY WHERE CountryCode like 'USA'",conn)