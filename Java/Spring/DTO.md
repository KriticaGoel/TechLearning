Step 1: use below dependency to validate the DTO
```xml
<dependency>
<groupId>jakarta.validation</groupId>
<artifactId>jakarta.validation-api</artifactId>
</dependency>
```

Step 2: import below
import jakarta.validation.constraints.Size;

Step 3 use annotation in dto

```java
@NotNull(message = "username cannot be null")
@Size(min=3, max=20,message="username must contain at least 3 character")
private String username;

@NotNull(message = "Password cannot be null")
@Size(min = 5, max = 50, message = "Password must contain at least 5 characters")
@Pattern(regexp = "^(?=.*[0-9])(?=.*[A-Z])(?=.*[!@#$%^&*])[a-zA-Z0-9!@#$%^&*]+$",
        message = "Password must contain at least one number, one capital letter, and one special character")

//    @Pattern(regexp = "^(?=(?:.*[0-9]){2,})(?=.*[!@#$%^&*])[a-zA-Z0-9!@#$%^&*]+$",
//            message = "Password must contain at least two numbers and one special character")

private String password;

@Email(message = "Email is not valid")
@NotNull(message = "Email cannot be null")
@Size(min=3, max=50, message="Email must contain at least 3 character")
private String email;

```

Create separate DTO for request and response