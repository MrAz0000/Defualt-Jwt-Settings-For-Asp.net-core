---

```markdown
# Default JWT Settings for ASP.NET Core

A minimal and clean setup for implementing **JWT authentication** in an ASP.NET Core Web API project using `Microsoft.AspNetCore.Authentication.JwtBearer`.

This repository serves as a boilerplate or starting point for any project that requires JWT authentication.

---

## 🔧 Features

- JWT Bearer Authentication Setup
- `Program.cs` configuration
- Token validation settings
- Supports environment-based secret keys (via `appsettings.json`)
- Easy to customize and extend

---

## 🧠 How It Works

1. JWT settings are configured via `appsettings.json`.
2. Middleware in `Program.cs` sets up the JWT Bearer authentication.
3. The API can now authenticate and authorize users using JWT access tokens.

---

## 📂 Project Structure

```

📁 Default-Jwt-Settings-For-Asp.net-core/
│
├── Controllers/
│   └── AuthController.cs        # (Optional) Entry point for testing JWT token generation
│
├── appsettings.json            # Contains JWT configuration values
├── Program.cs                  # Core JWT authentication setup
├── Properties/
│
└── Default-Jwt-Settings-For-Asp.net-core.csproj

````

---

## ⚙️ JWT Setup Overview (`Program.cs`)

```csharp
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options =>
    {
        options.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = builder.Configuration["Jwt:Issuer"],
            ValidAudience = builder.Configuration["Jwt:Audience"],
            IssuerSigningKey = new SymmetricSecurityKey(
                Encoding.UTF8.GetBytes(builder.Configuration["Jwt:Key"]))
        };
    });

app.UseAuthentication();
app.UseAuthorization();
````

> ✅ Make sure you have the following section in your `appsettings.json`:

```json
"Jwt": {
  "Key": "your_secret_key_here",
  "Issuer": "your_app",
  "Audience": "your_users"
}
```

---

## ▶️ Running the Project

1. Clone the repo

   ```bash
   git clone https://github.com/MrAz0000/Defualt-Jwt-Settings-For-Asp.net-core.git
   ```

2. Open in Visual Studio or run:

   ```bash
   dotnet run
   ```

3. Use Swagger or Postman to test protected endpoints (if any are added).

---

## 🔐 Token Generation

This template **does not** include token generation logic by default. You can add a controller like `AuthController.cs` to issue JWTs using `JwtSecurityTokenHandler`.

---

## 📌 Notes

* You can extend this setup with role-based authorization, refresh tokens, or identity integration.
* Always store secret keys securely (use user-secrets, environment variables, or Azure Key Vault in production).

---

## 📃 License

This project is open-source and free to use.

---

## 🤝 Contributing

Feel free to fork this repo and submit a PR with improvements or updates!

```

---

Would you like me to also include a basic `AuthController.cs` with JWT token generation?
```
