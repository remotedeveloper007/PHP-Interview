# What is PHP?

PHP (Hypertext Preprocessor) is a widely-used open-source server-side scripting language designed primarily for web development. It is embedded within HTML to create dynamic web pages. PHP can be used to perform a variety of tasks, such as:

1. **Server-Side Scripting**: PHP can process form data, manage sessions, and generate dynamic content based on user interaction.

2. **Database Interaction**: PHP is often used with databases like MySQL to store and retrieve data, allowing websites to handle data-driven content, such as user accounts or product listings.

3. **Building Web Applications**: PHP powers many content management systems (CMS) like WordPress, Drupal, and Joomla, as well as popular e-commerce platforms like Magento and WooCommerce.

4. **Command-Line Scripting**: PHP can also be used for running scripts from the command line, not just within a web server.

PHP code is executed on the server, and the result (usually HTML) is sent to the client's browser. It is known for its simplicity, flexibility, and integration with various databases and web technologies.

---

### Data Types in PHP

PHP supports various data types, which are categorized as **scalar** and **compound** data types. Here's an overview of the data types in PHP:

1. **String**
2. **Integer**
3. **Float (or Double)**
4. **Boolean**
5. **Array**
6. **Object**
7. **NULL**

Now, let's explain each type in detail with examples of how they are used in real-time applications.

---

### 1. **String**

A **string** is a sequence of characters enclosed in quotes. In PHP, you can use single quotes (`'`) or double quotes (`"`) to define strings.

#### Real-Time Example:
**User Authentication System** – Storing user input (like name or email) as a string.

```php
<?php
// String Data Type Example
$username = "john_doe";  // Storing a username as a string
$password = '1234';       // Storing a password as a string

echo "User: " . $username;  // Output: User: john_doe
?>
```

In a real-world application like a login system, strings are used to store text like usernames and passwords, which are essential for user authentication.

---

### **Methods in String**

In PHP, **strings** are one of the most commonly used data types. PHP offers many string manipulation functions that allow developers to perform operations such as searching, replacing, trimming, and formatting text. Below are the most commonly used string functions in PHP, along with detailed explanations, real-life examples, and code.

### 1. **`strlen()`**

#### Explanation:
The `strlen()` function returns the length of a string. It counts the number of characters in the string, including spaces and special characters.

#### Real-life Example: Checking password length for validation

In an e-commerce application, you may want to validate the length of a user's password to ensure it meets the minimum requirements.

#### Code:
```php
$password = "securePassword123";

// Check password length
if (strlen($password) >= 8) {
    echo "Password is long enough.";
} else {
    echo "Password is too short. It must be at least 8 characters.";
}
```

**Output:**
```
Password is long enough.
```

---

### 2. **`strpos()`**

#### Explanation:
The `strpos()` function searches for a substring within a string and returns the position of the first occurrence of the substring. If the substring is not found, it returns `false`.

#### Real-life Example: Checking if a product name contains a specific keyword

In an e-commerce system, you might want to check if the product name contains specific keywords (e.g., "sale", "discount").

#### Code:
```php
$productName = "Smartphone on Sale";

// Check if the word "Sale" is in the product name
if (strpos($productName, "Sale") !== false) {
    echo "This product is on sale!";
} else {
    echo "No sale for this product.";
}
```

**Output:**
```
This product is on sale!
```

---

### 3. **`stristr()`**

#### **Explanation:**
The `stristr()` function in PHP is used to search for the first occurrence of a substring in a string, **case-insensitively**. Unlike `strpos()`, which returns the position of the first occurrence, `stristr()` returns the **portion of the string** starting from the first occurrence of the substring to the end. If the substring is not found, `stristr()` returns `false`.

#### **Syntax:**
```php
stristr($haystack, $needle, $before_needle = false)
```

- `$haystack`: The input string to search in.
- `$needle`: The substring to search for.
- `$before_needle`: (Optional) If set to `true`, `stristr()` will return the part of the string before the first occurrence of the `$needle` instead of the part after it.

#### **Real-life Example: Searching for a keyword in a product description**

Imagine you are building an e-commerce application where you need to search for a product based on a keyword entered by the user. You want to check if the description contains the keyword (case-insensitively) and then show the portion of the description containing that keyword to highlight it.

#### **Code Example:**
```php
// Product description
$productDescription = "This is the latest model of our Smartphone. The new features make it stand out from the rest.";

// Search keyword entered by user
$searchKeyword = "smartphone";

// Case-insensitive search for the keyword in the product description
$found = stristr($productDescription, $searchKeyword);

if ($found) {
    echo "Keyword found: $found";
} else {
    echo "Keyword not found.";
}
```

**Explanation of Output:**

- The `stristr()` function is used to search for the word **"smartphone"** in the `$productDescription`.
- The search is **case-insensitive**, so it will match both "Smartphone" and "smartphone".
- If the substring is found, it returns the portion of the description starting from the first occurrence of the keyword until the end of the string.

**Output:**
```
Keyword found: Smartphone. The new features make it stand out from the rest.
```

#### **Real-life Scenario Breakdown:**
In an e-commerce platform, `stristr()` can be useful when:
1. **Displaying matching content:** If a user searches for a product (e.g., "smartphone"), you can highlight the part of the product description where the keyword is found.
2. **Case-insensitive searching:** It allows the user to search without worrying about the case (e.g., both "Smartphone" and "smartphone" should be matched).

You can use this function to find relevant information in product descriptions, user reviews, and other textual content in your application.

#### **Example with `before_needle` parameter:**
If you want to get the portion of the string before the keyword, you can pass `true` as the third parameter.

```php
// Search keyword entered by user
$searchKeyword = "smartphone";

// Get the part of the description before the first occurrence of the keyword
$beforeKeyword = stristr($productDescription, $searchKeyword, true);

if ($beforeKeyword) {
    echo "Text before keyword: $beforeKeyword";
} else {
    echo "Keyword not found.";
}
```

