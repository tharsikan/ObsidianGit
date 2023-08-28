Actuator gives APIs for application information
Example: 
- `/actuator/info`: Application information
- `/actuator/health`: Health check
- `/actuator/metrics`: Metrics about the application
- `/actuator/env`: Environment properties
- `/actuator/beans`: Information about Spring beans
- `/actuator/mappings`: URL mappings

1. **`/actuator/heapdump`**: Generates and returns a heap dump of the application. This can be useful for diagnosing memory-related issues.
    
2. **`/actuator/threaddump`**: Provides a thread dump of the application, showing the current state of threads, their stack traces, and other relevant information. This can help in diagnosing thread-related problems.
    
3. **`/actuator/logfile`**: Returns the contents of the application's log file. This can be helpful for retrieving logs without direct access to the server's file system.
    
4. **`/actuator/loggers`**: Allows you to view and configure logging levels for different parts of your application.
    
5. **`/actuator/conditions`**: Shows the conditions that were evaluated during the startup of the application, helping you understand why certain components were or were not auto-configured.
    
6. **`/actuator/scheduledtasks`**: Provides information about the scheduled tasks defined in your application.
    
7. **`/actuator/httptrace`**: Offers information about HTTP requests and responses, including timestamps, status codes, and more.
    
8. **`/actuator/caches`**: Allows you to interact with the application's caches, including evicting cache entries.
    
9. **`/actuator/threaddump`**: Provides a human-readable dump of all live threads in the JVM.
    
10. **`/actuator/sessions`**: If your application uses Spring Session, this endpoint provides information about user sessions


OWN Actuator endpoints

```java
@Component  
@Endpoint(id="stage")  
public class StageEndpoint {  
    Map<String, Stage> stages = new ConcurrentHashMap<>();  
  
    @ReadOperation  
    public Map<String, Stage> getStages() {  
        return stages;  
    }  
  
    @WriteOperation  
    public void setStages(@Selector String name, int stage) {  
        stages.put(name, new Stage(stage));  
    }  
  
    @ReadOperation  
    public Stage getStage(@Selector String name){  
        return stages.get(name);  
    }  
  
    static class Stage{  
        int value;
        constructor, getter, setter 
    }
```

![[Drawing 2023-08-26 22.38.35.excalidraw|200]]

post: http://localhost:8080/actuator/stage/st1002
{
    "stage": 1003
}

{

get: http://localhost:8080/actuator/stage
{
    "st1002": {
        "value": 1003
    },
    "st003": {
        "value": 1003
    },...

by using this we can dynamically change configuration/ log_level


