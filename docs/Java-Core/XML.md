# XML

> 在JDK中内置了两种XML解析器-DOM和SAX

## DOM XML Parser

> The DOM is the easiest to use Java XML Parser. It parses an entire XML document and load it into memory, modeling it with Object for easy nodel traversal. DOM Parser is slow and consume a lot memory if it load a XML document which contains a lot of data.

### Read a XML file

```XML
<?xml version="1.0"?>
<company>
  <staff id="1001">
    <firstname>yong</firstname>
    <lastname>mook kim</lastname>
    <nickname>mkyong</nickname>
    <salary>100000</salary>
  </staff>
  <staff id="2001">
    <firstname>low</firstname>
    <lastname>yin fong</lastname>
    <nickname>fong fong</nickname>
    <salary>200000</salary>
   </staff>
</company>
```
