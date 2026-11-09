# Library Management System: Java (JavaFX Reporting Module)

A JavaFX desktop application that imports the CSV files produced by the [Python Library Management System](https://github.com/vashika-0507/LibraryManagementSystem-Python), validates them, and generates reports. It is the second half of a two-part library system: Python handles day-to-day operations, Java handles data import and reporting.

## Features

- **Import and validate:** load `book.csv`, `student.csv` and `transactions.csv`. Invalid rows are skipped and listed with their line number and the reason.
- **Books issued report:** enter a date (DD/MM/YYYY) to see every book issued that day, with a total count.
- **Average book cost:** shows the number of books, the total cost and the average cost.
- **Search by title:** partial matching, plus a wildcard search such as `Harry*` for titles starting with a prefix.
- **Export:** save search results to a text file.

## Validation rules

| Field | Rule |
|---|---|
| ISBN-13 | 13 digits and a correct check digit |
| Student ID | exactly 8 digits |
| Copies | 1 or 2 |
| Available | between 0 and the number of copies |
| Date | DD/MM/YYYY with a valid day, month and year |
| Book ID | 2 letters followed by 2 digits (checked in `Validator`) |

All validation logic lives in `Validator.java` and is covered by **25 JUnit 5 tests**.

## Technologies

Java 21, JavaFX 21 (FXML), Maven, JUnit 5

## Concepts demonstrated

- Object-oriented design with model classes (`Book`, `Student`, `Transaction`)
- Separation of view and logic: the FXML layout is separate from `MainController`
- File handling with `BufferedReader` and try-with-resources
- Input validation and error reporting
- Unit testing

## Project structure

```
src/
├── main/
│   ├── java/
│   │   ├── module-info.java
│   │   └── com/library/
│   │       ├── MainApp.java
│   │       ├── controller/MainController.java
│   │       ├── model/ (Book, Student, Transaction)
│   │       └── util/ (CsvReader, Validator)
│   └── resources/com/library/librarymanagementsystem/main-view.fxml
└── test/java/ValidatorTest.java
```

Sample data files (`book.csv`, `student.csv`, `transactions.csv`) are included in the repository.

## How to run

1. Install JDK 21.
2. Open the project in IntelliJ IDEA and let Maven load the dependencies.
3. Run `MainApp`.
4. On the **Import Files** tab, select the three CSV files and click **Import All Files**.

Run the tests with:

```bash
./mvnw test
```

## Possible improvements

- Handle commas inside book titles (the importer currently splits each line on commas)
- Validate book IDs during import, not only in the `Validator` class
- Add a returns report next to the issued report

## Author

**Vashika Maheswaran**, BSc (Hons) Artificial Intelligence with Data Science, Robert Gordon University (delivered by IIT, Colombo)
[GitHub](https://github.com/vashika-0507) · [LinkedIn](https://www.linkedin.com/in/vashika-maheswaran-71a17738b)
