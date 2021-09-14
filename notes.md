# M320 Notes

## CHAPTER 0

### Intro

- Database schema
- Flexible data model
- All data has some kind of structure, and therefore a schema.
- If you know your usage pattern, acces data, critical queries, reand and writes operations, you can design a better performant DB
- Some approaches might be better to have everything in one document. But this might not be always be true
- Larger document, less performance. Find the right balance.

### QUIZ

Which of the following statements are true about data modeling using MongoDB?

- [ ] MongoDB should only be used for unstructured datasets.
- [X] MongoDB will help you iterate on the schema designs of your models throughout your application's lifecycle.
- [ ] MongoDB is schema-less so you should not worry about designing a schema for your models.

### MongoDB Data Hierarchy

- Data is stored as BSON data. BSON is Binary JSON
- JSON to visualize.
- Document is a collection of attributes for an entity.
- Document would be a row. Similar to a dictionary
- Instead of having information in several tables, collapsed in one dictionary.
- Data type in each field can be different
- Flexible schema DB

### QUIZ MongoDB Data Hierarchy

Which of the following statements are true about MongoDB documents?

- [X] MongoDB documents are stored as BSON documents.
- [ ] MongoDB documents within a collection must have the same fields.
- [X] MongoDB documents have a flexible schema.

### Constraints in Data Modeling

- Ram is super expensive > SSD > HDD
- Documents can't be larger than 16 mb
- Latency
- Data size, security
- Frequently accessed data. Wroking set.
- Keep the frequently used Documents in ram
- Keep indexes in Ram
- Prefer SSD on HDD
- Infrequently data could be stored in HDD

Your Hardware can limit the way you model your data.

### QUIZ Constraints Data modeling

Which of the following is not a usual constraint that would impact your data model for MongoDB?

- [ ] Network
- [ ] Disk Drives
- [ ] Ram
- [X] Operating System
- [ ] Security

### The data modeling Methodology

- Describe the workload
- Identify Relationships
- Apply patterns

- Scenarions, use of your knowladge to delimitate the best design.

### QUIZ The data modeling Methodology

Which of the following phases are included in our data modeling methodology for MongoDB?

- [X] Identifying the workload of the system.
- [X] Identifying the relationships between pieces of information.
- [X] Applying schema design patterns.

### Model for Simplicity or Performance

- Usually one or the other.
- Simplicity: Grouping together. Very agile. Few collections, richer documents.
- Performance: More atomic, spread out.

### QUIZ Model for Simplicity or Performance

Which of the following are use cases in which you should model your data for performance rather than simplicity?

- [X] The application is being developed by 100 engineers.
- [ ] There is not an applicable design pattern to the solution.
- [X] It is expected that the solution will be designed with only 10 shards.

### Identifying the Workloads

- Case: IOT. 100 millions weather sensors.
- Need: Collect the data. Analyze and make it available to 10 DS.
- Data can be collected every minute.
- Data need to be stored at least for 10 years.
- After identifying the needs, you can creat a table quantifying and quialificating the operations. Actor, CRUD operations, info needed, Operation Type.

### QUIZ Identifying the Workloads

Which of the following is not part of the first phase of the data modeling methodology?

- [ ] Listing the write operations.
- [ ] Quantifying each of the operations in terms of latency and frequency.
- [X] Identifying the relationships between the units of data.
- [ ] Listing the read operations.
- [ ] Identifying the durability of each write operation.

### CHAPTER 2

- Relational Database.
- Not tabular.
- Embedding and linking
- what are relationships in a Non relational Database.
- 1 to 1: in single identity.
- Types and cardinality.

Types and cardinalities

1-1: Same document
1-N: doesn't make sens to embed.
N-1:
N-N:

The usual cardinalities.
There are cases also of 1-Z
Also, the notation [min, median, max]

### QUIZ Relationship Types and Cardinality

Problem:

Why did we introduce the one-to-zillions relationship in our modeling notation?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [ ] To address the fact that a crow's foot has 5 fingers, not 3.
- [X] To graphically represent a relationship that has a higher order of magnitude than commonly seen in a 'one-to-many' relationship.
- [X] To highlight the fact that huge cardinalities may impact design choices.

### 1-N

- 1 object is associated with several from the other side, but from the other side, it is only associated with one. Example: Credit card.
- Solution: to embed one entity in the other, usually on the most queried side.
- Or, referencing, usually in the many side.
- Cascade deletes are not implemented in MongoDB.

