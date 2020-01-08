###Methods Description
1. to create a test record a user has to call "__create_root_summary()__". This should be called only one time for each test(example: Burn-in)
![](image.png)
1. Call "__measurements()__" to create a sub-test that includes or doesn't include 
measurements. to use messurements both the __test()__ parameters 
and the __messurments()__ paramenters must be met
1. If a user needs to add comments/notes call "__message()__" 
1. "__pretty()__" reformats and creates the xml to have readable indentation
1. "__insert()__" loads an xml file to a  maintainable station by passing
 in the xml file created by "__pretty()__" and the station key(BurnIn, Functional...)
___
[Link to Maintainable xml requirements](https://secure.maintainabletest.com/help/extending/file_formats.html#maintainable-test-report-xml)
___
### Examples of how to call each method"
__Parameters:__ create_root_summary(part_number, serial_number, operation, status, started_at, ended_at)
```Python
Etree.create_root_summary("31-001197-03-01", "113710008405", "Functional", "Pass", "2019-01-02 13:45:35",
                          "2019-01-02 13:52:50", "wo123123","operator_name","fixture_ident","fixture_socket",
                           "program_name", "program_version")
```

__Parameters Req:__ measurements(test_name, test_status, name, status, measured)
```Python
Etree.measurements(
    {1: {"number": "1", "test_name": "fn", "test_status": "Passed", "name": "Successful", "status": "Passed",\
         "measured": "2", "Unit": "89",\
         "min": "2"},\
     2: {"test_name": "fn", "test_status": "Passed", "name": "Successful", "status": "Passed", "measured": "3",\
         "max": "5", "Comparator": "GELE"}})
```
__Parameters Req:__ message(name, status, text)
```Python

Etree.message("test", "Passed", "This is only a test")
```

__Parameters Req:__ properties(name, value)
```Python

Etree.properties("Configuration Sector", {"name": "RDR",
                                          "value": "5",
                                          "name": "RDR", "value": "4"})
```
                                          
__reformat file to be readable__
```Python
Etree.pretty()
```

__Parameters Req:__ insert(station key, xml_file)
```Python
Input.insert("a2bc48c7", "items2.xml")
```
___



