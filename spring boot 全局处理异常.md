
To handle global exceptions in Spring, you can use the

@ControllerAdvice

annotation to define a class that will handle exceptions for all controllers. Within this class, you can define methods annotated with

@ExceptionHandler

to handle specific exceptions. Here's an example:
```
@ControllerAdvice

public class GlobalExceptionHandler {

  

    @ExceptionHandler(Exception.class)

    public ResponseEntity<String> handleException(Exception e) {

        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body("An error occurred");

    }

  

    @ExceptionHandler(MyCustomException.class)

    public ResponseEntity<String> handleMyCustomException(MyCustomException e) {

        return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(e.getMessage());

    }

  

}
```

  

In this example,

GlobalExceptionHandler

is the class that will handle exceptions for all controllers. It has two methods annotated with

@ExceptionHandler

. The first method will handle any

Exception

that is thrown, and will return a

500 Internal Server Error

response with the message "An error occurred". The second method will handle

MyCustomException

, and will return a

400 Bad Request

response with the message from the exception.

You can customize the response entity returned by the exception handler methods to suit your needs.
