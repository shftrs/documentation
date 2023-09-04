# SHFTRS Documentation

## APIs

With Shftrs you can call SOAP and REST APIs.

### To test SOAP you need two parts:

1. The XML representing the SOAP payload
2. The test representing the expected in and output.

The following is an example of the two:

SOAP-XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<s11:Envelope xmlns:s11='http://schemas.xmlsoap.org/soap/envelope/'>
  <s11:Body>
    <ns1:GetLabs xmlns:ns1='http://tempuri.org/' />
  </s11:Body>
</s11:Envelope>
```

TEST:

```json
{
  "initial-state": {},
  "sequence": [
    {
      "type": "soap",
      "url": "<URL>",
      "xml": "<PATH TO TEST JSON FILE>",
      "headers": {
        "content-type": "text/xml; charset=utf-8"
      }
    }
  ]
}
```

The sequence can be however long it needs to be.

### To test REST you need:

1. The test representing the expected in and output.
2. You don't need a schema to validate against, but it is a strong and powerful way to validate your API calls

TEST:

```json
{
  "initial-state": {},
  "sequence": [
    {
      "type": "rest",
      "url": "<URL>",
      "method": "<METHOD>",
      "schema": "<PATH TO JSON SCHEMA FILE>",
      "headers": {
        "content-type": "application/json"
      }
    }
  ]
}
```

METHOD: GET, POST, PUT or DELETE

SCHEMA:

```json
{
  "title": "Product",
  "description": "A product for a company",
  "type": "object",

  "properties": {
    "id": {
      "description": "The unique identifier for a product",
      "type": "integer"
    },

    "name": {
      "description": "Name of the product",
      "type": "string"
    },

    "price": {
      "type": "number",
      "minimum": 0
    }
  },

  "required": ["id", "name", "price"]
}
```

# UI

Runs UI tests via a headless browser, the following are the commands available.

### NAVIGATE

```json
{
  "type": "ui",
  "action": "navigate",
  "url": "<URL>"
}
```

Navigate to a specific URL.

### CLICK

```json
{
  "type": "ui",
  "action": "click",
  "selector": "<selector>"
}
```

Simulates a click on a specific selector follows standard selectors:

### DOUBLE CLICK

```json
{
  "type": "ui",
  "action": "double-click",
  "selector": "<selector>"
}
```

Simulates a double click on a specific selector follows standard selectors:

### SELECT OPTION

```json
{
  "type": "ui",
  "action": "select-option",
  "selector": "<selector>",
  "value": "<value>"
}
```

Selects a specific value from a select option

### FILL

```json
{
  "type": "ui",
  "action": "fill",
  "selector": "<selector>",
  "value": "<value>"
}
```

Fill a selector with a specific value. Used to fill in fields.

### TYPE

```json
{
  "type": "ui",
  "action": "type",
  "selector": "<selector>",
  "value": "<value>"
}
```

Fill a selector with a specific value. Used to fill in fields when you need the key press from the keyboard.

### IS CHECKED

```json
{
  "type": "ui",
  "action": "is-checked",
  "selector": "<selector>",
  "value": "<value>"
}
```

Checks if a specific value is selected among checkboxes

### INNER TEXT

```json
{
  "type": "ui",
  "action": "inner-text",
  "selector": "<selector>",
  "value": "<value>"
}
```

Compares the inner text with the supplied value.

### INPUT VALUE

```json
{
  "type": "ui",
  "action": "input-value",
  "selector": "<selector>",
  "value": "<value>"
}
```

Checks that an input value (input-fields, text-areas, checkboxes ...) have the correct value.

### SAVE VALUE

```json
{
  "type": "ui",
  "action": "save-value",
  "name": "test",
  "selector": "<selector>"
}
```

Creates an variable "test" and saves the value in the "<selector>" to the variable.

### WAIT FOR SELECTOR

```json
{
  "type": "ui",
  "action": "wait-for-selector",
  "selector": "<selector>"
},
```

### IMAGE DIFF

```json
{
  "type": "ui",
  "action": "image-diff",
  "screenshot": "<root-path-to-directory>",
  "threshold": 0.001
}
```

## Selectors

\# = an HTML id (eg. #my-id>)
. = class (eg. .my-class)
