# CRUD Quiz

Use the solution to this afternoon's Property Tracker lab to answer the following questions. Please write your answers under each question, push the file to GitHub, and submit in the usual way.

## MVP Questions

In our Property Tracker application:

Q1. Where are we instantiating instances of the `Property` class?
This is instantiated from the console.rb.

Q2. Where are we defining the SQL that enables us to save the ruby `Property` object into the database?
This is defined in the property.sql file.

Q3. In `console.rb`, which lines modify the database?
Properties.delete_all()
listing1.save
listing2.save
listing3.save

Q4. Why do we not define the id of a `Property` object at the point we instantiate it (‘new it up’)?
As this needs to be created by the database and then written to the Ruby object.

Q5. Where and how do we assign the id (that is generated by the database) to the ruby `Property` object?
Inside Properties.rb and using this code:
        @id = db.exec_prepared("save", values)[0]["id"].to_i


Q6. Why do we put a guard (an `if` clause) on the `@id` attribute in the constructor?
As a safety incase there is no @id set yet.

Q7. Why are some of the CRUD actions represented by instance methods, and others by class methods?
This depends on what access you want to give, for example, if you are changing all the records, this would be a class method. If you are only changing 1 record, this should be an instance methed.

Q8. What type of data structure is returned by calls to `db.exec_prepared()`? In the `save` method, how do we access the id from the returned data structure?
This is an PG array type object. We access the [0] index to get the ID as it is always the first element.

Q9. Why do we use prepared statements when performing database operations?
To counter sql injection attacks and sanitize the input.

## Extension Questions

Look at the `find_by_id` and `find_by_address` methods in the `Property` class.

Q10. What do they take in as their arguments?
Find by ID takes in the ID you are wanting to filter. It takes an integer.
Find by address takes in a string.

Q11. What are their return values?
They return an array with the hash of one record (row).
