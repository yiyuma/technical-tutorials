SpringBootApplication enthält @ComponentScan, @EnableAutoConfiguration, @Configuraion
```
@SpringBootApplication(scanBasePackage="de.ekl.backend")
```

@RestController = @Controller + @ResponseBody (Die Rückgabe aller Methoden wird mit einem ResponseBody angebunden)
@GetMapping(path= "/api/user/{id}", produces = MediaType.APPLICATION_JSON_VALUE)
@PostMapping(path= "/api/auth/login",consumes = MediaType.APPLICATION_JSON_VALUE, produces = MediaType.APPLICATION_JSON_VALUE)
@PutMapping itempotent
@DeleteMapping

@PathVariable String id
@RequestParam(name="user-name", defaultValue="") String userName

@ControllerAdvise (class level) + @ExceptionHandler (method level)


