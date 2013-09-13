generic-soap-client [![Build Status](https://secure.travis-ci.org/impactcentre/iif-generic-soap-client.png?branch=master)](http://travis-ci.org/impactcentre/iif-generic-soap-client)
-------------------

This is a library that can execute operations of an arbitrary SOAP web service. 

It takes a URL to a WSDL and generates a data structure corresponding to the definitions. 
All operations and input fields can be accessed and set at runtime. After executing an operation,
the returned values and file attachments can be read. 

Some simple usage examples:


// initialize the service
```java
SoapService service = new SoapService("http://myhost/myservice?wsdl");
```

// service operations
```java
List<SoapOperation> allOps = service.getOperations();  
SoapOperation op = service.getOperation("myOperation");
```

// analyzing and setting input values
```java
List<SoapInput> allInputs = op.getInputs();  
SoapInput in = allInputs.get(0);  
String name = in.getName();  
boolean multi = in.isMultiValued(); //&nbsp;can contain several values  
List<String> possible = in.getPossibleValues(); //&nbsp;for restricted types  
in.setValue("some value");
```

// executing the operation
```java
List<SoapOutput> outs = op.execute();
```

// printing the outputs
```java
for (SoapOutput out : outs) {  
                System.out.println(out.getName());
                System.out.println(out.getValue());
}
```