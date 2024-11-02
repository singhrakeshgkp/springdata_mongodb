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
- 
