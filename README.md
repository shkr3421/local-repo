
use product_db

/* 1. A user logs in → increase login count by 1 */
db.products.updateOne(
  { _id: 1 },
  { $inc: { loginCount: 1 } }
);

/* 2. A product is sold once → decrease stock by 1 */
db.products.updateOne(
  { _id: 1 },
  { $inc: { stock: -1 } }
);

/* 3. Wallet balance increases by ₹500 after cashback */
db.products.updateOne(
  { _id: 1 },
  { $inc: { walletBalance: 500 } }
);

/* 4. Blog post gets a new like → increment likes */
db.products.updateOne(
  { _id: 1 },
  { $inc: { likes: 1 } }
);

/* 5. Product return happens → increase stock by 1 */
db.products.updateOne(
  { _id: 1 },
  { $inc: { stock: 1 } }
);
