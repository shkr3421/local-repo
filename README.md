

/* 1. A user adds a new address to their profile */
db.products.updateOne(
  { _id: 1 },
  { $push: { addresses: { city: "Delhi", pincode: 110001 } } }
);

/* 2. A product receives a new review */
db.products.updateOne(
  { _id: 1 },
  { $push: { reviews: { user: "Shashank", rating: 5, comment: "Good product" } } }
);

/* 3. A student enrolls in a new course */
db.products.updateOne(
  { _id: 2 },
  { $push: { courses: "MongoDB" } }
);

/* 4. An order has multiple products, add one more product */
db.products.updateOne(
  { _id: 3 },
  { $push: { orderItems: { productName: "Mouse", price: 500 } } }
);

/* 5. A chat app stores messages in an array, push new message */
db.products.updateOne(
  { _id: 4 },
  { $push: { messages: "Hello, this is a new message" } }
);
