# sql_validator

The program functions as a basic SQL query validator that implements Rust as its development framework. The system analyses SQL SELECT queries applied against an internal memory table then verifies the output against the predetermined results. This application enables users to execute basic SELECT statements with optional database conditions that can utilize AND statements for filtering. The application depends on the sqlparser crate for SQL query analysis and the maplit crate provides easy data sample definition.
A proper installation of Rust is essential to execute the required compilation and execution. Build the project using cargo build followed by project execution through cargo run. The program runs the SQL query from the source code while validating its actual outcome against a specified output.

Two additional packages are needed by the project: the sqlparser library for SQL statement parsing as well as maplit for simplifying table row creation through hash maps. Prior to compilation you need to add dependencies in your Cargo.toml file.

When trying the query SELECT name FROM student WHERE major = 'CS', the in-memory student table consisting of students Alice, Bob, and Charlie with their majors should return only Alice and Charlie. When the program returns "Query is correct" the result data matches what was predetermined.
The parser cannot interpret syntax that lacks proper SQL syntax elements such as WHERE (SELECT name FROM student major = 'CS') or contains syntax errors (SELECT name FROM student major = 'CS'). The program displays "Query is incorrect" when this situation occurs.

The project contains its Rust code located in src/main.rs together with Cargo.toml for dependency declaration and this README that demonstrates how to run tests and builds the program.
Please indicate whether you need assistance building the .md file along with setting up a complete Rust project framework.


Sample testcases:
case 1:
Input:
let student_table = Table {
        rows: vec![
            hashmap! {"id".into() => "1".into(), "name".into() => "Alice".into(), "major".into() => "CS".into()},
            hashmap! {"id".into() => "2".into(), "name".into() => "Bob".into(), "major".into() => "Math".into()},
            hashmap! {"id".into() => "3".into(), "name".into() => "Charlie".into(), "major".into() => "CS".into()},
        ],
    };
    let query = "SELECT name FROM student WHERE major = 'CS'";

output:
Query is correct

Case2:
Input:
let student_table = Table {
        rows: vec![
            hashmap! {"id".into() => "1".into(), "name".into() => "Alice".into(), "major".into() => "CS".into()},
            hashmap! {"id".into() => "2".into(), "name".into() => "Bob".into(), "major".into() => "Math".into()},
            hashmap! {"id".into() => "3".into(), "name".into() => "Charlie".into(), "major".into() => "CS".into()},
        ],
    };
    let query = "SELECT name FROM student major = 'CS'";

output:
Query is incorrect