-

### QUIZ One-to-Many Relationship

Problem:

Consider a one-to-many relationship observed between a county and the cities in that county.
Which of the following are valid ways to represent this one-to-many relationship with the document model in MongoDB?
Attempts Remaining:∞Unlimited Attempts
Check all answers that apply:

- [X] Have a collection for the counties and a collection for the cities with each city document having a field to reference the document of its county.
- [ ] Embed all the fields for a city as a subdocument in the corresponding county document.
- [X] Embed the entities for the cities as an array of sub-documents in the corresponding county document.

### N-N

- Many stores, many items.
- Be carefull to check both sides.
- In SQL, you need a jump table.
- Data migration cost.
- Embed,m in the main side.
- References.

### QUIZ MANY TO MANY

Consider a many-to-many relationship observed between movies and the actors starring in these movies, for a system that could provide detailed information about either a movie or an actor.

<https://university-courses.s3.amazonaws.com/M320/rst-images-prob_movies_actors.png>

Which of the following are true about modeling this many-to-many relationship with the document model in MongoDB?

Check all answers that apply:

- [X] Embedding actors in movies creates duplication of actor information.
- [X] Embedding actors in movies still requires a separate collection to store all actors.
- [ ] When using one collection for movies and one collection for actors, all movie documents must have an array of references to the actors in that movie, and all actor documents must have an array of references to the movies they appear in.

### Lab: Many-to-Many Relationship

Check all answers that apply:

- [ ] items.title and items.reviews.body
- [X] stores.address.street and items.description
- [X] items.sold_at and items.reviews.body
- [X] users.credit_cards.number and items.reviews.body
- [ ] users.shipping_address.street and items.reviews.body

### 1-1

- Usually in the same document. Embedding.
- Refrence. Same identifier in one side, or in the many side.
- References: create compllexity. Improvess performance on samller dik, samller amount of RAM neeeded.
  
### QUIZ 1 to 1

Problem:

Which of the following are valid ways to represent a one-to-one relationship with the document model in MongoDB?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] Embed the fields in the document.
- [X] Link to a single document in another collection.
- [X] Embed the fields as a sub-document in the document.

## Lab: 1-1 Relationship

The option with the phones subdocument in the employees collection, and emp_confidential contains subdocuments for address and compensation as well as an employee_id

### 1-Z

- Subcase of 1-N
- Only way is to refrence the document in the ons side of the relationship from the zillion side. (Include reference in Zillion)

### QUIZ One-to-Zillions Relationship

Which of the following statements are true about one-to-zillions relationships?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] It is a special case of the one-to-many relationship.
- [X] The relationship representations that embed documents are not recommended.
- [X] We must take extra care when writing queries that retrieve data on the zillions side

## CHAPTER 3

### Introduction to patterns

- Patterns are reusable approaches for solving models
- Computed patter to avoid repetitive compututaions
- Attribute pattern: structure similar fields
- Schema versioning patterh to avoid changes with no downtime.
  
JSON VALIDATOR TOOL

- Download the hangouts

```sh
chmod 555 validate_m320
```

Set in Security (MacOS) to allow running that file.

Code after validation: 5d124f9bd971a774b97b5fc7

### Hnadling duplications, staleness, integrity

- Patterns. You might need to accept / deal with duplicaiton, data staleness.
- Extra application logic to ensure refrential integrity.
- Duplication: result of embedding information for faster access. In some cases duplication is better than not doing!
- Example: Shipments. Better to embed the direction.
- Staleness: Pieces of data that might be not up to date.
- Some operations need to be confirmed before its realization: checkout, stocks, etc.
- Staleness: Data qualityand realiability
- Bactch updates can solve staleness.
- Change stream too
- Referential integrity
- No support for cascading deletes
- Should or could the information be duplicated? => Bulk updates
- What is the tolarated or acceptable sateleness. => Updates based on changestreams.
- Referential integrity? Resolve prevent with change streams or transactions.

### QUIZ Chapter 3: Patterns (Part 1)

Handling Referential Integrity
Problem:

Which of the following are valid concerns regarding duplication, staleness and referential integrity management in a MongoDB database and appropriate resolution techniques?
Attempts Remaining:∞Unlimited Attempts

Check all answers that apply:

- [X] Data integrity issues can be minimized by using multi-document transactions.
- [ ] Data duplication should not exist and can be avoided with multi-document transactions.
- [X] Data staleness issues can be minimized with frequent batch updates.

