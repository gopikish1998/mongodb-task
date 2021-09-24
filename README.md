## mongodb-task

After initialising the mongod server, we open mongo shell and find the available dbs, we can select one from them or create another db.\
To select a db we type\
`use {name of db}`\

For the given task, we create a new db named 'product-data' and a collection named 'products' and insert the given data\
We execute this as\
`use product-data`\
`db.products.insertMany(data)`\

**1. Find all the information about each products**\
    `db.products.find()`\
**2. Find the product price which are between 400 to 800**\
    `db.products.find({ product_price: { $gte: 400, $lte: 800 } });`\
**3. Find the product price which are not between 400 to 600**\
    `db.products.find({ product_price: {$not:{$gte: 400, $lte: 600}}});`\
**4. List the four product which are grater than 500 in price**\
    `db.products.find({ product_price: { $gte: 500 } }).limit(4);`\    
**5. Find the product name and product material of each products**\
    `db.products.find({}, { product_name: 1, product_material: 1 });`\
**6. Find the product with a row id of 10**\
    `db.products.find({ id: "10" });`\
**7. Find only the product name and product material**\
    `db.products.findOne({}, { product_name: 1, product_material: 1 });`\
**8. Find all products which contain the value of soft in product material**\
    `db.products.find({ product_material: { $regex: /soft/, $options: "i" } });`\
**9. Find products which contain product color indigo  and product price 492.00**\
    `db.products.find({
  $and: [{ product_color: "indigo" }, { product_price: 492.0 }]
});`\
**10. Delete the products which product price value are same**\
    ``
