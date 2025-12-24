

/* 1. A user deletes an old address */
db.products.updateOne(
  { _id: 1 },
  { $pull: { addresses: { city: "Pune" } } }
);

/* 2. A product review violates policy */
db.products.updateOne(
  { _id: 1 },
  { $pull: { reviews: { rating: 1 } } }
);

/* 3. A student drops a course */
db.products.updateOne(
  { _id: 2 },
  { $pull: { courses: "Maths" } }
);

/* 4. Remove all products with price < 1000 from cart array */
db.products.updateOne(
  { _id: 3 },
  { $pull: { cart: { price: { $lt: 1000 } } } }
);

/* 5. Delete all inactive tags from a product document */
db.products.updateOne(
  { _id: 4 },
  { $pull: { tags: "inactive" } }
);
