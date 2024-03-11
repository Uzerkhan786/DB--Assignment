QUE-1 ->Explain the relationship between the "Product" and "Product_Category" entities from the above diagram.

Ans-1- In the schema provided, the relationship between the "Product" and "Product_Category" entities is a one-to-many relationship.

Specifically:

Each "Product" entity belongs to one "Product_Category" entity.
Each "Product_Category" entity can have multiple associated "Product" entities.
This relationship is established through the foreign key category_id in the "Product" table. This foreign key references the primary key of the "Product_Category" table. It means that each product record in the "Product" table has a corresponding category identified by the category_id. This association allows for the categorization of products where each product is assigned to a specific category.

In Sequelize, this relationship is defined using the belongsTo() association, indicating that each "Product" belongs to a single "Product_Category". This is represented in the code as:

code-
Product.belongsTo(ProductCategory, { foreignKey: 'category_id' });

QUE-2-> How could you ensure that each product in the "Product" table has a valid category assigned to it?

Ans2- To ensure that each product in the "Product" table has a valid category assigned to it, we can enforce referential integrity constraints at the database level. In Sequelize, we can achieve this by defining a foreign key constraint with the references option in the belongsTo() association.

Here's how we can modify the association between the "Product" and "Product_Category" entities to enforce this constraint:

Code:
Product.belongsTo(ProductCategory, {
foreignKey: 'category_id',
allowNull: false, // Ensures that category_id cannot be null
onDelete: 'CASCADE' // Specifies what action to take when the associated category is deleted
});

Answer3- Explanation of Code-

In this there is 4 types of schema we have made like product,product_category,product_inventory and discount,so we have made schema of all that and in this we give the associations like this -

-In product schema there is product_Category_id in which there is foreign key we will give this for product category ,
-In this there is inventory_id, this also works like a foreignkey key which is the main id of inventory schema,
-Here is discount_id,which also works as a foreign key for product and is coming from discount_Schema,

So in this way all the things work