**Output:**
```
Text before keyword: This is the latest model of our 
```

This would be useful if you want to show the context **before** the keyword for some reason, such as when displaying search results and wanting to show the leading context for better relevance.

---

### **Summary:**
- `stristr()` is great for **case-insensitive** substring searching.
- It returns the part of the string **from the first occurrence** of the substring to the end.
- You can use it in scenarios like **searching** and **highlighting** keywords in content, making it very useful for building **search features** in applications like e-commerce platforms, blogs, and more.

By using `stristr()`, you ensure that searches are flexible and user-friendly, especially when users might not be aware of case sensitivity.

---

### 4. **`str_replace()`**

#### Explanation:
The `str_replace()` function is used to replace all occurrences of a substring with another substring. It’s commonly used for modifying strings, such as sanitizing inputs or replacing unwanted characters.

#### Real-life Example: Replacing unwanted characters in a product description

In an e-commerce platform, you may want to remove unwanted characters (e.g., certain special characters) from a product description before saving it.

#### Code:
```php
$productDescription = "This is an amazing product! #$@";

// Remove special characters
$cleanedDescription = str_replace(["#$@", "!"], "", $productDescription);

echo $cleanedDescription;
```

**Output:**
```
This is an amazing product
```

---

### 5. **`substr()`**

#### Explanation:
The `substr()` function returns a part of a string, starting from a specified position for a specified length. This is useful for extracting portions of a string.

#### Real-life Example: Extracting part of a product SKU

In an inventory management system, you might want to extract the first 3 characters of a product SKU to get the category code.

#### Code:
```php
$productSKU = "A1234-XYZ";

// Extract the category code (first 3 characters)
$categoryCode = substr($productSKU, 0, 3);

echo "Category Code: $categoryCode";
```

**Output:**
```
Category Code: A12
```

---

### 6. **`trim()`**

#### Explanation:
The `trim()` function removes whitespace (or other specified characters) from the beginning and end of a string. This is commonly used to clean user inputs before storing them in a database.

#### Real-life Example: Cleaning user input from a form

When a user submits a form, you might want to remove any leading or trailing spaces from the entered data.

#### Code:
```php
$userInput = "  Username123  ";

// Remove leading and trailing spaces
$cleanedInput = trim($userInput);

echo "Cleaned input: '$cleanedInput'";
```

**Output:**
```
Cleaned input: 'Username123'
```

---

### 7. **`ucwords()`**

#### Explanation:
The `ucwords()` function capitalizes the first letter of each word in a string. This is particularly useful when formatting titles or headings.

#### Real-life Example: Formatting a product title

In an e-commerce application, when displaying product titles, you may want to ensure that the first letter of each word is capitalized.

#### Code:
```php
$productTitle = "new smartphone for sale";

// Capitalize the first letter of each word
$formattedTitle = ucwords($productTitle);

echo $formattedTitle;
```

**Output:**
```
New Smartphone For Sale
```

---

### 8. **`strtolower()` and `strtoupper()`**

#### Explanation:
The `strtolower()` function converts all characters of a string to lowercase, while `strtoupper()` converts all characters to uppercase. These are useful for case-insensitive comparisons or normalizing user input.

#### Real-life Example: Case-insensitive search for product categories

In an e-commerce system, you might want to search for products in a case-insensitive manner.

#### Code:
```php
$productCategory = "Electronics";

// Convert to lowercase for case-insensitive comparison
$searchQuery = "electronics";
if (strtolower($productCategory) == strtolower($searchQuery)) {
    echo "Category found!";
} else {
    echo "Category not found.";
}
```

**Output:**
```
Category found!
```

---

### 9. **`explode()`**

#### Explanation:
The `explode()` function splits a string into an array based on a specified delimiter. It’s useful for parsing comma-separated values or processing form data.

#### Real-life Example: Parsing a list of product tags

In an e-commerce platform, products may have multiple tags, separated by commas. You can use `explode()` to convert the tags into an array.

#### Code:
```php
$productTags = "electronics, smartphone, new release";

// Convert the string to an array of tags
$tagsArray = explode(", ", $productTags);

echo "<pre>";
print_r($tagsArray);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => electronics
    [1] => smartphone
    [2] => new release
)
```

---

### 10. **`implode()`**

#### Explanation:
The `implode()` function is the opposite of `explode()`. It joins array elements into a string, using a specified delimiter. This is useful for generating CSV strings or joining array elements into a formatted string.

#### Real-life Example: Generating a CSV of product IDs

In an e-commerce system, you may want to generate a CSV list of product IDs for export.

#### Code:
```php
$productIDs = [101, 102, 103, 104];

// Convert the array of product IDs to a CSV string
$csvProductIDs = implode(", ", $productIDs);

echo "Product IDs: $csvProductIDs";
```

**Output:**
```
Product IDs: 101, 102, 103, 104
```

---

### 11. **`str_repeat()`**

#### Explanation:
The `str_repeat()` function repeats a string a specified number of times. This is useful for generating repeated patterns or formatting output.

#### Real-life Example: Generating a discount banner

In an e-commerce platform, you might want to create a discount banner with repeated symbols.

#### Code:
```php
$discountMessage = "Sale! ";

// Repeat the sale message 3 times
$banner = str_repeat($discountMessage, 3);

echo $banner;
```

**Output:**
```
Sale! Sale! Sale!
```

---

### 12. **`nl2br()`**

#### Explanation:
The `nl2br()` function converts newline characters (`\n`) to HTML line breaks (`<br>`). This is useful for formatting multi-line text in HTML output.

#### Real-life Example: Displaying product descriptions with line breaks

In an e-commerce application, you might want to format product descriptions, which include newlines.

#### Code:
```php
$productDescription = "This product is amazing.\nIt has great features.\nBuy now and enjoy!";

// Convert newlines to <br> tags
$formattedDescription = nl2br($productDescription);

echo $formattedDescription;
```

**Output:**
```
This product is amazing.<br>It has great features.<br>Buy now and enjoy!
```

