```
Default-Jwt-Settings-For-Asp.net-core/
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
> Make sure you have the following section in your `appsettings.json`:

```json
"Jwt": {
  "Key": "your_secret_key_here",
  "Issuer": "your_app",
  "Audience": "your_users"
}
```

---

## Required NuGetPackage 
Download :
```
  Microsoft.AspNetCore.Authentication.JwtBearer
```
