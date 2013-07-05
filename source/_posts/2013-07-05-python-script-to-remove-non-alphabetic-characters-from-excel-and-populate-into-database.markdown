---
layout: post
title: "Python script to remove Non-alphabetic characters from excel &amp; populate into Database"
date: 2013-07-05 21:12
comments: true
categories: 
---
{% codeblock %}
import xlrd
import MySQLdb
import re
# Open the workbook and define the worksheet
book= xlrd.open_workbook("Worksheet_name.xls")
sheet = book.sheet_by_name("Sheet_Name")

# Establish a MySQL connection
database = MySQLdb.connect (host="localhost", user = User_name"", passwd = "Password", db = "Database_name")

# Get the cursor, which is used to traverse the database, line by line
cursor = database.cursor()

# Create the INSERT INTO sql query


query = """INSERT INTO Table_name  VALUES (%s,%s)"""      

# Create a For loop to iterate through each row in the XLS file, 
for r in range(1, sheet.nrows):
	
	Column_name1=re.sub("\d+","",sheet.cell(r,0).value).strip(")")   #removes numeric charcters and special charcters ; "()" here
	Column_name1=Column_name1[:-1]
	Column_name2=re.sub("\d+","",sheet.cell(r,1).value).strip(")")
	Column_name2=Column_name2[:-1]
	
	# Assign values from each row
	values =(Column_name1,Column_name2)
	# Execute sql Query
	try:
		
		cursor.execute(query,values)
	except:
		pass



# Close the cursor
cursor.close()

# Commit the transaction
database.commit()

# Close the database connection
database.close()

# Print results
print ""
print "All Done! Bye, for now."
print ""


{% endcodeblock %}