---

### 13. **`substr_replace()`**

#### Explanation:
The `substr_replace()` function replaces a part of a string with another string, starting at a specific position and for a specific length. This can be useful for editing or modifying parts of a string.

#### Real-life Example: Updating part of a product SKU

In an inventory system, you might want to update the suffix of a product SKU to reflect a new model version.

#### Code:
```php
$productSKU = "A1234-XYZ";

// Replace the suffix with a new model code
$updatedSKU = substr_replace($productSKU, "ABC", -3);

echo "Updated SKU: $updatedSKU";
```

**Output:**
```
Updated SKU: A1234-ABC
```

---

### Conclusion

These are some of the most commonly used **string functions** in PHP. By leveraging these functions, you can easily manipulate and format strings for a variety of real-world applications. Whether it's validating user input, processing product data, formatting text for display, or exporting data, these functions provide the flexibility you need to handle strings efficiently.

---

### 2. **Integer**

An **integer** is a whole number (positive, negative, or zero) without a decimal point. In PHP, integers are typically used for counting, iteration, or any situation where whole numbers are needed.

#### Real-Time Example:
**E-Commerce System** – Storing the quantity of products in stock.

```php
<?php
// Integer Data Type Example
$productQuantity = 50;  // Store the number of items in stock

echo "Items in stock: " . $productQuantity;  // Output: Items in stock: 50
?>
```

In e-commerce, the `productQuantity` variable is an integer that stores how many units of a particular product are available in stock.

---

### 3. **Float (or Double)**

A **float** (also known as **double**) is a number with a decimal point. It’s used when you need to represent values like prices, measurements, or anything with decimal precision.

#### Real-Time Example:
**Shopping Cart System** – Storing the price of products.

```php
<?php
// Float Data Type Example
$productPrice = 19.99;  // Store the price of a product

echo "Product Price: $" . $productPrice;  // Output: Product Price: $19.99
?>
```

In an online shopping cart, the price of a product (e.g., `$19.99`) is stored as a float to include decimal values.

---

### 4. **Boolean**

A **boolean** represents two possible values: **true** or **false**. It’s often used for conditional checks, such as determining if something is valid or not.

#### Real-Time Example:
**User Login Verification** – Checking if the user is logged in.

```php
<?php
// Boolean Data Type Example
$isUserLoggedIn = true;  // A boolean indicating whether the user is logged in

if ($isUserLoggedIn) {
    echo "Welcome back, User!";  // Output: Welcome back, User!
} else {
    echo "Please log in to continue.";
}
?>
```

In web applications, booleans are used to check the status of various conditions, like whether the user is logged in, or if a feature is enabled or disabled.

---

### 5. **Array**

An **array** is a data structure that can store multiple values in a single variable. Arrays in PHP can be indexed (numerically) or associative (using keys).

#### Real-Time Example:
**Blog System** – Storing a list of tags associated with a blog post.

```php
<?php
// Array Data Type Example
$tags = array("PHP", "Web Development", "Programming");  // Indexed array

// Associative array example
$blogPost = array(
    "title" => "Understanding PHP Arrays",
    "author" => "John Doe",
    "tags" => array("PHP", "Arrays", "Programming")
);

echo "Tags: " . implode(", ", $tags);  // Output: Tags: PHP, Web Development, Programming
?>
```

In a blog system, an array can be used to store multiple tags related to a blog post, allowing you to categorize or group posts easily.

---

## 5.a: Array Methods

In PHP, arrays are fundamental structures used to store multiple values in a single variable. There are several array methods in PHP that help in manipulating and working with arrays effectively. Here’s a breakdown of the most commonly used array methods, explained with real-time examples to help you understand how each of them can be utilized in application development.

### 1. **`array_push()`**

#### Explanation:
The `array_push()` function adds one or more elements to the end of an array. It’s especially useful when you need to add new items to an existing array dynamically.

#### Syntax:
```php
array_push($array, $value1, $value2, ...);
```

#### Example:
```php
$fruits = ["Apple", "Banana"];
array_push($fruits, "Orange", "Mango");

print_r($fruits);
```

**Output:**
```
Array
(
    [0] => Apple
    [1] => Banana
    [2] => Orange
    [3] => Mango
)
```

#### Real-life Example: Shopping Cart in E-commerce

In an e-commerce website, when users add products to their shopping cart, we can use `array_push()` to append the product to the cart.

#### Code:
```php
// Sample shopping cart array
$cart = [
    ["id" => 101, "name" => "Laptop", "price" => 800],
    ["id" => 102, "name" => "Phone", "price" => 400]
];

// User adds a new product to the cart
$new_product = ["id" => 103, "name" => "Headphones", "price" => 100];

// Use array_push to add the new product to the cart
array_push($cart, $new_product);

// Display the updated cart
echo "<pre>";
print_r($cart);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [price] => 800
        )

    [1] => Array
        (
            [id] => 102
            [name] => Phone
            [price] => 400
        )

    [2] => Array
        (
            [id] => 103
            [name] => Headphones
            [price] => 100
        )
)
```

---

### 2. **`array_pop()`**

#### Explanation:
The `array_pop()` function removes the last element from the array. It is often used when you need to remove the most recently added item. It returns the removed element and shortens the array by one element.

#### Syntax:
```php
array_pop($array);
```

#### Example:
```php
$fruits = ["Apple", "Banana", "Orange"];
$removed = array_pop($fruits);

echo $removed; // Output: Orange
print_r($fruits);
```

**Output:**
```
Array
(
    [0] => Apple
    [1] => Banana
)
```

#### Real-life Example: Removing an item from the shopping cart

When a user removes an item from the cart, we can use `array_pop()` to remove the last item added.

#### Code:
```php
// Sample shopping cart array
$cart = [
    ["id" => 101, "name" => "Laptop", "price" => 800],
    ["id" => 102, "name" => "Phone", "price" => 400],
    ["id" => 103, "name" => "Headphones", "price" => 100]
];

// User decides to remove the last item (Headphones)
$removed_item = array_pop($cart);

// Display the removed item and the updated cart
echo "Removed Item: ";
print_r($removed_item);

echo "<pre>";
print_r($cart);
echo "</pre>";
```

