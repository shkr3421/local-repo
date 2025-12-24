
/* 1. Update quantity of a specific product inside order's items array */
db.products.updateOne(
  { _id: 1, "orderItems.productId": 101 },
  { $set: { "orderItems.$.quantity": 3 } }
);

/* 2. Change phone number inside nested contact object */
db.products.updateOne(
  { _id: 1 },
  { $set: { "contact.phone": "9876543210" } }
);

/* 3. Increase salary of employees in a specific department (e.g., IT) */
db.products.updateMany(
  { "employees.department": "IT" },
  { $inc: { "employees.$.salary": 5000 } }
);

/* 4. Add a new skill to a specific employee inside employees array */
db.products.updateOne(
  { "employees.empId": 201 },
  { $push: { "employees.$.skills": "Node.js" } }
);

/* 5. Remove a specific item from nested cart array based on product ID */
db.products.updateOne(
  { _id: 2 },
  { $pull: { cart: { productId: 501 } } }
);
