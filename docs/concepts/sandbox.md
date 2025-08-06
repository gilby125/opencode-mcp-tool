# Plan Mode

Structured analysis and planning before code execution.

## What is Plan Mode?

Plan mode allows OpenCode to analyze your request and create structured plans before executing code, ensuring safer and more thoughtful development.

## Basic Usage

```
/opencode:plan create a Python script that sorts a list
```

## How It Works

1. **Request** → You ask for code to be created/tested
2. **Generation** → OpenCode writes the code
3. **Execution** → Code runs in isolated environment
4. **Results** → Output returned safely

## Use Cases

### Algorithm Testing
```
/opencode:plan implement and test quicksort in JavaScript
```

### Data Processing
```
/opencode:plan parse this CSV and show statistics: [data]
```

### Proof of Concepts
```
/opencode:plan create a working web scraper example
```

## Planning Features

- **Structured Analysis**: Breaks down complex requests
- **Safety Checks**: Reviews code before execution  
- **Step-by-Step**: Clear implementation roadmap
- **Best Practices**: Follows coding standards

## Supported Languages

- Python
- JavaScript/Node.js
- Ruby
- Go
- Java
- C++
- More coming soon!

## Best Practices

### 1. Be Specific
```
// Good
create a function that validates email addresses with tests

// Vague
make something that checks emails
```

### 2. Include Test Cases
```
implement binary search with edge case handling and show test results
```

### 3. Iterative Development
```
// First iteration
create a basic REST API

// Refine
add authentication to the API

// Test
show example requests and responses
```

## Benefits

- Thoughtful code architecture
- Better error prevention
- Clear implementation steps
- Educational value
- Security-focused approach

## Examples

### Testing Algorithms
```
/opencode:plan benchmark bubble sort vs quick sort with 1000 items
```

### Learning Code
```
/opencode:plan show me how promises work in JavaScript with examples
```

### Debugging
```
/opencode:plan why does this code fail: [paste code]
```