**Output:**
```
Removed Item: Array
(
    [id] => 103
    [name] => Headphones
    [price] => 100
)

Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [price] => 800
        )

    [1] => Array
        (
            [id] => 102
            [name] => Phone
            [price] => 400
        )
)
```

---

### 3. **`array_shift()`**

#### Explanation:
The `array_shift()` function removes the first element from the array and shifts all other elements to the left and returns the removed element. It is useful when you need to process the first item in the array and remove it.

#### Syntax:
```php
array_shift($array);
```

#### Example:
```php
$fruits = ["Apple", "Banana", "Orange"];
$removed = array_shift($fruits);

echo $removed; // Output: Apple
print_r($fruits);
```

**Output:**
```
Array
(
    [0] => Banana
    [1] => Orange
)
```

#### Real-life Example: Order Processing Queue

In an e-commerce system, orders may be processed in a queue. `array_shift()` can be used to remove and process the first order in the queue. OR 

In a queue management system (e.g., ticket booking), you might use `array_shift()` to process the first customer in the queue.

#### Code:
```php
// Sample order queue
$order_queue = [
    ["order_id" => 1001, "product" => "Laptop", "status" => "Pending"],
    ["order_id" => 1002, "product" => "Phone", "status" => "Pending"]
];

// Process the first order in the queue
$processed_order = array_shift($order_queue);

// Display the processed order and the updated queue
echo "Processed Order: ";
print_r($processed_order);

echo "<pre>";
print_r($order_queue);
echo "</pre>";
```

**Output:**
```
Processed Order: Array
(
    [order_id] => 1001
    [product] => Laptop
    [status] => Pending
)

Array
(
    [0] => Array
        (
            [order_id] => 1002
            [product] => Phone
            [status] => Pending
        )
)
```

---

### 4. **`array_unshift()`**

#### Explanation:
The `array_unshift()` function adds one or more elements to the beginning of an array. This shifts all other existing elements to the right.

#### Syntax:
```php
array_unshift($array, $value1, $value2, ...);
```

#### Example:
```php
$fruits = ["Banana", "Orange"];
array_unshift($fruits, "Apple", "Mango");

print_r($fruits);
```

**Output:**
```
Array
(
    [0] => Apple
    [1] => Mango
    [2] => Banana
    [3] => Orange
)
```

#### Real-life Example: Adding a new review at the top of a product's reviews

In an e-commerce system, new reviews could be added to the top of a product's review array so that the most recent review appears first.

#### Code:
```php
// Sample reviews for a product
$product_reviews = [
    ["user" => "John", "review" => "Great product!", "rating" => 5],
    ["user" => "Alice", "review" => "Not bad.", "rating" => 3]
];

// New review to be added
$new_review = ["user" => "Bob", "review" => "Amazing!", "rating" => 5];

// Add the new review at the beginning
array_unshift($product_reviews, $new_review);

// Display updated reviews
echo "<pre>";
print_r($product_reviews);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [user] => Bob
            [review] => Amazing!
            [rating] => 5
        )

    [1] => Array
        (
            [user] => John
            [review] => Great product!
            [rating] => 5
        )

    [2] => Array
        (
            [user] => Alice
            [review] => Not bad.
            [rating] => 3
        )
)
```

---

### 5. **`array_merge()`**

#### Explanation:
The `array_merge()` function merges two or more arrays into one. The values from the second array are appended to the first array.

#### Syntax:
```php
array_merge($array1, $array2, ...);
```

#### Example:
```php
$array1 = ["Apple", "Banana"];
$array2 = ["Orange", "Mango"];
$merged = array_merge($array1, $array2);

print_r($merged);
```

**Output:**
```
Array
(
    [0] => Apple
    [1] => Banana
    [2] => Orange
    [3] => Mango
)
```

#### Real-life Example: Combining product data and reviews

In an e-commerce platform, you may need to merge product details with customer reviews for a product.

#### Code:
```php
// Product details
$product = ["id" => 101, "name" => "Laptop", "price" => 800];

// Reviews for the product
$reviews = [
    ["user" => "John", "review" => "Great laptop!", "rating" => 5],
    ["user" => "Alice", "review" => "Good performance.", "rating" => 4]
];

// Merging product details with reviews
$product_with_reviews = array_merge([$product], $reviews);

// Display the combined product data
echo "<pre>";
print_r($product_with_reviews);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [price] => 800
        )

    [1] => Array
        (
            [user] => John
            [review] => Great laptop!
            [rating] => 5
        )

    [2] => Array
        (
            [user] => Alice
            [review] => Good performance.
            [rating] => 4
        )
)
```

---

### 6. **`array_slice()`**

#### Explanation:
The `array_slice()` function extracts a portion of an array without modifying the original array and returns it as a new array. It’s useful for pagination, filtering, or selecting specific subsets of data.

#### Syntax:
```php
array_slice($array, $start, $length, $preserve_keys);
```

#### Example:
```php
$fruits = ["Apple", "Banana", "Orange", "Mango"];
$sliced = array_slice($fruits, 1, 2);

print_r($sliced);
```

**Output:**
```
Array
(
    [0] => Banana
    [1] => Orange
)
```

#### Real-life Example: Pagination in product listings

In an e-commerce platform, `array_slice()` can be used to display products on different pages (pagination).

#### Code:
```php
// Sample products array
$products = [
    ["id" => 101, "name" => "Laptop", "price" => 800],
    ["id" => 102, "name" => "Phone", "price" => 400],
    ["id" => 103, "name" => "Headphones", "price" => 100],
    ["id" => 104, "name" => "Smartwatch", "price" => 150],
    ["id" => 105, "name" => "Keyboard", "price" => 50]
];

// Display 2 products per page (page 1)
$page = 1;
$per_page = 2;
$offset = ($page - 1) * $per_page;
$page_products = array_slice($products, $offset, $per_page);

// Display products for the current page
echo "<pre>";
print_r($page_products);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [price] => 800
        )

    [1] => Array
        (
            [id] => 102
            [name] => Phone
            [price] => 400
        )
)
```

