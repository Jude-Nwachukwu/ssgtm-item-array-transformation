# GTM Item Array Transformation (Server-Side Version)

A Google Tag Manager (GTM) **server-side** custom variable template designed to transform arrays of objects by remapping attribute keys. This template simplifies the process of structuring data for analytics, tagging, or other integrations.

**➡️ Here is the custom template repository for the [web GTM custom template](https://github.com/Jude-Nwachukwu/gtm-item-array-transformation)**


## Features

- **Flexible Attribute Mapping**: Remap existing attribute keys to new ones using a user-defined table.
- **Ecommerce Items Source Selection**: Choose between extracting items from **event data** or using a custom variable that holds the array.
- **Efficient Data Handling**: Validates input arrays and ensures proper mapping.
- **Dynamic Transformations**: Handles complex transformations dynamically and reliably.
- **Data Formatting Options**: Convert attributes to numbers, integers, or strings.
- **Static Key-Value Assignments (Optional)**: Define static attributes with fixed values for all items.

## Use Cases

- Restructuring ecommerce event data for custom tracking.
- Converting object keys to align with third-party integration requirements.
- Adapting data structures for use in multi-platform analytics.

## Template Configuration

### 1. Select Items Array Source

Users must first choose the **Ecommerce Items Array Source (Array of Objects)**:

| Option                            | Description                                                               |
| --------------------------------- | ------------------------------------------------------------------------- |
| **Use Event Data Items Array**    | Automatically fetches the `items` array from the event data.              |
| **Use Custom Variable**           | Requires users to provide a variable containing the items array.          |

After selecting the source, proceed with attribute mapping and optional data formatting.

### 2. Attribute Key Mapping

| Field Name            | Description                           |
| --------------------- | ------------------------------------- |
| **Attribute Mapping** | A table mapping old keys to new keys. |

### 3. Data Formatting Options

Users can apply transformations to selected attributes:

- **Convert to Number**
- **Convert to Integer**
- **Convert to String**

### 4. Static Key-Value Assignments (Optional)

| Field Name            | Description                                     |
| --------------------- | ----------------------------------------------- |
| **Static Attributes** | A table mapping fixed attribute keys to values. |

## Transformation Examples

### Example 1: Basic Attribute Mapping

#### Input Array
```json
[
  { "oldKey1": "value1", "oldKey2": "value2" },
  { "oldKey1": "value3", "oldKey2": "value4" }
]
```

#### Attribute Mapping Table
| Old Key | New Key |
| ------- | ------- |
| oldKey1 | newKey1 |
| oldKey2 | newKey2 |

#### Output
```json
[
  { "newKey1": "value1", "newKey2": "value2" },
  { "newKey1": "value3", "newKey2": "value4" }
]
```

### Example 2: Attribute Mapping with Static Key-Value Assignments

#### Static Key-Value Table
| Static Key | Static Value |
| ---------- | ------------ |
| fixedKey   | fixedValue   |

#### Output
```json
[
  { "newKey1": "value1", "newKey2": "value2", "fixedKey": "fixedValue" },
  { "newKey1": "value3", "newKey2": "value4", "fixedKey": "fixedValue" }
]
```

### Example 3: Data Formatting (Numbers & Strings)

#### Input Array
```json
[
  { "price": "10.99", "quantity": "5" }
]
```

#### Data Formatting Rules
| Attribute | Format  |
| --------- | ------- |
| price     | Number  |
| quantity  | Integer |

#### Output
```json
[
  { "price": 10.99, "quantity": 5 }
]
```

### Example 4: Mixed Transformations

#### Input Array
```json
[
  { "sku": "1234", "cost": "15.50", "stock": "10" },
  { "sku": "5678", "cost": "8.75", "stock": "20" }
]
```

#### Attribute Mapping Table
| Old Key | New Key  |
| ------- | -------  |
| sku     | item_id  |
| cost    | price    |
| stock   | quantity |

#### Data Formatting Rules
| Attribute | Format  |
| --------- | ------- |
| price     | Number  |
| quantity  | Integer |

#### Output
```json
[
  { "item_id": "1234", "price": 15.50, "quantity": 10 },
  { "item_id": "5678", "price": 8.75, "quantity": 20 }
]
```

## Installation

1. Download the JSON file for the custom template from this repository.
2. Import it into your Google Tag Manager account.
3. Configure the fields as per your requirements.

## Author

Created by **Jude Nwachukwu Onyejekwe**.

This template is part of the [Dumbdata.co Measurement Resource Hub](https://dumbdata.co), which provides resources designed to simplify measurement strategies and implementations.

## License

This project is licensed under the Apache License.

