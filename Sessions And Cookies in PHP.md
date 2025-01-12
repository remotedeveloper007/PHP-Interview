### What are Sessions in PHP?

In PHP, **sessions** are a way to store user-specific information across multiple pages during a user's visit to a website. A session allows you to keep track of the user's data, such as login status, preferences, or shopping cart items, while they navigate between different pages.

Unlike cookies, which are stored on the user's browser, sessions store data on the server, making it more secure because users cannot easily manipulate the data.

### Where are Sessions Stored in PHP?

In PHP, session data is typically stored on the **server** by default. PHP creates a unique session ID for each user and stores the session data in a file on the server. The location of the session files depends on the server's configuration.

- **Session ID:** This is stored in the user's browser as a cookie (by default) or passed via the URL. It helps the server associate the user with their session data.
- **Session Data:** This is stored on the server, often in a directory defined by the `session.save_path` directive in the `php.ini` file (e.g., `/var/lib/php/sessions` on Linux systems).

### How do Sessions Work in PHP?

1. **Starting a Session:**
   To start using sessions, you need to call the `session_start()` function at the beginning of your PHP script. This function checks if a session already exists for the user and retrieves the associated session data from the server.

2. **Storing Data in a Session:**
   Once the session is started, you can store data using the `$_SESSION` superglobal array. This data will be available throughout the user's visit to the website.

3. **Accessing Session Data:**
   You can access or modify the session data on any page as long as the session is started.

4. **Ending the Session:**
   When the user logs out or the session is no longer needed, you can call `session_destroy()` to end the session, which will delete the session data from the server.

### Real-Time Example: Online Shopping Cart

Let’s walk through a simple example of how sessions are used in an **online shopping cart** application.

1. **Starting the Session** (In `cart.php`):
   This page allows the user to add items to their shopping cart.

   ```php
   <?php
   session_start(); // Start the session to store and retrieve cart data

   // Check if an item is added to the cart
   if (isset($_GET['add'])) {
       $item = $_GET['add']; // Get the item to be added
       
       // Add the item to the cart session array
       if (!isset($_SESSION['cart'])) {
           $_SESSION['cart'] = []; // Initialize cart if it doesn't exist
       }
       $_SESSION['cart'][] = $item; // Add the item to the cart array
       echo "Item added to cart: " . $item;
   }
   ?>
   <a href="cart.php?add=apple">Add Apple to Cart</a><br>
   <a href="cart.php?add=banana">Add Banana to Cart</a><br>
   ```

2. **Viewing the Cart** (In `view_cart.php`):
   This page allows the user to view the items they have added to their cart.

   ```php
   <?php
   session_start(); // Start the session to access cart data

   // Check if there are items in the cart
   if (isset($_SESSION['cart']) && !empty($_SESSION['cart'])) {
       echo "Your shopping cart contains:<br>";
       foreach ($_SESSION['cart'] as $item) {
           echo $item . "<br>";
       }
   } else {
       echo "Your shopping cart is empty.";
   }
   ?>
   ```

3. **Clearing the Cart (Logging Out or Ending the Session)** (In `logout.php`):

   ```php
   <?php
   session_start(); // Start the session
   session_destroy(); // Destroy the session to clear the cart
   echo "You have been logged out, and your cart is empty.";
   ?>
   ```

### Explanation of the Example:

1. **Adding Items to the Cart:**
   - When the user clicks on "Add Apple to Cart" or "Add Banana to Cart", it adds the item to the `$_SESSION['cart']` array.
   - The session data persists as long as the session is active, allowing the user to add multiple items.

2. **Viewing the Cart:**
   - On the `view_cart.php` page, the session data is retrieved, and the items in the cart are displayed.

3. **Logging Out/Clearing the Cart:**
   - When the user logs out, the session is destroyed with `session_destroy()`, and the cart is cleared.

### Key Points to Remember:

- **Session ID:** PHP generates a unique session ID for each user to identify their session data.
- **Session Storage:** The actual session data (such as items in the cart) is stored on the server.
- **Secure Data:** Unlike cookies, session data cannot be easily modified by the user because it is stored on the server.
- **Session Start:** Always call `session_start()` before accessing or storing session data.
- **Session Destroy:** Use `session_destroy()` when you want to end the session and clear the data.

