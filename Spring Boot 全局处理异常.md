# Spring Boot 全局处理异常
在Spring Boot中，可以通过编写一个全局异常处理器（Global Exception Handler）来处理应用程序中所有未处理的异常，使应用程序更加健壮和可靠。以下是一个简单的示例：
1. 创建一个类并实现Spring的 ErrorController 接口。
```java
@Controller
public class GlobalExceptionHandler implements ErrorController {

    @RequestMapping("/error")
    public ResponseEntity<Object> handleError(HttpServletRequest request) {
        // 处理异常并返回相应的信息
    }

    @Override
    public String getErrorPath() {
        return "/error";
    }
}
```
2. 在 handleError 方法中，通过检查请求中的异常信息来处理异常并返回相应的信息。可以使用 @ExceptionHandler 注解来处理特定类型的异常。如果异常类型未被处理，则可以返回一个通用的错误消息。
```java
@ExceptionHandler(NullPointerException.class)
public ResponseEntity<Object> handleNullPointerException(HttpServletRequest request, NullPointerException ex) {
    // 处理NullPointerException异常并返回相应的信息
}

@ExceptionHandler(Exception.class)
public ResponseEntity<Object> handleException(HttpServletRequest request, Exception ex) {
    // 处理所有未处理的异常并返回相应的信息
}
```

3.在类级别上使用 @ControllerAdvice 注解来使该类成为全局异常处理器，并将其添加到Spring Boot应用程序中。
```java
@ControllerAdvice
public class GlobalExceptionHandler {

    // 上面的异常处理方法
}

```

以上就是处理Spring Boot中全局异常的基本步骤。但是，实际情况可能会更加复杂。您可能需要根据您的需求进行更多的自定义和处理。