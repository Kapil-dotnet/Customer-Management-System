# 🧑‍💼 Customer Management System

A customer records management web application built with ASP.NET Core MVC, Entity Framework Core, and Microsoft SQL Server.

The application supports customer record operations, user authentication, email confirmation and password reset flows, and sample customer data through Entity Framework Core migrations.

## 🚀 Features

- ➕ **Add Customers:** Create customer records with an ID, name, balance, city, and status.
- 📋 **View Customers:** Display active customer records in a table.
- 👁️ **View Customer Details:** View an individual customer's details.
- ✏️ **Edit Customers:** Update customer information.
- 🗑️ **Soft Delete:** Mark a customer inactive instead of permanently removing the database row.
- 🔐 **User Authentication:** Register, log in, and log out using ASP.NET Core Identity.
- ✉️ **Email Confirmation:** Send account confirmation links by email.
- 🔑 **Password Reset:** Send password reset links to registered users.
- 🌐 **External Login:** Google and Facebook login providers are configured; they require valid credentials.
- 🌱 **Sample Data:** An Entity Framework Core migration adds four sample customers.
- 🧩 **Data Access Layer:** `ICustomerDAL` defines customer operations, and `CustomerSqlDAL` is the active SQL Server implementation.

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | C# |
| Framework | ASP.NET Core MVC |
| Target Framework | .NET 10 |
| Database | Microsoft SQL Server |
| Database Context and Data Access | Entity Framework Core, `MVCCoreDbContext`, `ICustomerDAL` |
| Authentication | ASP.NET Core Identity |
| Email | MailKit, MimeKit, Gmail SMTP |
| Frontend | Razor Views, HTML, CSS, Bootstrap |
| Client-side Libraries | jQuery, jQuery Validation |
| Library Management | LibMan |
| Version Control | Git, GitHub |

## 📁 Project Structure

```text
Customer-Management-System/
├── README.md
└── MVCDHProject/
    ├── Controllers/
    │   ├── AccountController.cs
    │   ├── CustomerController.cs
    │   ├── ErrorController.cs
    │   └── HomeController.cs
    ├── Migrations/
    ├── Models/
    │   ├── Customer.cs
    │   ├── ICustomerDAL.cs
    │   ├── CustomerSqlDAL.cs
    │   ├── CustomerXmlDAL.cs
    │   ├── CustomerAccessDAL.cs
    │   ├── CustomerOracleDAL.cs
    │   └── MVCCoreDbContext.cs
    ├── Views/
    │   ├── Account/
    │   ├── Customer/
    │   ├── Error/
    │   ├── Home/
    │   └── Shared/
    ├── wwwroot/
    ├── Customer.xml
    ├── libman.json
    ├── appsettings.json
    ├── Program.cs
    └── MVCDHProject.csproj
```

`Program.cs` registers `CustomerSqlDAL`. `CustomerXmlDAL` is an alternate implementation; the Access and Oracle DAL classes are placeholders and are not active implementations.

## ⚙️ Installation and Setup

### 1. Prerequisites

Make sure the following tools are installed:

- 💻 Visual Studio with the ASP.NET and web development workload
- 🧰 .NET 10 SDK
- 🗄️ Microsoft SQL Server
- 🔧 Git

### 2. Clone the Repository

```bash
git clone https://github.com/Kapil-dotnet/Customer-Management-System.git
cd Customer-Management-System
```

### 3. Configure the Database

Open `MVCDHProject/appsettings.json` and update the `ConStr` connection string for your SQL Server instance.

The sample connection string uses Windows Integrated Security and a computer-specific SQL Server name. Replace the server name with the one configured on your computer.

### 4. Apply Database Migrations

In Visual Studio, open **Tools → NuGet Package Manager → Package Manager Console** and run:

```powershell
Update-Database
```

This applies the existing migrations, including the migration that inserts sample customer records.

### 5. Run the Application

Open `MVCDHProject/MVCDHProject.csproj` in Visual Studio and press **F5** or click **Start**.

### 6. Register and Log In

Register an account and log in to use the customer management actions.

Email confirmation, password reset, Google login, and Facebook login need valid credentials. Keep credentials private; do not commit them to GitHub.

### 7. Publish the Application

To create a Release build, open a terminal in the `MVCDHProject` directory and run:

```bash
dotnet publish -c Release
```

## 🧾 Customer Pages

| Page | Route | Description |
|---|---|---|
| Customer List | `/Customer/DisplayCustomers` | Displays active customer records |
| Customer Details | `/Customer/DisplayCustomer?Custid=101` | Displays one customer's details |
| Add Customer | `/Customer/AddCustomer` | Opens the customer creation form |
| Edit Customer | `/Customer/EditCustomer?Custid=101` | Opens the customer edit form |
| Register | `/Account/Register` | Creates an application account |
| Login | `/Account/Login` | Signs in to the application |
| Forgot Password | `/Account/ForgotPassword` | Starts the password reset flow |

The customer list and details actions allow anonymous access. The add, edit, and delete actions require login.

## 🗃️ Database Migrations and Seeding

Entity Framework Core migrations manage the database schema. The `SeedData` migration inserts four sample customers.

To apply the existing migrations, run:

```powershell
Update-Database
```

## 🧪 Application Verification

After starting the application:

1. Open `/Customer/DisplayCustomers` and check that sample customer records appear.
2. Register and log in.
3. Add a customer and check that it appears in the list.
4. Edit a customer and verify the updated details.
5. Use the Delete action and confirm that the customer becomes inactive and disappears from the active list.
6. Test email and external login features only after configuring valid credentials.

## 🔐 Security and Best Practices

- 🔑 Never commit Gmail App Passwords, OAuth client secrets, or database passwords.
- 🧪 Use fictional customer data for demonstrations.
- 🗄️ Update the computer-specific SQL Server name for each development computer.
- 👁️ Customer list and details actions currently allow anonymous access.
- ⚠️ The current Delete link uses a GET request. Before production use, change it to a POST form with anti-forgery validation.
- 🧩 Only the SQL Server DAL is registered for use. The Access and Oracle DAL classes are placeholders.

## 🔮 Future Improvements

- ✅ Add server-side validation to customer forms.
- 🛡️ Require login to view customer records if the data is private.
- 🔒 Change the Delete action to POST with anti-forgery validation.
- ⚙️ Move email and OAuth credentials to secure configuration.
- 🧩 Complete or remove unused Access and Oracle DAL placeholders.
- 🔍 Add customer search, sorting, and pagination.
- ☁️ Deploy the application with a hosted database.

## 👨‍💻 Author

GitHub: [Kapil-dotnet](https://github.com/Kapil-dotnet)  
LinkedIn: [Kapil Rathod](https://www.linkedin.com/in/kapil-rathod-dotnet/)

Built with C#, ASP.NET Core MVC, Entity Framework Core, and Microsoft SQL Server.
