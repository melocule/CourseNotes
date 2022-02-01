Nested Model
Top-down: Problem-based 
Bottom-up: Technique-based

Threats to validity: Wrong problem or data abstraction. No initially correct answer, depends on user experience

# Data
**Semantics**: real-world meaning of data
**Data type**: what kind of thing it is, structurally or value-wise, mainly:
- **Attribute** is a value
![[Pasted image 20220128174357.png]]
- **Item** is a discrete entity (vector)
- **Link** is relation between items
- **Grid** samples continuous data between cells
- **Position** is spacial
**Metadata**: data about the data, ambiguous line betweeen this and data

**Table** = rows + columns
**Flat table**: row is item, column is attribute, cell is value, primary key (e.g. index)
**Multidimensional table** has compound primary key

**Field**
- Scalar (1 attribute)
- Vector (2+ attributes)
- Tensor (3+ attributes)

# Visualization
**Sciviz** (scientific visualization) subfield, use of space is given with the dataset
**Infoviz** (information visualization) subfield, use of space is chosen by designer

## Use
Analyze with three questions: 
- what data the user sees
- why the user intends to use a vis tool
- how the visual encoding and interaction idioms are constructed in terms of design choices
Each three-fold what–why–how question has a corresponding data–task– idiom answer trio. One of these analysis trios is called an instance

### Building Blocks of visual encoding
- Marks (Geometric elements) ![[Pasted image 20220128175543.png]]
- Channels (Properties of the element's appearance; magnitude) ![[Pasted image 20220128175601.png]]
	- **Magnitude** channels, dimension
	- **Identity** channels, categorical

### Channel Selection
- **Effectiveness principle** importance of attribute should match saliency of data
- **Expressiveness principle** all of and only info in dataset, dont imply anything else