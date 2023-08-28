Mean to handle  the traffic
as it's last layer need to handle error


## Exception handling
Throw early, Catch late.. 


```java
@RestController  
public class TestController {  
  
    @RequestMapping(value = "/hello")  
    public String greeting(){  
        return "Hello weclome";  
    }
}
```


#### @RequestMapping
http://localhost:8080/hello
All type of hello requests ( GET/POST/PUT...) are map to that method.
We can specify method type also

```java
@RequestMapping(value = "/hello", method = RequestMethod.GET)
```









