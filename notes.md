Week 1 PHP Learning Notes
1. How PHP Processes a Request
PHP runs on the server rather than in the user's browser, which means the browser only ever sees the final result—not the underlying PHP code.

Here is what happens behind the scenes when someone loads a PHP page:

A visitor types a URL or clicks a link.

Their browser sends a request to the web server.

The server locates the requested .php file.

PHP runs the code inside that file.

Along the way, the script might handle form inputs, evaluate conditions, work with files, or run other logic.

PHP produces an output, typically HTML.

The server sends that output back to the browser.

The browser renders the page on screen.

2. Arrays vs. Objects
Both arrays and objects help organize data in PHP, though they serve slightly different purposes.

Arrays
An array lets me hold multiple values inside a single variable—handy when I have a set of related details to keep together.

PHP
$student = [
    "name" => "Issack",
    "age" => 20,
    "course" => "Computer Engineering"
];

echo $student["name"];
Objects
An object is built from a class and can bundle data (properties) together with actions or behaviors (methods).

PHP
class Student {
    public $name;
    public $course;

    public function introduce() {
        return "My name is " . $this->name;
    }
}

$student = new Student();
$student->name = "Issack";
$student->course = "Computer Engineering";

echo $student->introduce();
Key Difference
Arrays are primarily for storing and grouping values, while objects combine data with methods that act on that data.

3. Why We Sanitise User Input
Sanitising means cleaning up input from users before using or displaying it. People filling out a form might type extra spaces, stray characters, or even malicious HTML or script tags.

Sanitising helps me:

Stop unwanted HTML or JavaScript from rendering on the page.

Guard against common web security issues.

Keep incoming data tidy and predictable to work with.

Avoid broken or unexpected page output.

PHP
$name = trim($_POST["name"] ?? "");

$safeName = htmlspecialchars($name, ENT_QUOTES, "UTF-8");

echo $safeName;
trim() strips leading and trailing whitespace.

htmlspecialchars() turns special HTML characters into safe entities before output.

It is also worth keeping sanitising and validating separate in mind: validation checks whether data meets expected rules (like confirming an email address looks valid), while sanitising cleans or safely prepares the data.

Overall, PHP makes it practical to build dynamic sites, and seeing how requests, arrays, objects, and form inputs fit together gave me a much clearer picture of how web apps work in practice.
