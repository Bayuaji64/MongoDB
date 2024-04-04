# MongoDB

 mongosh
show dbs
 use shop
 db.products.insertOne({name:"A Book",price: 12.99})
 db.products.find()
 db.products.find().pretty()
 cls

 # CRUD mongo


db.dropDatabase()
db.flightData.deleteOne({departureAirport:"TXL"})
db.flightData.deleteMany({departureAirport:"TXL"})
db.flightData.updateOne({distance: 12000},{$set: {marker:"delete"}})
db.flightData.updateMany({},{$set:{marker:"toDelete"}})
db.flightData.deleteMany({marker:"toDelete"})
db.flightData.insertMany([
...   {
...     "departureAirport": "MUC",
...     "arrivalAirport": "SFO",
...     "aircraft": "Airbus A380",
...     "distance": 12000,
...     "intercontinental": true
...   },
...   {
...     "departureAirport": "LHR",
...     "arrivalAirport": "TXL",
...     "aircraft": "Airbus A320",
...     "distance": 950,
...     "intercontinental": false
...   }
... ])


db.flightData.find({intercontinental:true})
db.flightData.find({distance:{$gt: 10000}})

db.flightData.findOne({distance:{$gt: 900}})



db.flightData.updateOne({_id: ObjectId("660eb5fe4bc6e7a2682c9f35")},{$set:{delayed: true}})
db.flightData.update({_id: ObjectId("660eb5fe4bc6e7a2682c9f35")},{$set:{delayed: false}})

db.passengers.find().toArray()
db.passengers.find().forEach((passengerData)=>{printjson(passengerData)})
db.passengers.find({},{name: 1})
db.passengers.find({},{name: 1, _id:0})


db.flightData.updateMany({},{$set:{status:{description:"on-time",lastUpdate:"1 hour ago"}}})
db.flightData.updateMany({},{$set:{status:{description:"on-time",lastUpdate:"1 hour ago",details:{responsible:"Bayuaji Arinanda"}}}})

db.passengers.updateOne({name:"Albert Twostone"},{$set:{hobbies:["sports","cooking"]}})
db.passengers.findOne({name:"Albert Twostone"}).hobbies
db.passengers.find({hobbies:"sports"})
db.flightData.find({"status.description":"on-time"})
db.flightData.find({"status.details.responsible":"Bayuaji Arinanda"})