In real-world applications, sessions are used for a variety of purposes, such as tracking logged-in users, saving user preferences, and managing shopping carts, making them an essential feature of dynamic web development.

---

### Default Session Time and Path in PHP

In PHP, sessions are used to store data for a user across multiple pages during a visit. When a session is started, PHP creates a session ID, which it sends to the user's browser in the form of a cookie (by default). This session ID is used to track the user’s session and associate them with the correct session data on the server.

### Default Session Time (Expiration)

The default session timeout in PHP is controlled by the `session.gc_maxlifetime` directive in the `php.ini` file. This value specifies the number of seconds a session can be inactive before it is considered garbage and can be cleared.

By default, PHP sets this value to **1440 seconds**, which equals **24 minutes**. This means if a session is inactive for 24 minutes, it will expire and be destroyed.

### Default Session Path

The session path is controlled by the `session.save_path` directive in PHP. This path determines where session data (like variables and session state) is stored on the server.

By default:
- PHP stores session data in a temporary directory on the server (like `/tmp` or `C:\Windows\Temp` depending on the operating system).

You can change both the session timeout and path to customize session behavior in your PHP application.

### How to Change Session Timeout and Path in PHP?

To change the session expiration time and path, you can either:
1. Modify the `php.ini` file (global settings).
2. Use `ini_set()` to set the values dynamically at runtime within your PHP script.

Let's go through both methods with examples.

---

### 1. **Changing Session Timeout**

The session timeout (expiration) time can be changed using the `session.gc_maxlifetime` directive.

#### Example 1: Changing Session Timeout in `php.ini`

In the `php.ini` configuration file, find the following setting and modify it:

```ini
session.gc_maxlifetime = 3600  ; Set session expiration time to 1 hour (3600 seconds)
```

This will make the session expire after **1 hour** of inactivity.

#### Example 2: Changing Session Timeout Using `ini_set()` in PHP

If you don’t have access to the `php.ini` file or want to change the session timeout for a specific script, you can set it dynamically using `ini_set()`.

```php
<?php
// Set session timeout to 1 hour (3600 seconds) before starting the session
ini_set('session.gc_maxlifetime', 3600);

// Start the session
session_start();

// Store some session data
$_SESSION['username'] = 'john_doe';

// Example: Access the session data
echo "User: " . $_SESSION['username'];  // Output: User: john_doe
?>
```

In this example:
- We set the session timeout to **3600 seconds (1 hour)**.
- The session will expire after 1 hour of inactivity, even if the user doesn't do anything.

---

### 2. **Changing Session Path**

To change the session storage path (where session files are saved), you can modify the `session.save_path` directive. By default, PHP uses the system's temporary folder, but you can change it to a custom directory.

#### Example 1: Changing Session Path in `php.ini`

In the `php.ini` configuration file, you can change the session storage directory:

```ini
session.save_path = "/path/to/your/custom/directory"
```

Ensure the specified directory has the appropriate write permissions.

#### Example 2: Changing Session Path Using `ini_set()` in PHP

You can also set a custom session path at runtime using the `ini_set()` function, like this:

```php
<?php
// Set a custom session save path
ini_set('session.save_path', '/path/to/your/custom/directory');

// Start the session
session_start();

// Store some session data
$_SESSION['username'] = 'john_doe';

// Example: Access the session data
echo "User: " . $_SESSION['username'];  // Output: User: john_doe
?>
```

In this example:
- We set the session path to a custom directory (`/path/to/your/custom/directory`).
- When the session is started, PHP will store the session data in the specified directory.

---

### 3. **How Session Works with the Default Settings (Real-Time Example)**

Let's look at a real-time example of a simple login system. The session settings (timeout and path) are important to ensure the session persists for a certain duration and is stored securely.

#### Example: Session in a Login System

