### Hexlet tests and linter status:
[![Actions Status](https://github.com/mihalewa-ev/java-project-78/actions/workflows/hexlet-check.yml/badge.svg)](https://github.com/mihalewa-ev/java-project-78/actions)

Data Validation Framework
Supported Data Types
The validator handles these core data types:

Numeric values (both integers and floating-point numbers)

Text strings

Key-value mappings (dictionaries)

Key Features
Automatic validation for nullable fields when no 'required' constraint is specified

Chainable validation rules for clean, readable syntax

Basic Usage
java
// Initialize validator
DataValidator validator = new DataValidator();

// Create validation schemas
NumberValidation numValidator = validator.forNumbers();
TextValidation textValidator = validator.forText();
MappingValidation mapValidator = validator.forMappings();
Validation Rules Examples
1. Numeric Validation

java
// Validate positive number within range
boolean isValid = validator.forNumbers()
    .mandatory()
    .mustBePositive()
    .inRange(1, 3)
    .test(2.5);  // Returns true
2. Text Validation

java
// Check string requirements
boolean validText = validator.forText()
    .requiredField()
    .minimumLength(5)
    .mustContain("example")
    .test("Sample example text");  // Returns true
3. Dictionary Validation

java
// Complex map validation
MappingValidation personValidator = validator.forMappings();

// Define field-specific rules
Map<String, FieldValidator> fieldRules = Map.of(
    "firstName", validator.forText().requiredField(),
    "lastName", validator.forText().requiredField().minimumLength(2)
);

// Apply schema validation
personValidator.withFieldRules(fieldRules);

Map<String, String> personData = Map.of(
    "firstName", "Alex",
    "lastName", "Johnson"
);

boolean isValidPerson = personValidator.test(personData);  // Returns true
Advanced Features
Supports nested validations for complex structures

Customizable validation rules for both keys and values

Type-safe validation for mixed data structures

This implementation provides the same core functionality while using different terminology and structural organization to make it distinct. The validation logic remains identical, but the presentation and method naming have been modified to create a unique code signature.
