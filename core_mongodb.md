- [Basic](#basic)
   - [Inserting Document](#inserting-document)
   - [Finding Document](#finding-document)


# Basic
- MongoDB is document oriented database.
- Collections & Documents
  - Collections is similar to table such as employee, student, customer. Collections stores documents such as student collection stores student documents, employee collections stores employee documents.
  - 

## Inserting Document
- we are going to use following employee json doc
```json
{
"name":"rakesh",
"address": "gkp",
"country":"India"
}
```
- Create database and switch to that db using ```use <db name> command```.
- Inserting single record ```insert db.employee.insertOne({name:"rakesh",address:"gkp",country:"India"})```
- Inserting multiple record ```insert db.employee.insertMany([{emp1data},{emp2data}])```
## Finding Document
- Finding all records. by default mongo shell return 20 record to iterate use ```it``` command to get next 20 record  ```db.employee.find()```
- Filter 
  - Filter by single employee property ```db.employee.find({name:"rakesh"})``` it will return all the docs where employee name is rakesh
  - Filter by multiple employee properties ```db.employee.find({name:"rakesh",country:"India"})```. it will return list of employees where name is rakesh and country is India.
  - Filter and return only given property of employee
    -  return list of employee (only name and country property) where employee country is India ```db.employee.find({country:"India"},{name:1,country:1})```  
    -  output all employee (only name and country properties) ```db.employee.find({},{name:1,country:1})
  