```php
<?php
// Set session timeout and path
ini_set('session.gc_maxlifetime', 3600);  // Set session to 1 hour
ini_set('session.save_path', '/path/to/sessions');  // Custom session storage path

session_start();

// Check if the user is already logged in
if (isset($_SESSION['logged_in']) && $_SESSION['logged_in'] == true) {
    echo "Welcome back, " . $_SESSION['username'];  // Output: Welcome back, john_doe
} else {
    // Simulate a login process
    $_SESSION['username'] = 'john_doe';
    $_SESSION['logged_in'] = true;
    echo "You are now logged in.";
}
?>
```

In this example:
1. **Session Timeout**: We set the session timeout to **1 hour** using `ini_set()`. If the user is inactive for 1 hour, the session will expire.
2. **Session Path**: We set a custom session storage path where the session data will be saved.
3. **Login Simulation**: The script checks if the user is logged in by verifying the session data. If not, the script logs in the user and stores session information (`username` and `logged_in`).

#### Key Points for Real-Time Applications:

- **Session Timeout**: For security reasons, it’s common to have session timeouts in web applications. For example, an e-commerce site might expire sessions after 30 minutes of inactivity to protect user accounts.
- **Session Path**: In certain environments (like shared hosting or cloud servers), you may need to change the session path to a custom directory where PHP has proper write access, especially for performance or security reasons.
- **Custom Path and Timeout**: Some applications, such as online banking or e-commerce sites, might have longer session lifetimes (e.g., 1 hour or more) to allow users to complete tasks. At the same time, sensitive applications might set a shorter session timeout (e.g., 15 minutes) for security.

---

### Conclusion

1. **Default Session Timeout** is 1440 seconds (24 minutes) in PHP.
2. **Default Session Path** is typically the system’s temporary directory (like `/tmp` in Linux or `C:\Windows\Temp` in Windows).
3. **Changing Session Timeout**: You can change the session timeout using `session.gc_maxlifetime` in the `php.ini` file or `ini_set()` in your PHP code.
4. **Changing Session Path**: You can change the session storage path using `session.save_path` in `php.ini` or `ini_set()` in PHP.

These settings are important in real-time applications like login systems, shopping carts, or any system that needs to manage user data securely and efficiently over time.


---

### What are Cookies in PHP?

A **cookie** is a small piece of data that is stored on the user's **browser** and sent to the server with every subsequent request. Cookies are used to store information about the user, such as preferences, login information, or tracking details. Cookies can persist even after the user closes the browser, unlike session data, which is stored on the server and typically expires when the session ends.

In PHP, cookies allow you to store data on the client side and retrieve it on future visits.

### How Cookies are Used in PHP?

Cookies in PHP are set using the `setcookie()` function, and their values can be accessed through the `$_COOKIE` superglobal array. A cookie is stored in the user's browser until it expires, or the user deletes it.

#### Steps for Using Cookies:

1. **Setting a Cookie:**
   To set a cookie, you use the `setcookie()` function. This function must be called before any output (like HTML or echo statements) is sent to the browser.

2. **Accessing a Cookie:**
   You can access the value of a cookie using the `$_COOKIE` superglobal array.

3. **Deleting a Cookie:**
   To delete a cookie, you can set its expiration date to a time in the past.

### Syntax of `setcookie()`:
```php
bool setcookie ( string $name , string $value = "" , int $expire = 0 , string $path = "" , string $domain = "" , bool $secure = false , bool $httponly = false )
```

- **name**: The name of the cookie.
- **value**: The value stored in the cookie.
- **expire**: The expiration date of the cookie in Unix timestamp format. Default is 0, which means the cookie will expire when the browser is closed.
- **path**: The path where the cookie is available. Default is "/" (root of the domain).
- **domain**: The domain for which the cookie is available. Default is the current domain.
- **secure**: If set to true, the cookie will only be sent over HTTPS.
- **httponly**: If set to true, the cookie cannot be accessed through JavaScript.

### Example of Cookies in PHP: Remembering User Preferences

Let’s walk through a real-world example where a website remembers a user's theme preference (light or dark mode) using cookies.