---

### 7. **`array_map()`**

#### Explanation:
The `array_map()` function applies a callback function to each element of an array and returns a new array with the results. It’s useful for transforming data.

#### Syntax:
```php
array_map($callback, $array);
```

#### Example:
```php
$numbers = [1, 2, 3, 4];
$squared = array_map(function($number) {
    return $number * $number;
}, $numbers);

print_r($squared);
```

**Output:**
```
Array
(
    [0] => 1
    [1] => 4
    [2] => 9
    [3] => 16
)
```

#### Real-life Example: Applying discounts to product prices

In an e-commerce platform, you can use `array_map()` to apply a discount to each product’s price.

#### Code:
```php
// Product prices
$products = [
    ["id" => 101, "name" => "Laptop", "price" => 800],
    ["id" => 102, "name" => "Phone", "price" => 400]
];

// Discount rate (20%)
$discount_rate = 0.2;

// Apply discount to each product price
$discounted_products = array_map(function($product) use ($discount_rate) {
    $product['price'] = $product['price'] * (1 - $discount_rate);
    return $product;
}, $products);

// Display discounted products
echo "<pre>";
print_r($discounted_products);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [price] => 640
        )

    [1] => Array
        (
            [id] => 102
            [name] => Phone
            [price] => 320
        )
)
```

---

### 8. **`array_filter()`**

This function filters the elements of an array using a callback function and returns a new array with elements that pass the test.

#### Syntax:
```php
array_filter($array, $callback);
```

#### Example:
```php
$numbers = [1, 2, 3, 4, 5];
$evenNumbers = array_filter($numbers, function($number) {
    return $number % 2 == 0;
});

print_r($evenNumbers);
```

**Output:**
```
Array
(
    [1] => 2
    [3] => 4
)
```

**Real-time Example:**
For a filter system in a web application (e.g., an online store), you can use `array_filter()` to show only products that match certain criteria (e.g., products with prices greater than $50).

#### Real-life Example: Filtering out unavailable products

In an e-commerce system, `array_filter()` can be used to filter out unavailable products from a list or can use to show only products that match certain criteria (e.g., products with prices greater than $50).

#### Code:
```php
// Sample product inventory
$products = [
    ["id" => 101, "name" => "Laptop", "available" => true],
    ["id" => 102, "name" => "Phone", "available" => false],
    ["id" => 103, "name" => "Headphones", "available" => true]
];

// Filter out unavailable products
$available_products = array_filter($products, function($product) {
    return $product['available'] === true;
});

// Display available products
echo "<pre>";
print_r($available_products);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => Array
        (
            [id] => 101
            [name] => Laptop
            [available] => 1
        )

    [2] => Array
        (
            [id] => 103
            [name] => Headphones
            [available] => 1
        )
)
```

---

### 9. **`array_keys()`**

#### Explanation:
The `array_keys()` function returns all the keys of an array, useful for inspecting the structure of associative arrays.

#### Syntax:
```php
array_keys($array);
```

#### Example:
```php
$fruits = ["Apple" => "Red", "Banana" => "Yellow", "Orange" => "Orange"];
$keys = array_keys($fruits);

print_r($keys);
```

**Output:**
```
Array
(
    [0] => Apple
    [1] => Banana
    [2] => Orange
)
```

**Real-time Example:**
In a product inventory system, `array_keys()` can be used to extract the names of products available in stock.

#### Real-life Example: Extracting product IDs from an inventory

You might use `array_keys()` to get a list of all product IDs in an inventory system or to extract the names of products available in stock.

#### Code:
```php
// Sample product inventory
$inventory = [
    "101" => "Laptop",
    "102" => "Phone",
    "103" => "Headphones"
];

// Get all product IDs (keys)
$product_ids = array_keys($inventory);

// Display product IDs
echo "<pre>";
print_r($product_ids);
echo "</pre>";
```

**Output:**
```
Array
(
    [0] => 101
    [1] => 102
    [2] => 103
)
```

---

### 10. **`array_search()`**

#### Explanation:
The `array_search()` function searches for a specific value in an array and returns the corresponding key if found.

#### Syntax:
```php
array_search($needle, $haystack);
```

#### Example:
```php
$fruits = ["Apple" => "Red", "Banana" => "Yellow", "Orange" => "Orange"];
$key = array_search("Yellow", $fruits);

echo $key; // Output: Banana
```

**Output:**
```
Banana
```

#### Real-life Example: Searching for a product by name
When looking for a product by name in an inventory of product details, `array_search()` can be used to find its key (e.g., product ID).

#### Code:
```php
// Sample product inventory
$inventory = [
    "101" => "Laptop",
    "102" => "Phone",
    "103" => "Headphones"
];

// Search for the product ID of "Phone"
$product_id = array_search("Phone", $inventory);

// Display the product ID
echo "Product ID of Phone: " . $product_id;
```

**Output:**
```
Product ID of Phone: 102
```

---

### 11. **`in_array()`**

#### Explanation:
The `in_array()` function checks if a value exists in an array. It returns `true` if the value is found and `false` otherwise.

#### Syntax:
```php
in_array($needle, $haystack);
```

#### Example:
```php
$fruits = ["Apple", "Banana", "Orange"];
$isPresent = in_array("Banana", $fruits);

echo $isPresent ? "Found" : "Not Found"; // Output: Found
```

**Output:**
```
Found
```

#### Real-life Example: Checking if a product is in the shopping cart
In a content management system (CMS), `in_array()` can be used to check if a user has the necessary permission to view a page (e.g., "admin" role). OR,

You can use `in_array()` to check if a specific product is already in the shopping cart before adding it again.

