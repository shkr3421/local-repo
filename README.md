use product_db

db.products.insertMany([
  { _id: 1, name: "Laptop", category: "electronics", price: 60000, stock: 10, likes: 50 },
  { _id: 2, name: "Mobile", category: "electronics", price: 20000, stock: 25, likes: 120 },
  { _id: 3, name: "Chair", category: "furniture", price: 3000, stock: 40, likes: 30 },
  { _id: 4, name: "Table", category: "furniture", price: 7000, stock: 15, likes: 45 },
  { _id: 5, name: "Headphones", category: "electronics", price: 2500, stock: 60, likes: 80 }
])

/* ---------- $set ---------- */

// Rename product
db.products.updateOne(
  { _id: 2 },
  { $set: { name: "Smartphone" } }
)

// Add discount field
db.products.updateOne(
  { _id: 1 },
  { $set: { discount: 10 } }
)

// Update category
db.products.updateOne(
  { _id: 5 },
  { $set: { category: "accessories" } }
)

/* ---------- $inc ---------- */

// Product sold
db.products.updateOne(
  { _id: 1 },
  { $inc: { stock: -1 } }
)

// New like
db.products.updateOne(
  { _id: 1 },
  { $inc: { likes: 1 } }
)

// Product returned
db.products.updateOne(
  { _id: 3 },
  { $inc: { stock: 1 } }
)

/* ---------- $mul ---------- */

// 10% price increase on electronics
db.products.updateMany(
  { category: "electronics" },
  { $mul: { price: 1.10 } }
)

// 20% discount on furniture
db.products.updateMany(
  { category: "furniture" },
  { $mul: { price: 0.80 } }
)

/* ---------- $push ---------- */

// Add review
db.products.updateOne(
  { _id: 1 },
  { $push: { reviews: { user: "Shashank", rating: 5 } } }
)

// Add tag
db.products.updateOne(
  { _id: 2 },
  { $push: { tags: "sale" } }
)

/* ---------- $pull ---------- */

// Remove low rating review
db.products.updateOne(
  { _id: 1 },
  { $pull: { reviews: { rating: 1 } } }
)

// Remove tag
db.products.updateOne(
  { _id: 2 },
  { $pull: { tags: "sale" } }
)

/* ---------- Aggregation ---------- */

db.products.aggregate([
  {
    $group: {
      _id: "$category",
      totalStock: { $sum: "$stock" },
      avgPrice: { $avg: "$price" }
    }
  }
])
