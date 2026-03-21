# PumpIron Site

> Multi-page PHP website for a gym brand that presents plans and gym locations, answers common questions, and stores payment requests and help messages in a MySQL database.

## 📚 Academic Context

| | |
|---|---|
| **Degree** | BSc in Computer Science @ University of Madeira |
| **Course** | Web Development |
| **Year** | 2022/23 |

## 🛠️ Technologies & Concepts

- `PHP` for server-rendered pages, form handling, and CRUD operations
- `MySQL` with `mysqli` for persistence
- `HTML` and `CSS` for page structure and styling
- `JavaScript` + `jQuery` for client-side form validation
- `Bootstrap 5` for layout, components, and responsive styling
- Multi-page website architecture with reusable includes (`logo.php`, `footer.php`)
- Form validation, confirmation-step workflows, and database-backed create/read/update/delete operations

## 🏗️ Architecture / Approach

- The project is organized as a plain PHP site under `PumpIron-Site/`, without a framework.
- Public-facing pages include `index.php`, `gymplans.php`, `gymsnearyou.php`, `faq.php`, `payment.php`, and `help.php`.
- Both the payment flow and the help flow use a two-step process: the user submits a form, reviews the data in a confirmation page (`detailsPayment.php` / `detailsHelp.php`), and only then persists it to the database.
- Database access is handled with small procedural PHP scripts in `PumpIron-Site/db/`, covering create, list, edit, and delete operations for the `payment` and `help_message` tables.
- Shared UI elements are extracted into `logo.php` and `footer.php`, while `styles.css` defines the custom theme and validation states.

## 🚀 How to Run

1. Make sure you have a local PHP + MySQL environment available, such as `XAMPP`, `MAMP`, or another Apache/PHP stack.
2. Place the `PumpIron-Site` folder inside your web server document root, or serve it from a local PHP-enabled web server.
3. Create a MySQL database named `pumpiron`, which is the database configured in `PumpIron-Site/db/constants.php`.
4. Create the tables expected by the code:
   - `payment` with fields `id`, `card_number`, `street_address`, `country`, `city`, `province`, `postal`
   - `help_message` with fields `id`, `name`, `email`, `gym`, `message`
   The repository does not include a `.sql` schema file, so this step has to be done manually.
5. Adjust `PumpIron-Site/db/constants.php` if your MySQL credentials are different from the default local setup:

```php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "pumpiron";
```

6. Start Apache and MySQL, then open the site in the browser through your local server, for example:

```text
http://localhost/PumpIron-Site/index.php
```

7. To access the database-backed admin-style listing pages used in the assignments, open:
   - `db/AllPayment.php`
   - `db/AllHelpMessage.php`

## 📝 Notes

- This work was developed in the BSc in Computer Science at the University of Madeira during an Erasmus period at the University of Maribor.
- This project was developed as a sequence of weekly Web Development assignments and later brought together into one gym-themed website.
- It combines informational pages with interactive database-backed flows for payments and help messages.
- The payment and help sections use a confirmation step before saving data, reinforcing form handling and multi-page interaction patterns.
- Local execution requires creating the `pumpiron` database and the two tables used by the PHP scripts.
