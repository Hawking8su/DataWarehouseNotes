# Chapter 1 Data Warehousing, Business Intelligence, and Dimensional Modeling Primer

First and foremost, the DW/BI system must consider the needs of the business.

Data is almost always used for two purposes: operational record keeping and analytical decision making. 

- Users of an operational system, almost always deal with one transaction record at a time.
- Users of a DW/BI system, almost never deal with one transaction record at a time. To further complicate matters, they typically demand that historical context to preserved to accurately evaluate the organization's performance overtime.

## Goals of DW/BI systems

- Must make info easily accessible (simple and fast)
  - The data's structures and labels should mimic the business user's though processes and vocabulary
- Must present information consistently
  - If two performance measure have the same name, they must mean the same thing.
- Must adapt to change
- Must present info in a timely way
- Must be a secure bastion that protects the information assets.
- Must serve as the authoritative and trustworthy foundation for improved decision making.
- The business community must accept the DW/BI system to deem it successful.

DW/BI manager responsibilities:

- Understand the business users
- Deliver high-quality, relevant, and accessible information and analytics to the business users.
- Sustain the DW/BI environment.

## Dimensional Modeling Introduction 

Dim Model addresses two requirements:

- Deliver data that's understandable to the business users.
- Deliver fast query performance.

A data model that starts simple has a chance of remaining simple at the end of the design.

>"Make everything as simple as possible, but not simpler"   --  Albert Einstein

Normalized 3NF structures are immensely useful in operational processing because an update or insert transaction touches the database in only one place. Normalized model, however, are too complicated for BI queries. 

A dimensional model contains the same information as a normalized model, but packages the data in a format that delivers user understandability, query performance, and resilience to change.

### Star Schemas  VS OLAP Cubes

Dim models implemented in relational database are referred to as star schemas

Dim models implemented in multidimensional database are referred to as OLAP cubes. 

### Fact Tables for Measurements

The fact table in a dimensional model stores the performance measurements resulting from an organization's business process events. You should strive to store the low-level measurement data resulting from a business process in a single dimensional model. 

One of the core tenets of dimensional modeling is that all the measurement rows in a fact table must be at the same grain.

The most useful facts are numeric and additive, such as dollar sales amount.

All fact table grains falls into one of the three categories: transaction, periodic snapshot, and accumulating snapshot.

The fact table generally has its own primary key composed of a subset of the foreign keys. This key is often called a composite key. Every table that has a composite key is a fact table. Fact tables express many-to-many relationships. All others are dimension tables.

### Dimension Tables for Descriptive Context

The dimension tables contain the textual context associated with a business process measurement event. They describe the "who, what, where, how, and why" associated with the event.

Dimension attributes serve as the primary source of query constraints, groupings, and report labels.

You should strive to minimize the use of codes in dimension tables by replacing them with more verbose textual attributes. 

In many ways, the DW is only as good as the dimensional attributes, the analytic power of the DW/BI environment is directly proportional to the quality and depth of the dimension attributes.

The normalization is called snowflaking. Instead of 3NF, dimensional tables typically are highly denormalized with flattened many-to-one relationship within a single dimension table. You should almost always trade off dimension table space for simplicity and accessibility. 

## Kimball's DW/BI Architecture 

### Operational Source Systems

The main priorities of the source systems are processing performance and availability. 

### Extract, Transformation, and Load System

### Presentation Area to Support BI

- The data be presented, stored, and accessed in dimensional schemas
- The area must contain detailed, atomic data. 
- The presentation data area should be structured around business process measurement events. 
- All the dimensional structures must be built using common, conformed dimensions.



## Alternative DW/BI Architectures

### Independent Data Mart Architecture

It's the path of least resistance for fast development at relatively low cost, at least in the short run. 

![image-20210509234722863](https://raw.githubusercontent.com/Hawking8su/Images/main/20210509234809.png)

### Hub-and-Spoke Corporate Information Factory Inmon Architecture

![image-20210509234740878](E:\04_Blog\DWToolkit-DimensionalModeling-Kimball\01-DW,BI,DimensionalModeling.assets\image-20210509234740878.png)

### Hybrid  Hub-and-Spoke  and Kimball Architecture

![image-20210509234752664](https://raw.githubusercontent.com/Hawking8su/Images/main/20210509234824.png)

## Dimensional Modeling Myths

### Myth1: Dimensional models are only for summary data

### Myth2: Dimensional models are departmental, not enterprise

### Myth3: Dimensional models are not scalable

### Myth4: Dimensional models are only for predictable usage.

Dimensional models should not be designed by focusing on predefined reports or analyses; the design should center on measurement processes. 

### Myth5: Dimensional models can't be integrated.

## More Reasons to Think Dimensionally

When specifying the project's scope, you must stand firm to focus on a single business process per project and not sign up to deploy a dashboard that covers a handful of them in a single iteration.

Data stewardship or governance programs should focus first on the major dimensions. 

## Agile Considerations

- Focus on delivering business value. This has been the Kimball mantra for decades. 
- Value collaboration between the development team and business stakeholders.
- Stress ongoing face-to-face communication, feedback, and prioritizaition with the business stakeholders.