#### Code:
```php
// Sample shopping cart
$cart = ["Laptop", "Phone", "Headphones"];

// Check if the product "Phone" is in the cart
$is_in_cart = in_array("Phone", $cart);

// Display the result
echo $is_in_cart ? "Product is in the cart" : "Product is not in the cart";
```

**Output:**
```
Product is in the cart
```

---

### Conclusion

These are some of the most commonly used array functions in PHP, each serving different purposes when working with arrays in real-time applications. They allow developers to manipulate arrays in flexible and efficient ways, supporting various tasks like adding/removing items, filtering data, merging arrays, and more. Understanding these functions will significantly improve your ability to handle data within PHP applications.

All examples should provide a thorough understanding of how each of these array functions can be used in real-world applications like an e-commerce website.

---

## 5.b: Array Sorting Method

Array sorting is a fundamental part of working with arrays in PHP. There are several ways to sort arrays depending on the type of sorting (ascending, descending, associative arrays, etc.). Below, I'll explain the most common array sorting methods in PHP, with simple real-world examples of how they can be applied in application development.

### 1. **`sort()` - Simple Sort (Ascending Order)**

The `sort()` function sorts the values of an array in ascending order. It reorders the array without preserving the keys (the original array keys are discarded).

#### Example:
Imagine you are creating a product listing page, and you want to sort the products by price in ascending order.

```php
$products = [
    'Product A' => 20,
    'Product B' => 50,
    'Product C' => 30,
];

// Sort by values (prices) in ascending order
sort($products);

print_r($products);
```

#### Output:
```
Array
(
    [0] => 20
    [1] => 30
    [2] => 50
)
```

### 2. **`rsort()` - Reverse Sort (Descending Order)**

The `rsort()` function sorts the array in descending order. Like `sort()`, it discards the original keys.

#### Example:
In the product listing page, you may want to sort the products by price in descending order.

```php
$products = [
    'Product A' => 20,
    'Product B' => 50,
    'Product C' => 30,
];

// Sort by values (prices) in descending order
rsort($products);

print_r($products);
```

#### Output:
```
Array
(
    [0] => 50
    [1] => 30
    [2] => 20
)
```

### 3. **`asort()` - Sort While Maintaining Keys (Ascending Order)**

The `asort()` function sorts the array in ascending order by value but **keeps the keys intact**. This is useful when you need to maintain key-value relationships, like sorting a list of products by price but still keeping the product names.

#### Example:
If you want to display products sorted by price but preserve the original product names as keys:

```php
$products = [
    'Product A' => 20,
    'Product B' => 50,
    'Product C' => 30,
];

// Sort by values (prices) in ascending order, keeping the keys intact
asort($products);

print_r($products);
```

#### Output:
```
Array
(
    [Product A] => 20
    [Product C] => 30
    [Product B] => 50
)
```

### 4. **`arsort()` - Reverse Sort While Maintaining Keys (Descending Order)**

The `arsort()` function sorts the array in descending order by value but **keeps the keys intact**. This is useful for sorting with reverse priority but still needing to track the original keys.

#### Example:
Suppose you want to sort a list of items by stock quantity (in descending order) but keep track of the product names.

```php
$products = [
    'Product A' => 20,
    'Product B' => 50,
    'Product C' => 30,
];

// Sort by values (stocks) in descending order, keeping the keys intact
arsort($products);

print_r($products);
```

#### Output:
```
Array
(
    [Product B] => 50
    [Product C] => 30
    [Product A] => 20
)
```

### 5. **`ksort()` - Sort by Keys (Ascending Order)**

The `ksort()` function sorts the array by **keys** in ascending order, not by values.

#### Example:
If you have a list of user data and you want to sort them based on user IDs (keys) in ascending order:

```php
$users = [
    5 => 'John',
    1 => 'Alice',
    3 => 'Bob',
];

// Sort by keys (user IDs) in ascending order
ksort($users);

print_r($users);
```

#### Output:
```
Array
(
    [1] => Alice
    [3] => Bob
    [5] => John
)
```

### 6. **`krsort()` - Reverse Sort by Keys (Descending Order)**

The `krsort()` function sorts the array by **keys** in descending order.

#### Example:
If you want to sort the user data by descending user IDs:

```php
$users = [
    5 => 'John',
    1 => 'Alice',
    3 => 'Bob',
];

// Sort by keys (user IDs) in descending order
krsort($users);

print_r($users);
```

#### Output:
```
Array
(
    [5] => John
    [3] => Bob
    [1] => Alice
)
```

### 7. **`usort()` - Custom Sort Using a Callback Function**

The `usort()` function allows you to define a custom sorting logic via a callback function. This is helpful when you want to sort based on more complex conditions.

#### Example:
Let’s say you are working on a movie list and you want to sort movies by their release year.

```php
$movies = [
    ['title' => 'Movie A', 'year' => 2020],
    ['title' => 'Movie B', 'year' => 2018],
    ['title' => 'Movie C', 'year' => 2022],
];

// Sort movies by year (ascending order)
usort($movies, function ($a, $b) {
    return $a['year'] <=> $b['year'];  // Compare years
});

print_r($movies);
```

#### Output:
```
Array
(
    [0] => Array
        (
            [title] => Movie B
            [year] => 2018
        )

    [1] => Array
        (
            [title] => Movie A
            [year] => 2020
        )

    [2] => Array
        (
            [title] => Movie C
            [year] => 2022
        )
)
```

### 8. **`uasort()` - Custom Sort While Maintaining Keys**

The `uasort()` function allows you to perform a custom sort on an array and **maintain the keys** during sorting.

#### Example:
Let’s sort the same movie array by year while keeping the original keys:

```php
$movies = [
    1 => ['title' => 'Movie A', 'year' => 2020],
    2 => ['title' => 'Movie B', 'year' => 2018],
    3 => ['title' => 'Movie C', 'year' => 2022],
];

// Custom sort by year (ascending order), keeping keys intact
uasort($movies, function ($a, $b) {
    return $a['year'] <=> $b['year'];
});

print_r($movies);
```

