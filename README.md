# BookMyShow Automation Framework

A comprehensive test automation framework for BookMyShow application using Selenium WebDriver, Cucumber, TestNG, and Java.

## 🚀 Project Overview

This project is a robust test automation framework designed to test the BookMyShow application's core functionalities including:
- Location/City selection
- Activities listing and filtering
- Events management
- User authentication flows

## 🛠️ Technology Stack

- **Programming Language**: Java 21
- **Test Framework**: TestNG 7.9.0
- **BDD Framework**: Cucumber 7.18.0
- **WebDriver**: Selenium 4.29.0
- **Build Tool**: Maven 3.x
- **Reporting**: Allure Reports 2.29.1
- **Logging**: Log4j2 2.20.0
- **Browser Management**: WebDriverManager 5.3.3

## 📁 Project Structure

```
bookmyshow-1/
├── src/
│   ├── main/java/com/bookmyshow/
│   │   ├── base/           # WebDriver setup and configuration
│   │   ├── listeners/      # Test listeners and retry mechanisms
│   │   ├── models/         # Data models and POJOs
│   │   ├── pages/          # Page Object Model classes
│   │   └── utils/          # Utility classes and helpers
│   ├── main/resources/     # Configuration files
│   └── test/
│       ├── java/com/bookmyshow/
│       │   ├── hooks/      # Cucumber hooks for setup/teardown
│       │   ├── runners/    # Test runners and configurations
│       │   ├── reRun/      # Retry mechanisms
│       │   └── stepDefinitions/ # Cucumber step definitions
│       └── resources/
│           ├── features/    # Cucumber feature files
│           ├── testdata/    # Test data files (Excel)
│           └── config/      # Test configuration files
├── target/                  # Compiled classes and reports
├── allure-results/         # Allure report results
├── test-output/            # Test execution outputs
└── logs/                   # Application logs
```

## 🚀 Getting Started

### Prerequisites

- Java 21 or higher
- Maven 3.6 or higher
- Chrome browser (latest version)
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd bookmyshow-1
   ```

2. **Verify Java version**
   ```bash
   java -version
   # Should show Java 21
   ```

3. **Verify Maven installation**
   ```bash
   mvn -version
   ```

### Configuration

1. **Update configuration properties** (`src/main/resources/config.properties`)
   ```properties
   app.url=https://in.bookmyshow.com
   browser=chrome
   implicit.wait=10
   explicit.wait=10
   page.load.timeout=30
   ```

2. **Update test data file path** if needed
   ```properties
   test.data.file=src/test/resources/testdata/testdata.xlsx
   ```

## 🧪 Running Tests

### Run All Tests
```bash
mvn clean test
```

### Run Specific Test Runner
```bash
mvn test -Dtest=TestRunner
```

### Run Tests with Specific Tags
```bash
# Run smoke tests only
mvn test -Dcucumber.filter.tags="@smoke"

# Run activities tests only
mvn test -Dcucumber.filter.tags="@activities"

# Run regression tests only
mvn test -Dcucumber.filter.tags="@regression"
```

### Run Tests from IDE
- Right-click on `TestRunner.java` and select "Run TestRunner"
- Or run individual feature files from the `features` directory

## 📊 Test Reports

### Allure Reports
After test execution, generate and view Allure reports:
```bash
# Generate report
mvn allure:report

# Open report in browser
mvn allure:serve
```

### Cucumber HTML Reports
HTML reports are automatically generated in:
```
target/cucumber-html-reports/index.html
```

### TestNG Reports
TestNG reports are available in:
```
target/surefire-reports/
```

## 🏗️ Framework Architecture

### Page Object Model (POM)
- **HomePage**: Handles city selection and navigation
- **ActivitiesPage**: Manages activities listing, filtering, and information extraction
- **EventsPage**: Handles events-related functionality
- **LoginPage**: Manages user authentication flows

### Step Definitions
- **BaseSteps**: Common WebDriver management
- **CommonStepDefinitions**: Shared steps like city selection
- **ActivitiesStepDefinitions**: Activities-specific test steps
- **EventsStepDefinitions**: Events-specific test steps

### Test Hooks
- **TestHooks**: Browser setup/teardown, screenshot capture on failure
- **RetryListener**: Automatic test retry mechanism for flaky tests
- **ScreenshotListener**: Captures screenshots on test failures

## 📝 Test Data Management

Test data is managed through Excel files located in `src/test/resources/testdata/`:
- `testdata.xlsx` - Main test data file
- `testdata_updated.xlsx` - Updated test data
- `comprehensive_testdata.xlsx` - Comprehensive test scenarios

## 🔧 Troubleshooting

### Common Issues

1. **Chrome Driver Version Mismatch**
   ```
   WARNING: Unable to find CDP implementation matching 138
   ```
   - This is a warning and doesn't affect test execution
   - Chrome driver is automatically managed by WebDriverManager

2. **Element Not Found Errors**
   - Check if the website structure has changed
   - Update locators in page classes
   - Verify element selectors in `@FindBy` annotations

3. **Test Execution Failures**
   - Check logs in `logs/app.log`
   - Review Allure reports for detailed failure information
   - Verify test data in Excel files

### Debug Mode
Enable debug logging by updating `log4j2.xml`:
```xml
<Logger name="com.bookmyshow" level="DEBUG"/>
```

## 🚀 Best Practices

1. **Page Object Model**: Always use POM for better maintainability
2. **Explicit Waits**: Use explicit waits instead of implicit waits
3. **Test Data**: Keep test data separate from test logic
4. **Reporting**: Always check Allure reports for test insights
5. **Logging**: Use proper logging for debugging and monitoring

## 📋 Test Scenarios

### Smoke Tests (`@smoke`)
- Basic navigation and city selection
- Activities page accessibility
- Core functionality verification

### Regression Tests (`@regression`)
- Comprehensive feature testing
- Filter functionality
- Data extraction and validation

### Activities Tests (`@activities`)
- Activities page navigation
- Category filtering
- Information extraction

## 🤝 Contributing

1. Follow the existing code structure and naming conventions
2. Add proper logging and error handling
3. Update documentation for new features
4. Ensure all tests pass before committing



