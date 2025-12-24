/* 1. Apply 10% price increase to all electronics products */
db.products.updateMany(
  { category: "electronics" },
  { $mul: { price: 1.10 } }
);

/* 2. Give 20% discount on furniture items */
db.products.updateMany(
  { category: "furniture" },
  { $mul: { price: 0.80 } }
);

/* 3. Increase salary of all employees by 5% (salary field stored in product document) */
db.products.updateMany(
  { salary: { $exists: true } },
  { $mul: { salary: 1.05 } }
);

/* 4. Apply GST of 18% on product prices */
db.products.updateMany(
  {},
  { $mul: { price: 1.18 } }
);

/* 5. Reduce price by 30% during a sale */
db.products.updateMany(
  {},
  { $mul: { price: 0.70 } }
);