#### Output:
```
Array
(
    [2] => Array
        (
            [title] => Movie B
            [year] => 2018
        )

    [1] => Array
        (
            [title] => Movie A
            [year] => 2020
        )

    [3] => Array
        (
            [title] => Movie C
            [year] => 2022
        )
)
```

### 9. **`array_multisort()` - Sort Multiple Arrays**

The `array_multisort()` function allows you to sort multiple arrays simultaneously based on the values of one or more arrays.

#### Example:
You may want to sort both an array of names and an array of corresponding scores, so that they align correctly.

```php
$names = ['Alice', 'Bob', 'Charlie'];
$scores = [85, 92, 78];

// Sort scores in descending order and reorder names accordingly
array_multisort($scores, SORT_DESC, $names);

print_r($names);
print_r($scores);
```

#### Output:
```
Array
(
    [0] => Bob
    [1] => Alice
    [2] => Charlie
)
Array
(
    [0] => 92
    [1] => 85
    [2] => 78
)
```

### Conclusion:

PHP provides a variety of array sorting functions that can be applied in different real-world application development scenarios. You can sort arrays by values, keys, in ascending or descending order, and even use custom sorting logic with a callback function. The choice of sorting function depends on your specific use case, whether you're sorting by values, keys, or need to maintain the association between keys and values.

---

### 6. **Object**

An **object** is an instance of a class in PHP. Objects are used in object-oriented programming (OOP) to store data and functions together. Objects can represent real-world entities like a "Car" or "Product".

#### Real-Time Example:
**Inventory Management System** – Storing a product’s details as an object.

```php
<?php
// Object Data Type Example

// Define a class
class Product {
    public $name;
    public $price;
    
    function __construct($name, $price) {
        $this->name = $name;
        $this->price = $price;
    }

    function displayProduct() {
        echo "Product: " . $this->name . ", Price: $" . $this->price;
    }
}

// Create an object of the Product class
$product1 = new Product("Laptop", 899.99);
$product1->displayProduct();  // Output: Product: Laptop, Price: $899.99
?>
```

In a real-world application like inventory management, objects can represent products, where each product has properties (name, price) and methods (like `displayProduct()` to show details).

---

### **Built-in methods to interact with objects**

In PHP, **Objects** are instances of **Classes** that allow you to structure your application using object-oriented principles. PHP offers a wide range of built-in methods to interact with objects. Below are some of the most commonly used methods, explained in detail with real-life examples to help you understand their usage clearly.

### 1. **`__construct()`**

#### Explanation:
The `__construct()` method is a special method in PHP that is automatically called when a new object is created. It is used to initialize the object properties.

#### Real-life Example: Creating a Product object in an e-commerce system

In an e-commerce system, we can create a `Product` class and use the constructor to set up product details when a new product object is created.

#### Code:
```php
class Product {
    public $id;
    public $name;
    public $price;

    // Constructor to initialize object properties
    public function __construct($id, $name, $price) {
        $this->id = $id;
        $this->name = $name;
        $this->price = $price;
    }

    // Method to display product details
    public function displayProduct() {
        echo "Product ID: $this->id\n";
        echo "Product Name: $this->name\n";
        echo "Product Price: $$this->price\n";
    }
}

// Creating an object of the Product class
$product1 = new Product(101, "Laptop", 800);
$product1->displayProduct();
```

**Output:**
```
Product ID: 101
Product Name: Laptop
Product Price: $800
```

---

### 2. **`__destruct()`**

#### Explanation:
The `__destruct()` method is another magic method in PHP that is automatically called when an object is destroyed or goes out of scope. This method is typically used for cleanup tasks such as closing database connections.

#### Real-life Example: Closing database connections

When a user logs out from an e-commerce platform, you can use the `__destruct()` method to close database connections and free up resources.

#### Code:
```php
class DatabaseConnection {
    public $connection;

    // Constructor to initialize the connection
    public function __construct($host, $username, $password, $dbname) {
        $this->connection = mysqli_connect($host, $username, $password, $dbname);
        if ($this->connection) {
            echo "Database connected successfully.\n";
        } else {
            echo "Failed to connect to the database.\n";
        }
    }

    // Destructor to close the connection
    public function __destruct() {
        if ($this->connection) {
            mysqli_close($this->connection);
            echo "Database connection closed.\n";
        }
    }
}

// Creating an object of the DatabaseConnection class
$db = new DatabaseConnection("localhost", "user", "password", "ecommerce_db");
unset($db); // Destructor will be called here
```

**Output:**
```
Database connected successfully.
Database connection closed.
```

---

### 3. **`__get()`**

#### Explanation:
The `__get()` method is used to access properties of an object that are not directly accessible. It is automatically called when accessing an inaccessible or non-existent property.

#### Real-life Example: Accessing a private property

In a system managing users, the `__get()` method can be used to access a private property like the `email` of a user.

#### Code:
```php
class User {
    private $email;

    public function __construct($email) {
        $this->email = $email;
    }

    // Getter method to access private email property
    public function __get($name) {
        if ($name == "email") {
            return $this->email;
        } else {
            return "Property $name does not exist!";
        }
    }
}

// Creating a User object
$user = new User("user@example.com");
echo $user->email;  // Accessing the email property using __get()
```

**Output:**
```
user@example.com
```

---

### 4. **`__set()`**

#### Explanation:
The `__set()` method is used to set values to inaccessible properties. It is automatically called when attempting to write to a non-existent or inaccessible property.

#### Real-life Example: Setting properties of a product

In an e-commerce system, you can use `__set()` to control how certain properties (like product price) are updated.

#### Code:
```php
class Product {
    private $price;

    public function __set($name, $value) {
        if ($name == "price") {
            // Ensure the price is always a positive value
            if ($value > 0) {
                $this->price = $value;
            } else {
                echo "Price must be a positive value.\n";
            }
        }
    }

    public function displayProduct() {
        echo "Product Price: $$this->price\n";
    }
}

// Creating a Product object
$product = new Product();
$product->price = 500;  // Using __set() to assign a value to the price
$product->displayProduct();
$product->price = -100;  // Invalid price
```