### ATTRIBUTE PATTERN

- Polimorphism
- Represent different objects with same structure.
- One of the most used pattern in MongoDB
- List of fields impredictable.
- Identify the fields that you want to transpose.
- then add a new key:

```js
const props = [
    {"k": someKeyName, "v": someValue},
    {"k": someKeyName, "v": someValue},
    {"k": someKeyName, "v": someValue},
    {"k": someKeyName, "v": someValue},
]

// then you can create a compound index on props.k:1 and props.v: 1
```

Problem:

- Lots of similar fields.
- want to search across many fields at once
- fields represent in only a small subset of documents.
- Break the field value intoa  sub document.
- Ideal for characteristic of a product.
- Easier to index
- Allow for non deterministic field names

### QUIZ Attribute Pattern

Problem:

Which one of the following scenarios is best suited for the application of the Attribute Pattern?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] The documents are large.
- [X] Some fields share a number of characteristics, and we want to search across those fields.
- [ ] The working set does not fit in memory.
- [ ] The documents need strict validation.
- [ ] The system is accessing the disk too frequently.

### LAB Chapter 3: Patterns (Part 1)

Lab: Apply the Attribute Pattern

Code: 02008affbe09bedd4f196f19

### Extended Reference Pattern

- Joins: application side with 2 queries.
- $lookup
- $graphLookup
- Avoid a join by embedding the joined table!
- A many to 1, is  a 1 to many looked from the other side.
- So we can embed the many into the 1
- Extended reference: embed only the neccesary fields
- Select the fields that doesn't change often.

- Problem: Too many repetitive joins
- Bring those fields to the main
- Use cases: catalog, mobile app, real time
- faster reads
- less joins
- May introduce lots of duplication if extended reference contains fields that mutate a lot

### QUIZ Extended Reference Pattern

Problem:

Which one of the following scenarios is the best candidate to use the Extended Reference Pattern to avoid doing additional reads through joins/lookups?
Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [ ] A product model needs to store references to images of the product that are kept in an external location outside the database.
- [ ] A product model needs to store a counter representing the number of times it was purchased. **Computed Pattern.**
- [ ] An app needs to retrieve a product and its ten most recent reviews. **(better for subset pattern)**
- [X] An app needs to retrieve a product and information about its supplier.
- [ ] An order model needs to store the product ID, the price sold, and the quantity ordered for each product in an order.

### SUBSET PATTERN

- Break up huge documents.
- Start with the basic fields and move the 1 to 1 and 1 to many to other collections.
- Problem: Working set is too big
- A large part is rarely used
- Solution: breaking it apart.
- Use cases: List of reviews, list of comments. List of actors.
- Smaller working set, faster.
- More round trips to the server to get the full data.
- A little more space used on disk

### QUIZ SUBSET PATTERN

Problem:

Which one of the following scenarios is the best candidate for use of the Subset Pattern?
Attempts Remaining:Correct Answer

Choose the best answer:

- [ ] The system is running out of RAM.
- [ ] The developers of the system have left and no one understands the application.
- [ ] The system is accessing the disk too frequently
- [ ] The documents are too big.
- [X] The working set does not fit in memory and it is difficult to scale the hardware

### LAB SUBSET PATTERN

Code: 5c9c02e1f752ec6b191c3c7f

### CHAPTER 4

### COMPUTED PATTERNS

- Used for Computed calculations. 3 main categories:
  - Mathematical operations (sum, average, median. Built in function in the server.)
  - Fan out operations
  - Roll up opreations

Example on mathematical operations: Every time we sell a ticket.

In this pattern, you would probably have another collection that you would like to keep it tracked by groups, for example on every write.

Fan out = Many task to represent 1 logical task. Or you fan out on reads, or in writes.

Fan out on writes: less common, preparing the data before reading it, when you have a lot of time to write it. Example: Storing everything that the user needs in his homepage in a social network.

Fan out on writes.

Roll up. Drill down
Merge data together.
Goruping data togetter will be a roll up.
Reports on monthly, daily, weekly, etc.

Computed pattern

- Apply when lot of CPU power is being used
- Reduced latency
- Avoid doing same computation.
- Decomputation and store in the appropiate document or collection.
- Faster reads, saving on CPU
- Difficult to identify. Avoid usage when not needed.

Basically, this pattern 'caches' data to avoid multiple calculations.

### QUIZ Computed Pattern

Problem:

