# Easy XML

Highly configurable Object to XML converter for Node.

## Installation

```console
$ npm install easyxml
```

## Usage

```javascript
var easyxml = require('easyxml');

easyxml.configure({
    singularizeChildren: true,
    underscoreAttributes: true,
    rootElement: 'response',
    dateFormat: 'ISO', // JS, SQL
    indent: 2,
    manifest: true
});

var myObject = {
    items: [{
        name: 'one',
        _id: 1
    }, {
        name: 'two',
        _id: 2
    }, {
        name: 'three',
        _id: 3
    }],
    blah: 'http://www.google.com',
    when: new Date(),
    boolz: true,
    nullz: null
};

console.log(easyxml.render(myObject));
```

This should output the following XML document:

```xml
<?xml version='1.0' encoding='utf-8'?>
<response>
  <items>
    <item id="1">
      <name>one</name>
    </item>
    <item id="2">
      <name>two</name>
    </item>
    <item id="3">
      <name>three</name>
    </item>
  </items>
  <blah>http://www.google.com</blah>
  <when>2012-09-25T18:47:39.485Z</when>
  <boolz>true</boolz>
  <nullz />
</response>
```

## Configuration

* `singularizeChildren`: If an array is plural, its children elements will be singular
* `underscoreAttributes`: String attributes starting with _ will be XML attributes
* `underscoreChar`: Prefix to look for when creating attributes
* `rootElement`: A string to wrap around your entire XML object
* `dateFormat`: A date format for JS dates, currently accepts ISO, SQL, JS
* `indent`: A number representing the spaces to indent children, use 0 for no whitespace
* `manifest`: Whether or not to add that XML manifest line to the top
* `unwrappedArrays`: TODO: Document
* `filterNulls`: Should nulls and undefines be removed from the rendered XML

## License

This project is licensed under a Dual BSD/GPL license.