1. **Setting a Cookie to Remember Theme Preference (In `set_theme.php`):**
   In this example, when the user selects a theme (light or dark), the website stores their preference in a cookie. 

   ```php
   <?php
   // Check if the theme is selected from the form
   if (isset($_POST['theme'])) {
       $theme = $_POST['theme'];
       
       // Set a cookie that expires in 30 days
       setcookie('theme', $theme, time() + (30 * 24 * 60 * 60), '/'); // Expires in 30 days

       // Inform the user that the theme preference has been saved
       echo "Theme preference saved!";
   }
   ?>

   <!-- HTML Form to Choose Theme -->
   <form method="post" action="set_theme.php">
       <label>Select Theme:</label>
       <input type="radio" name="theme" value="light" <?php if (isset($_COOKIE['theme']) && $_COOKIE['theme'] == 'light') echo 'checked'; ?>> Light
       <input type="radio" name="theme" value="dark" <?php if (isset($_COOKIE['theme']) && $_COOKIE['theme'] == 'dark') echo 'checked'; ?>> Dark
       <br>
       <input type="submit" value="Save Theme">
   </form>
   ```

2. **Accessing the Cookie and Displaying the Correct Theme (In `index.php`):**
   On the homepage (or any other page), the website will check if the "theme" cookie is set and apply the corresponding theme.

   ```php
   <?php
   // Check if the theme cookie exists
   if (isset($_COOKIE['theme'])) {
       $theme = $_COOKIE['theme'];
   } else {
       $theme = 'light'; // Default theme if no cookie is set
   }
   ?>

   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Theme Preference</title>

       <!-- Apply theme style based on cookie value -->
       <style>
           body {
               background-color: <?php echo ($theme == 'dark') ? '#333' : '#fff'; ?>;
               color: <?php echo ($theme == 'dark') ? '#fff' : '#000'; ?>;
               font-family: Arial, sans-serif;
               text-align: center;
               padding: 50px;
           }
       </style>
   </head>
   <body>
       <h1>Welcome to Our Website!</h1>
       <p>Your selected theme is: <?php echo ucfirst($theme); ?></p>
       <a href="set_theme.php">Change Theme</a>
   </body>
   </html>
   ```

3. **Deleting the Cookie (In `delete_theme.php`):**
   If the user wants to reset their theme, the cookie can be deleted by setting its expiration date to a time in the past.

   ```php
   <?php
   // Delete the theme cookie by setting its expiration to the past
   setcookie('theme', '', time() - 3600, '/');
   echo "Theme preference has been reset.";
   ?>
   ```

### Explanation of the Example:

1. **Setting the Cookie:**
   - When the user selects a theme (light or dark), the form sends the theme value to `set_theme.php`.
   - In `set_theme.php`, the `setcookie()` function saves the user's theme preference in a cookie. The cookie will expire in 30 days, meaning it will persist across sessions until it expires or is deleted.

2. **Accessing the Cookie:**
   - On the homepage (`index.php`), we check if the "theme" cookie is set using `isset($_COOKIE['theme'])`. If it is, the page applies the corresponding theme (light or dark) by modifying the CSS.

3. **Deleting the Cookie:**
   - In `delete_theme.php`, the cookie is deleted by setting its expiration date to a time in the past (using `time() - 3600`).

### Key Points to Remember:

- **Cookies Are Stored on the Client-Side:** Unlike sessions, which are stored on the server, cookies are stored on the user's browser. This means the data is accessible even if the user navigates away from the site or closes their browser.
  
- **Expiry Time:** If you don't set an expiry time, the cookie will last only for the duration of the user's session (until the browser is closed).

- **Security Considerations:**
  - Cookies can be tampered with by users, so sensitive data should never be stored in cookies without encryption.
  - The `secure` flag should be used for cookies that should only be sent over HTTPS connections.
  - The `httponly` flag can be used to prevent cookies from being accessed via JavaScript, reducing the risk of cross-site scripting (XSS) attacks.

### Conclusion:

Cookies in PHP provide a way to store data on the client side for later use. In our example, we demonstrated how to use cookies to remember a user's theme preference. Cookies are useful for scenarios like remembering user preferences, login states, or even tracking user behavior across sessions. However, because they are stored on the client's device, care should be taken when storing sensitive information in cookies.