Which one of the following scenarios is best suited for the application of the Computed Pattern?

Choose the best answer:

- [ ] We have too much information to store in a single document.
- [X] We need to calculate a value that is displayed 100 times a minute and is based on a field which updates once a minute.
- [ ] We need to calculate a value that is displayed once per minute and is based on a field which updates 100 times per minute.
- [ ] We need to group documents and sum on a field.
- [ ] We need to calculate a value that is displayed 100 times a minute and is based on a field which updates 100 times per minute.

### LAB

Validation code: 5c94f393f752ec6b191c3c7d

### BUCKET PATTERN

- It is about finding the granularity between 1 document per device and 1 document for all the info.
- Bucketing info per device per day.
- Array with the info.
- One document per device per day. Temps: {00: ..., 01:} //keys are hours
- Another example" Messages per channel per day. Messages as a single document: to granular. Messages per conversation: might exceed 16 mb
- Problem: avoiding too many documents, or too big.
- Problem: a 1 to N can't be embedded (fully)
- Can lead to poor query results if not designed correctly.
- Middle ground solution. You need to have a good knowledge of your workload.
- Data needs to be grouped
  
### QUIZ Bucket Pattern

Which one of the following requirements in our system is the best candidate to use the Bucket Pattern?

Choose the best answer:

- [ ] Our system ingests 10 million pieces of data per day from 1 million devices, with 20% coming from 10 devices.
- [ ] Our system must embed a one-to-many relationship in one of our models, however, some of the result documents would be too big.
- [X] Our system ingests thousands of log lines each day for each host it monitors.
- [ ] Our system performs sums and averages over all elements of certain arrays.
- [ ] Our system handles 1 million IOT devices

### LAB Pattern

- [X] Option A
- [X] Option B
- [ ] Option C

### SCHEMA VERSIONING PATTERN

- Alter table nightmares.
- Based on the polyphormic aspect of documents.
- The app can read a field named schema_version and perform conditional handling.
- Migrations. Batch process can handle it.
- Avoid downtime with schema ugrades.
- Updating all documents migth take time, and might not be desired to do so having in count the amount.
- Less future technical debt.
- Might need 2 indexes for same field during migration (-)

### LAB Schema Versioning

- Scenarios A and B

### Tree patterns

- Hierarchical information.
- Company organization charts
- Categories products from an e shop
- Relationship with ancestors
- Books in a bookstore
- Reference in parent
- Reference in child
- materialized path: .Swag.office
- MongoMart solution: Ancestor array + parent reference
- parent: "Fashion"
- Ancestors: ["Swag", "Fashion"]

### QUIZ tree patterns

Which of the following scenarios would be ideal to use the Tree Pattern?

Check all answers that apply:

- [ ] Contact lists of users
- [X] Company organization charts
- [X] Product categories

### LAB TREE PATTERN

- Parent refence

### Polymporphic pattern

- Group elements together that might be queried together.
- Can be applied to described products.

### QUIZ Polymorphic Pattern

Problem:

Which one of the following scenarios is best suited for the use of the Polymorphic Pattern?

Choose the best answer:

- [X] The organization acquired different companies over the years, serving the same markets with the same customers and there is a requirement to merge all systems into one.
- [ ] There is a requirement to keep many versions of a document, and these versions may have different fields for each version.
- [ ] The application has a base class with some derived classes.
- [ ] There are billions of documents.
- [ ] There is a requirement to store addresses for my customers.

### LAB Polyphormic

Code: 5caab67a9c0aa5e40786f802

### OTHER PATTERNS

- Approximation pattern. When data is expensive to compute, with little value on exactity. Page counters, metric statistics. Less writes, less documents. Not exactly.
- Outliers. Identify them as exceptions and handle them differently. Social networks, popularity.

### QUIZ Other Patterns

Problem:

A pharmaceutical company needs to implement a design to model the relationships between the company and its partners, customers, and suppliers. A team came up with a design that works perfectly, meeting all performance requirements. However, when loading the real data in the system, they realized that one customer, the U.S. government had too many contacts to be stored into the designated array for this information.

Instead of redesigning the whole system to make this customer fit well into the new data model, which pattern can you use?Attempts Remaining:∞Unlimited Attempts

Choose the best answer:

- [X] The Outlier Pattern.
- [ ] The Attribute Pattern.
- [ ] The Schema Versioning Pattern.
- [ ] The Subset Pattern.
- [ ] The Pharmaceutical Pattern

### SUMMARY