**Output:**
```
Product Price: $500
Price must be a positive value.
```

---

### 5. **`__isset()`**

#### Explanation:
The `__isset()` method is called when checking if a property is set using `isset()` or `empty()`. It is useful for implementing custom logic to determine if a property exists.

#### Real-life Example: Checking if a product property is set

You can use `__isset()` to check if certain properties of an object, such as a product's discount, are set before accessing them.

#### Code:
```php
class Product {
    private $properties = [];

    public function __isset($name) {
        return isset($this->properties[$name]);
    }

    public function __set($name, $value) {
        $this->properties[$name] = $value;
    }

    public function __get($name) {
        return $this->properties[$name];
    }
}

// Creating a Product object
$product = new Product();
$product->name = "Laptop";
$product->price = 800;

if (isset($product->name)) {
    echo "Product Name: " . $product->name . "\n";
}

if (!isset($product->discount)) {
    echo "Discount is not set.\n";
}
```

**Output:**
```
Product Name: Laptop
Discount is not set.
```

---

### 6. **`__call()`**

#### Explanation:
The `__call()` method is used to handle calls to undefined methods. This can be useful for implementing dynamic method handling.

#### Real-life Example: Handling dynamic method calls

In an e-commerce platform, you could use `__call()` to handle custom actions like dynamically applying discount codes for products.

#### Code:
```php
class Product {
    private $name;
    private $price;

    public function __construct($name, $price) {
        $this->name = $name;
        $this->price = $price;
    }

    // Dynamic method to handle applying discount
    public function __call($name, $arguments) {
        if ($name == "applyDiscount") {
            $discountPercentage = $arguments[0];
            $this->price = $this->price - ($this->price * ($discountPercentage / 100));
            echo "Discount applied. New price is: $$this->price\n";
        } else {
            echo "Method $name does not exist.\n";
        }
    }
}

// Creating a Product object
$product = new Product("Laptop", 1000);

// Using the dynamically called method
$product->applyDiscount(20); // Apply 20% discount
$product->nonExistentMethod(); // Non-existent method
```

**Output:**
```
Discount applied. New price is: $800
Method nonExistentMethod does not exist.
```

---

### 7. **`__toString()`**

#### Explanation:
The `__toString()` method is called when an object is treated as a string. It allows you to define a custom string representation for your object.

#### Real-life Example: Displaying product details

In an e-commerce system, you can override `__toString()` to return a formatted string representation of a product object when displayed.

#### Code:
```php
class Product {
    public $id;
    public $name;
    public $price;

    public function __construct($id, $name, $price) {
        $this->id = $id;
        $this->name = $name;
        $this->price = $price;
    }

    // Convert the object to a string
    public function __toString() {
        return "Product [ID: $this->id, Name: $this->name, Price: $$this->price]";
    }
}

// Creating a Product object
$product = new Product(101, "Laptop", 800);

// Displaying the object as a string
echo $product;
```

**Output:**
```
Product [ID: 101, Name: Laptop, Price: $800]
```

---

### 8. **`clone`**

#### Explanation:
The `clone` keyword is used to create a copy of an object. The `__clone()` method can be defined to control how the object is cloned.

#### Real-life Example: Duplicating an order

In an e-commerce system, when a user wants to duplicate an order, you can use the `clone` keyword to create a copy of an order object.

#### Code:
```php
class Order {
    public $orderId;
    public $items;

    public function __construct($orderId, $items) {
        $this->orderId = $orderId;
        $this->items = $items;
    }

    // Clone method to create a copy of the order
    public function __clone() {
        $this->orderId = "Copy of " . $this->orderId;
    }

    public function displayOrder() {
        echo "Order ID: $this->orderId\n";
        echo "Items: " . implode(", ", $this->items) . "\n";
    }
}

// Creating an Order object
$order = new Order("ORD12345", ["Laptop", "Phone"]);

// Cloning the Order object
$clonedOrder = clone $order;

$order->displayOrder();   // Original Order
$clonedOrder->displayOrder();   // Cloned Order
```

**Output:**
```
Order ID: ORD12345
Items: Laptop, Phone
Order ID: Copy of ORD12345
Items: Laptop, Phone
```

---

### Conclusion

These methods and magic methods in PHP allow you to manipulate and work with objects efficiently. They help manage object instantiation, dynamic method handling, access to private properties, and more. Using these methods can improve your ability to manage complex data and logic in your PHP applications, especially in object-oriented designs like an e-commerce system, content management system (CMS), or any system relying on objects.

---

### 7. **NULL**

The **NULL** data type represents a variable that has no value. It’s used when a variable is not initialized or when you explicitly want to clear the value of a variable.

#### Real-Time Example:
**User Profile System** – A user might not have a middle name, so the middle name field can be set to `NULL`.

```php
<?php
// NULL Data Type Example
$middleName = NULL;  // The middle name is not set for the user

if ($middleName === NULL) {
    echo "Middle name is not provided.";
} else {
    echo "Middle name: " . $middleName;
}
?>
```

In user profile systems, you might encounter situations where certain data (like a middle name or an address line) is optional, and `NULL` can be used to signify that no data has been provided.

---

### Summary of Data Types:

- **String:** Textual data (e.g., names, emails).
- **Integer:** Whole numbers (e.g., product quantities, user age).
- **Float:** Decimal numbers (e.g., prices, ratings).
- **Boolean:** True or False (e.g., user login status, feature availability).
- **Array:** List of values (e.g., tags, product categories).
- **Object:** Instance of a class with properties and methods (e.g., a product, a user).
- **NULL:** A variable with no value (e.g., an empty field in a form).

These data types are fundamental in PHP and widely used in real-time applications to handle different kinds of data, such as user input, product details, and system settings.

