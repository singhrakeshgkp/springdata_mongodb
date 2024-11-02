- [Mongo DB](#mongo-db)
   - [Basic](#basic)
      - [Inserting Document](#inserting-document)
      - [Finding Document](#finding-document)
      - [Apply Sorting](#apply-sorting)
      - [Limiting Data](#limiting-data)
   - [Operators](#Operators)
   - [Nested Documet](#nested-document) 

# Mongo DB
- Simple Document
```json
{
"name":"rakesh",
"address": "gkp",
"salary": 40000,
"country":"India"
}
``` 
- Nested document
```json
{
"name":"rakesh",
"sal":40000,
"kycDocs":["passport","voterid","aadhaar card"]
"address":{"city":"noida", "isPermanentAddress":false,"country":"India"}
}
```
  
## Basic
- MongoDB is document oriented database.
- Collections & Documents
  - Collections is similar to table such as employee, student, customer. Collections stores documents such as student collection stores student documents, employee collections stores employee documents.
  - 

### Inserting Document
- Create database and switch to that db using ```use <db name> command```.
- Inserting single record ```insert db.employee.insertOne({name:"rakesh",address:"gkp",country:"India"})```
- Inserting multiple record ```insert db.employee.insertMany([{emp1data},{emp2data}])```
### Finding Document
- Finding single record. **query** ```db.employee.findOne(_id:"")```
- Finding all records. by default mongo shell return 20 record to iterate use ```it``` command to get next 20 record **query** ```db.employee.find()```
- Filter 
  - Filter by single employee property **query** ```db.employee.find({name:"rakesh"})``` it will return all the docs where employee name is rakesh
  - Filter by multiple employee properties **query** ```db.employee.find({name:"rakesh",country:"India"})```. it will return list of employees where name is rakesh and country is India.
  - Filter and return only given property of employee
    -  return list of employee (only name and country property) where employee country is India **query** ```db.employee.find({country:"India"},{name:1,country:1})```  
    -  output all employee (only name and country properties) **query** ```db.employee.find({},{name:1,country:1})
   
### Apply Sorting
- Sorting in ascending order, for sorting use employee name property. **query** ```db.employee.find().sort({name:1})
- Sorting in descending order, for sorting use employee name property. **query** ```db.employee.find().sort({name:-1})
### Limiting Data
- return number of available documents. **query** ```db.employee.find().count()```
- return given number of documents. **query** ```db.employee.find().limit(5)```

## Operators
- Filter using logical ```or``` operator. **query** ```db.employee.find({$or: [{country:"India"},{country:"USA"}]})```
- Output all employee, where salary is greater than 20k. **query** ```db.employee.find({salary: {$gt: 20000}})```
- ```$in``` and ```$nin``` IN and Not In Operators
  - Output all employee, where employee country is India, USA or Russia. **query** ```db.employee.find({country: {$in: ["India","USA","Russia"]}})```
  - Output all employee, where employee country is not India, USA or Russia. **query** ```db.employee.find({country: {$nin: ["India","USA","Russia"]}})```

## Nested Document
### Apply Filter on nested json doc
- **Query on array**
  - Get list of employee, having passport in the kycDocs array. **query** ```db.employee.find({kycDocs:"password"})```
  - Get list of employee, having only passport in the kycDocs array. **query** ```db.employee.find({kycDocs:["password"]})```
  - Get list of employee, having only passport and voterid in the kycDocs array. **query** ```db.employee.find({kycDocs:["password","voterid"]})```
  - Get list of employee, having  passport and voterid in the kycDocs array. **query** ```db.employee.find({kycDocs:{$all: ["password","voterid"]}})```. apart from voter id and password it could have other things such as aadhaar as its not exact match its kind of contains query.
- Get list of employee where employee.address.city = Noida. **query** ```db.employee.find({"address.city":"Noida"})```

