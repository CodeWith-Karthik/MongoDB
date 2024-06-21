# MongoDB Complete Course

##### Youtube - [https://www.youtube.com/@codewithkarthik](https://www.youtube.com/@codewithkarthik)

![https://www.youtube.com/@codewithkarthik](https://yt3.ggpht.com/twg8jbKidn4ovJaChPm2X5de9fRGlwt5xvltlqi7KltzzfMsHyMBjF8Q6iDP7KVR_mF8kWQs=s88-c-k-c0x00ffffff-no-rj)

# How to Configure MongoDB

### Step 1

##### Install MongoDB Database

Download MongoDB - [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)

### Step 2

##### Install MongoDB Shell

Download MongoDB Shell - [https://www.mongodb.com/try/download/shell](https://www.mongodb.com/try/download/shell)

### Step 3

Configure Enviroment Variables As Per Tutorial Video - [https://youtu.be/0zwYbudzaJc](https://youtu.be/0zwYbudzaJc)

---

# No-SQL Commands

#### Connecting to MongoDB Server

```bash
Step 1: Open command prompt(cmd) in your system
Step 2: Type 'mongosh' then hit enter key
```

---

#### Show database

###### The following command is used to show avaliable database list.

```bash
show dbs
```

---

#### Command to connect database

###### The following command is used to connect with database even if database is not exists it will create new database.

```bash
#Syntax
use [database name]
```

```bash
#Example
use maxishop
```

---

#### Creating Collection & Document

```bash
#Syntax
db.collectionName.insertOne({document})
```

```bash
#Example
db.products.insertOne({name:'Iphone 15',price:80000})

```

---

#### To get all the data from the collection

```bash
#Syntax
db.collectionName.find()
```

```bash
#Example
db.products.find()

#For Older version
db.products.find().pretty()
```

---

#### Creating Document with different schema or structure

```bash
#Example
db.products.insertOne({name:'Mac Book Pro',price:120000,brand:'Apple'})
```

```bash
db.products.insertOne({name:'Samsung Galaxy s24 Ultra',price:120000,brand:'Samsung'})
```

```bash
db.products.insertOne({name:'Bravia 43 inch 4k',price:120000,brand:'Samsung',productType:'TV'})
```

#### Embedded Document

##### Instead Document in Collections

```bash
db.products.insertOne({name:'Lenovo Legion',price:120000,brand:'Lenovo',productType:'Laptop',specification:{ram:'16 GB',processor:'i7 13th Gen',storageType:'SSD',storageSize:'1 TB'}})
```

```bash
#for easy understanding
db.products
  .insertOne(
    {
      name:'Lenovo Legion',
      price:120000,
      brand:'Lenovo',
      productType:'Laptop'
      specification:{
        ram:'16 GB',
        processor: 'i7 13th Gen',
        storageType:'SSD',
        storageSize: '1 TB'
      }
    })
```

you can also provide your own id as well like the following example.

###### note: Id should be unique, no duplicate key

```bash
db.products.insertOne({_id:'AX1000001',name:'MSI Katna 15',price:98000,brand:'MSI',productType:'Laptop',specification:{ram:'16 GB',processor:'i7 12th Gen',storageType:'SSD',storageSize:'512 GB'}})
```

```bash
#for easy understanding
db.products
  .insertOne(
    {
      _id:'AX1000001'
      name:'MSI Katna 15',
      price:98000,
      brand:'MSI',
      productType:'Laptop'
      specification:{
        ram:'16 GB',
        processor: 'i7 12th Gen',
        storageType:'SSD',
        storageSize: '512 GB'
      }
    })
```

---

#### Datatypes

```bash
use temp
```

```bash
db.orders.insertOne({quantity:50,totalAmount:1234567890123456,discount:0.10,status:'warehouse',isActive:true,details:{address:'Chennai,Tamil Nadu,India',pincode:600044},phoneNo: [123456789,987654321],orderDate:new Date(),createdAt:new Timestamp()})
```

```bash
db.orders.find()
```

```bash
db.orders.drop()
```

```bash
db.orders.insertOne({quantity:NumberInt(50),totalAmount:NumberLong('1234567890123456'),discount:0.10,status:'warehouse',isActive:true,details:{address:'Chennai,Tamil Nadu,India',pincode:NumberInt(600044)},phoneNo: [NumberLong('123456789'),NumberLong('987654321')],orderDate:new Date(),createdAt:new Timestamp()})
```

```bash
db.orders.find()
```

---

#### CRUD Operation

1. Create

   - insertOne(data,options)
   - insertMany(data,options)

2. Read

   - find(filter,options)
   - findOne(filter,options) #first matching document

3. Update

   - updateOne(filter,data,options)
   - updateMany(filter,data,options)
   - replaceOne(filter,data,options)

4. Delete
   - deleteOne(filter,options)
   - deleteMany(filter,options)

---

## Create Document In Collection

#### Inserting Single Record

```bash
db.products.insertOne({name:'Nothing Phone 2a',price:56000,brand:'Nothing',productType:'Mobile'})
```

```bash
db.products.insertOne({_id:'AX1000002',name:'MSI Katna 15 Pro',price:130000,brand:'MSI',productType:'Laptop',specification:{ram:'16 GB',processor:'i7 13th Gen',storageType:'SSD',storageSize:'1 TB'}})
```

```bash
#for easy understanding
db.products
  .insertOne(
    {
      _id:'AX1000002'
      name:'MSI Katna 15 Pro',
      price:130000,
      brand:'MSI',
      productType:'Laptop'
      specification:{
        ram:"16 GB",
        processor: 'i7 13th Gen',
        storageType:'SSD',
        storageSize: '1 TB'
      }
    })
```

#### Inserting Many Records

```bash
db.products.insertMany([{name:'Iphone 14',price:75000,brand:'Apple'},{name:'Samsung Galaxy A50',price:54000,brand:'Samsung'}])
```

---

## Read document from collection

```bash
db.products.find()
```

##### Filter

```bash
db.products.find({brand:'Apple'})
```

```bash
db.products.findOne({brand:'Apple'})
```

---

## Update document in collection

#### Updating Single Record

```bash
db.products.updateOne({name:'Mac Book Pro'},{$set:{productType:'Laptop'}})
```

```bash
db.products.updateOne({name:'Samsung Galaxy s24 Ultra'},{$set:{price:93000}})
```

```bash
db.products.updateOne({name:'Bravia 43 inch 4k'},{$set:{price:45000}})
```

```bash
db.products.updateOne({name:'Iphone 15'},{$set:{brand:'Apple',productType:'Mobile'}})
```

#### Updating Many Records

```bash
db.products.updateMany({_id:{$in:[ObjectId('66695c4aa52b865509cdcdf8'),ObjectId('66695c8ba52b865509cdcdfd')]}},{$set:{productType:"Mobile"}})
```

#### Replacing The Document

```bash
 db.products.replaceOne({_id:ObjectId('66695c8ba52b865509cdcdfc')},{name:"Iphone 14 Pro Max",price:115000,brand:'Apple',productType:'Mobile'})
```

---

## Delete document from collection

#### Deleting Single Record

```bash
# the following command will delete the 1st document with matched filter
db.products.deleteOne({brand:'Apple'})
```

```bash
db.products.deleteOne({brand:'Samsung'})
```

```bash
db.products.deleteOne({productType:'Laptop'})
```

```bash
# the following command will delete document based on Id
db.products.deleteOne({_id:'AX1000002'})
```

#### Deleting Many Record

```bash
# the following command will delete document many at same time
db.products.deleteMany({productType:'Laptop'})
```

```bash
db.products.deleteMany({})
```

#### Deleting Collection

```bash
db.products.drop()
```

#### Deleting Database

```bash
db.dropDatabase()
```

---

## Convert Json to Json minifier

Link - [https://codebeautify.org/jsonminifier](https://codebeautify.org/jsonminifier)

#### Prepare Data

###### Products

```
db.products.insertMany([{"name":"Iphone 15","price":80000,"brand":"Apple","productType":"Mobile"},{"name":"Iphone 14 Pro Max","price":115000,"brand":"Apple","productType":"Mobile"},{"name":"Samsung Galaxy A50","price":54000,"brand":"Samsung","productType":"Mobile"},{"name":"Nothing Phone 2a","price":56000,"brand":"Nothing","productType":"Mobile"},{"name":"Samsung Galaxy s24 Ultra","price":93000,"brand":"Samsung","productType":"Mobile"},{"name":"Bravia 43 inch 4k","price":45000,"brand":"Samsung","productType":"TV"},{"name":"Mac Book Pro","price":120000,"brand":"Apple","productType":"Laptop","specification":{"ram":"8 GB","processor":"M1","storageType":"SSD","storageSize":"512 GB"}},{"name":"Lenovo Legion","price":120000,"brand":"Lenovo","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 13th Gen","storageType":"SSD","storageSize":"1 TB"}},{"name":"MSI Katna 15","price":98000,"brand":"MSI","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 12th Gen","storageType":"SSD","storageSize":"512 GB"}},{"name":"MSI Katna 15 Pro","price":130000,"brand":"MSI","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 13th Gen","storageType":"SSD","storageSize":"1 TB"}}])
```

###### Customers

```
 db.customers.insertMany([{"name":"Amit Sharma","age":29,"gender":"Male"},{"name":"Priya Singh","age":30,"gender":"Female"},{"name":"Ravi Verma","age":35,"gender":"Male"},{"name":"Sandeep Kumar","age":28,"gender":"Male"},{"name":"Anita Joshi","age":30,"gender":"Female"},{"name":"Anjali Patel","age":27,"gender":"Female"},{"name":"Dr.Rajesh Mehta","age":47,"gender":"Male"},{"name":"Seema Gupta","age":33,"gender":"Female"},{"name":"Aarti Chawla","age":29,"gender":"Female"},{"name":"Rohit Desai","age":41,"gender":"Male"},{"name":"Karandeep Alun","age":48,"gender":"Male"},{"name":"Neha Singh","age":39,"gender":"Female"},{"name":"Arjun Reddy","age":22,"gender":"Male"},{"name":"Vikram Sharma","age":44,"gender":"Male"},{"name":"Aman Khan","age":41,"gender":"Male"},{"name":"Meera Iyer","age":"35","gender":"Female"},{"name":"Nidhi Kapoor","age":27,"gender":"Female"},{"name":"Arjun Gupta","age":35,"gender":"Male"},{"name":"Kiran Naik","age":53,"gender":"Male"},{"name":"Bharat Rao","age":68,"gender":"Male"},{"name":"Ramesh Patel","age":38,"gender":"Male"}])
```

---

#### Cursor Object

```bash
#find will not give all records
db.customers.find()
#it to show remaining records
```

To see all the data use following commands

```bash
db.customers.find().toArray()
```

```bash
db.customers.find().forEach((customersData)=> {printjson(customersData)})
```

---

#### Projection

```bash
db.customers.find({},{name:1})
```

```bash
db.products.find({},{name:1,price:1})
```

To ignore id

```bash
db.products.find({},{_id:0,name:1,price:1})
```

```bash
db.products.find({},{_id:0,name:1,price:1,brand:1})
```

---

#### Array

```bash
db.customers.updateOne({name:'Arjun Reddy'},{$set:{contactNo:[5987452368,8536547859]}})
```

```bash
db.customers.updateOne({name:'Seema Gupta'},{$set:{hobbies:['cooking','sports','singing']}})
```

```bash
db.customers.updateMany({name:{$in:['Neha Singh','Vikram Sharma','Arjun Gupta']}},{$set:{hobbies:['travel','sports']}})
```

```bash
db.customers.updateMany({name:{$in:['Meera Iyer','Nidhi Kapoor','Bharat Rao']}},{$set:{hobbies:['cooking','sports']}})
```

```bash
db.products.updateMany({},{$set:{categories:['electronics']}})
```

---

#### Delete and Prepare dataset

```
db.products.deleteMany({})
```

```
db.products.insertMany([{"name":"Iphone 15","price":80000,"brand":"Apple","productType":"Mobile","categories":["electronics"]},{"name":"Iphone 14 Pro Max","price":115000,"brand":"Apple","productType":"Mobile","categories":["electronics"]},{"name":"Samsung Galaxy A50","price":54000,"brand":"Samsung","productType":"Mobile","categories":["electronics"]},{"name":"Nothing Phone 2a","price":56000,"brand":"Nothing","productType":"Mobile","categories":["electronics"]},{"name":"Samsung Galaxy s24 Ultra","price":93000,"brand":"Samsung","productType":"Mobile","categories":["electronics"]},{"name":"Bravia 43 inch 4k","price":45000,"brand":"Samsung","productType":"TV","categories":["electronics"]},{"name":"Mac Book Pro","price":120000,"brand":"Apple","productType":"Laptop","specification":{"ram":"8 GB","processor":"M1","storageType":"SSD","storageSize":"512 GB"},"categories":["electronics"]},{"name":"Lenovo Legion","price":120000,"brand":"Lenovo","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 13th Gen","storageType":"SSD","storageSize":"1 TB"},"categories":["electronics"]},{"name":"MSI Katna 15","price":98000,"brand":"MSI","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 12th Gen","storageType":"SSD","storageSize":"512 GB"},"categories":["electronics"]},{"name":"MSI Katna 15 Pro","price":130000,"brand":"MSI","productType":"Laptop","specification":{"ram":"16 GB","processor":"i7 13th Gen","storageType":"SSD","storageSize":"1 TB"},"categories":["electronics"]},{"_id":"666982f9132be8d964cdce53","name":"Samsung RT28T3022S8","price":25000,"brand":"Samsung","productType":"Refrigerator","specification":{"capacity":"253L","energyRating":"3 Star"},"categories":["kitchen_appliances"]},{"_id":"666982f9132be8d964cdce54","name":"LG MC2846BG","price":15000,"brand":"LG","productType":"Microwave Oven","specification":{"type":"Convection","capacity":"28L"},"categories":["kitchen_appliances"]},{"_id":"666982f9132be8d964cdce55","name":"Whirlpool IF278","price":22000,"brand":"Whirlpool","productType":"Refrigerator","specification":{"capacity":"265L","energyRating":"4 Star"},"categories":["kitchen_appliances"]},{"_id":"666982f9132be8d964cdce56","name":"IFB 30BRC2","price":20000,"brand":"IFB","productType":"Microwave Oven","specification":{"type":"Convection","capacity":"30L"},"categories":["kitchen_appliances"]},{"_id":"666982f9132be8d964cdce57","name":"Samsung WW60R20GLMA","price":28000,"brand":"Samsung","productType":"Washing Machine","specification":{"capacity":"6 kg","type":"Front Load"},"categories":["laundry_appliances"]},{"_id":"666982f9132be8d964cdce58","name":"LG T7281NDDLG","price":18000,"brand":"LG","productType":"Washing Machine","specification":{"capacity":"6.2 kg","type":"Top Load"},"categories":["laundry_appliances"]},{"_id":"666982f9132be8d964cdce59","name":"Philips HD6975/00","price":7000,"brand":"Philips","productType":"Oven Toaster Grill","specification":{"capacity":"25L","powerConsumption":"1500W"},"categories":["kitchen_appliances"]},{"_id":"666982f9132be8d964cdce5a","name":"Dyson V11 Absolute Pro","price":52000,"brand":"Dyson","productType":"Vacuum Cleaner","specification":{"type":"Cord-free","runTime":"60 minutes"},"categories":["home_cleaning"]},{"_id":"666982f9132be8d964cdce5b","name":"Eureka Forbes Aquaguard Marvel","price":15000,"brand":"Eureka Forbes","productType":"Water Purifier","specification":{"type":"RO+UV","storageCapacity":"8L"},"categories":["water_appliances"]},{"_id":"666982f9132be8d964cdce5c","name":"Kent Grand Plus","price":19000,"brand":"Kent","productType":"Water Purifier","specification":{"type":"RO+UV+UF","storageCapacity":"9L"},"categories":["water_appliances"]}])
```

---

#### Accessing Embedded Document Data

###### Filter by hobbies in customers

```bash
db.customers.find({hobbies:'sports'})
```

```bash
 db.customers.find({hobbies:'cooking'})
```

###### Finding embedded data in customers

```bash
db.customers.findOne({age:22}).contactNo
```

```bash
db.customers.findOne({name:'Nidhi Kapoor'}).hobbies
```

###### Filter by catgory in products

```
db.products.find({categories:'electronics'});
```

```
 db.products.find({categories:'kitchen_appliances'});
```

###### Fliter by embedded data in products

```
db.products.find({"specification.storageSize":'512 GB'})
```

```
db.products.find({"specification.storageSize":'1 TB'})
```

```
db.products.find({"specification.ram":'8 GB'})
```

```
db.products.find({'specification.energyRating':'4 Star'});
```

---

### Database Methods

##### Status of database

```bash
db.stats()
```

##### Get current database name

```bash
db.getName()
```

##### Get collection list from current database

```bash
db.getCollectionNames()
```

##### Get collection list with more information from current database

```bash
db.getCollectionInfos()
```

### Collection Methods

##### Find no of documents in collection

```bash
db.products.countDocuments()
```

##### Find distinct values from collection

```bash
db.products.distinct('categories')
```

---

## Document Validation

```bash
use schoolDb
```

```bash
db.createCollection('staff',{
  validator:{
    $jsonSchema:{
      bsonType:'object',
      required:['name','age','email'],
      properties:{
        name:{
          bsonType:'string',
          description:'must be string and required field'
        },
        age:{
          bsonType:'int',
          description:'must be integer and required field'
        },
        email:{
          bsonType:'string',
          description:'must be string and required field'
        }
      }
    }
  }
})
```

```bash
db.createCollection('staffs',{validator:{$jsonSchema:{bsonType:'object',required:['name','age','email'],properties:{name:{bsonType:'string',description:'must be string and required field'},age:{bsonType:'int',description:'must be integer and required field'},email:{bsonType:'string',description:'must be string and required field'}}}}})
```

```bash
db.staffs.insertOne({name:'john',age:25,email:'john@gmail.com'})
```

```bash
db.runCommand({
  collMod:'staffs',
  validator:{
    $jsonSchema:{
      bsonType:'object',
      required:['name','email'],
      properties:{
        name:{
          bsonType:'string',
          description:'must be string and required field'
        },
        email:{
          bsonType:'string',
          description:'must be string and required field'
        }
      }
    }
  }
});
```

```bash
db.runCommand({collMod:'staffs',validator:{$jsonSchema:{bsonType:'object',required:['name','email'],properties:{name:{bsonType:'string',description:'must be string and required field'},email:{bsonType:'string',description:'must be string and required field'}}}}});
```

```bash
db.staffs.insertOne({name:'alex',email:'alex@gmail.com'})
```

```bash
db.staffs.find()
```

---

## Operators

```bash
use maxishop
```

### Comparison Operators

##### Equals

```bash
db.products.find({price:{$eq:80000}})
```

##### Greater Than

```bash
db.products.find({price:{$gt:80000}})
```

```bash
db.products.findOne({price:{$gt:80000}})
```

##### Greater Than or Equal

```bash
db.products.find({price:{$gte:80000}})
```

##### Less Than

```bash
db.products.find({price:{$lt:80000}})
```

```bash
db.products.findOne({price:{$lt:80000}})
```

##### Less Than or Equal

```bash
db.products.find({price:{$lte:80000}})
```

##### Not Equal

```bash
db.products.find({price:{$ne:80000}})
```

##### Matches any of the values in an array

```bash
 db.customers.find({hobbies:{$in:['cooking']}})
```

```bash
db.customers.find({hobbies:{$in:['cooking','travel']}})
```

##### Not Matched any of the values in an array

```bash
 db.customers.find({hobbies:{$nin:['cooking']}})
```

```bash
db.customers.find({hobbies:{$nin:['cooking','travel']}})
```

### Logical Operators

##### AND

```bash
db.products.find({$and:[{price:{$gt:80000}},{brand:'Apple'}]})
```

##### OR

```bash
db.products.find({$or:[{price:{$lt:10000}},{brand:'Apple'}]})
```

##### NOR

```bash
db.products.find({$nor:[{price:{$lt:10000}},{productType:'Laptop'},{productType:'Mobile'}]})
```

```bash
db.products.find({$nor:[{price:{$lt:40000}},{productType:'Laptop'},{productType:'Mobile'}]})
```

##### NOT

```bash
db.products.find({price:{$not:{$gt:10000}}})
```

### Element Operators

##### Exists

```bash
db.customers.find({hobbies:{$exists:false}})
```

```bash
db.customers.find({hobbies:{$exists:true}})
```

```bash
db.customers.find({$and:[{hobbies:{$exists:true}},{age:{$gt:40}}]})
```

```bash
db.customers.find({$and:[{hobbies:{$exists:false}},{age:{$gt:40}}]})
```

##### Type

```bash
db.customers.find({age:{$type:'string'}})
db.customers.find({age:{$type:'number'}})
```

#### Expr - expression

```bash
use personalData
```

```bash
db.personalData.insertMany([{category:'food',budget:400,spent:450},{category:'clothes',budget:100,spent:50},{category:'travel',budget:200,spent:650}])
```

```bash
 db.personalData.find({$expr:{$gt:['$spent','$budget']}})
```

### Array Operators

```bash
use maxishop
```

##### Array Size

```bash
db.customers.find({hobbies:{$size:3}})
```

```bash
db.customers.find({hobbies:{$size:2}})
```

##### All

```bash
db.customers.find({hobbies:["sports","travel"]})
```

```bash
db.customers.find({hobbies:["travel","sports"]})
```

```bash
db.customers.find({hobbies:{$all:["sports","travel"]}})
```

---

### Sort, Skip & Limit

##### Sorting the document

```bash
db.products.find().sort('price')
```

```bash
db.products.find().sort({'price':-1})
```

```bash
db.products.find({productType:'Mobile'}).sort('price')
```

```bash
db.products.find({productType:'Mobile'}).sort({'price':-1})
```

##### Skip the document

```bash
db.products.find({productType:'Mobile'}).sort('price').skip(2)
```

##### Limit the document

```bash
db.products.find({productType:'Mobile'}).sort('price').limit(2)
```

```bash
db.products.find({productType:'Mobile'}).sort({'price':-1}).skip(1).limit(2)
```

---

### Example from Learning

```bash
 db.products.find({},{_id:0,name:1,'specification.ram':1}).sort({'price':-1}).limit(4)
```

```bash
 db.products.find({specification:{$exists:true}},{_id:0,name:1,'specification.ram':1}).sort({'price':-1}).limit(4)
```

---

### CRUD Options

##### Create option

```bash
use temp
```

```bash
db.users.insertOne({_id:'UA001',name:'John wick'})
```

```bash
db.users.insertMany([{_id:'UA001',name:'Lisa'},{_id:'UA002',name:'Rose'}])
```

ordered - partial insert for valid documents

```bash
db.users.insertMany([{_id:'UA001',name:'Lisa'},{_id:'UA002',name:'Rose'}],{ordered:false})
```

##### Read Option

```bash
use maxishop
```

Projection

```bash
db.products.find({},{name:1})
```

```bash
db.products.find({},{_id:0,name:1})
```

```bash
 db.products.find({productType:'Laptop'},{name:1})
```

```bash
 db.products.find({productType:'Laptop'},{name:1,specification:1})
```

```bash
 db.products.find({productType:'Laptop'},{name:1,'specification.ram':1})
```

```bash
 db.products.find({productType:'Laptop'},{name:1,'specification.ram':1,'specification.processor':1})
```

Slice

```bash
db.customers.find({hobbies:{$exists:true}},{hobbies:{$slice:1}})
```

Slice Skip and Take

```bash
db.customers.find({hobbies:{$exists:true}},{hobbies:{$slice:[1,2]}})
```

##### Update option

Before upsert, if there is not match then changes will not happen

```bash
db.customers.updateOne({name:'Swetha'},{$set:{name:'Swetha Sri',age:25,gender:'Female',hobbies:['travel','dancing']}})
```

upsert

```bash
db.customers.updateOne({name:'Swetha'},{$set:{name:'Swetha Sri',age:25,gender:'Female',hobbies:['travel','dancing']}},{upsert:true})
```

##### Delete option

```bash
db.customers.find().sort('age').limit(3)
```

```bash
db.customers.findOneAndDelete({},{sort:{age:1}})
```

---

### Relations

##### One to One Relation

```bash
use OrgDB
```

```bash
db.employees.insertOne({_id:'EMP001',name:'John Doe',postion:'Software Enginner'})
```

```bash
db.profiles.insertOne({employee_id:'EMP001',age:26,address:'123 Main St',phone:'555-555-5555'})
```

Aggregate

```bash
db.employees.aggregate([{$lookup:{from:'profiles',localField:'_id',foreignField:'employee_id',as:"personalDetails"}}])
```

##### One to Many Relation

Creating Companies

```bash
db.companies.insertMany([{_id:'CMP001',name:'Nule Soft',isMNC:true},{_id:'CMP002',name:'JexiTech',isMNC:false},{_id:'CMP003',name:'DSA Softwares',isMNC:true}])
```

Updateing old employee to assgin company

```bash
db.employees.updateOne({_id:'EMP001'},{$set:{company_id:'CMP001'}})
```

Adding More Employee with different companies

```bash
db.employees.insertMany([{_id:'EMP002',name:'Alice Smith',postion:'Product Manager',company_id:'CMP001'},{_id:'EMP003',name:'Bob Brown',postion:'UI/UX Designer',company_id:'CMP002'},{_id:'EMP004',name:'Charlie Davis',postion:'Backend Developer',company_id:'CMP001'},{_id:'EMP005',name:'Diana Evans',postion:'Frontend  Developer',company_id:'CMP001'}])
```

```bash
db.profiles.insertMany([{employee_id:'EMP002',age:36,address:'123 Main St',phone:'444-555-5555'},{employee_id:'EMP003',age:28,address:'123 Main St',phone:'222-333-5555'},{employee_id:'EMP004',age:37,address:'567 Main St',phone:'111-333-4444'},{employee_id:'EMP005',age:32,address:'987 Main St',phone:'111-222-8888'}])
```

Aggregate

```bash
db.companies.aggregate([{$lookup:{from:'employees',localField:'_id',foreignField:'company_id',as:'Employees'}}])
```

##### Many to Many Relation

Creating projects

```bash
db.projects.insertMany([{_id:'P001',name:'Project Alpha'},{_id:'P002',name:'Project Beta'}])
```

```bash
db.employee_projects.insertMany([{employee_id:'EMP001',project_id:'P001'},{employee_id:'EMP005',project_id:'P001'},{employee_id:'EMP003',project_id:'P001'},{employee_id:'EMP002',project_id:'P002'},{employee_id:'EMP004',project_id:'P002'},{employee_id:'EMP003',project_id:'P002'}])
```

Aggregate

```bash
db.projects.aggregate([{$lookup:{from:'employee_projects',localField:'_id',foreignField:'project_id',as:'employee_projects'}}])
```

```bash
 db.projects.aggregate([{$lookup:{from:'employee_projects',localField:'_id',foreignField:'project_id',as:'employee_projects'}},{$unwind:"$employee_projects"},{$lookup:{from:'employees',localField:'employee_projects.employee_id',foreignField:'_id',as:'employees'}},{$unwind:'$employees'},{$group:{_id:'$_id',name:{$first:'$name'},employees:{$push:'$employees'}}},{$project:{_id:0,name:1,employees:1}}])
```

```bash
db.projects.aggregate([{$lookup:{from:'employee_projects',localField:'_id',foreignField:'project_id',as:'employee_projects'}},{$unwind:"$employee_projects"},{$lookup:{from:'employees',localField:'employee_projects.employee_id',foreignField:'_id',as:'employees'}},{$unwind:'$employees'},{$group:{_id:'$_id',name:{$first:'$name'},employees:{$push:{employee_id:'$employees._id',name:'$employees.name'}}}},{$project:{_id:1,name:1,employees:1}}])
```

---

# Copyrights to codewithkarthik
