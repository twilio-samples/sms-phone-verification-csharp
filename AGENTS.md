# Build a User Registration System with SMS Phone Verification

An ASP.NET Core MVC application demonstrating user registration, authentication, and SMS phone verification using Twilio Verify.

## Commands

```bash
# Install dependencies
dotnet build

# Install EF Core CLI (if not already installed)
dotnet tool install --global dotnet-ef

# Create database
dotnet ef database update

# Run
dotnet run

# Test
dotnet test
```

## Environment Variables

Copy `appsettings.Development.json.example` to `appsettings.Development.json`. Never commit `appsettings.Development.json`.

```bash
cp appsettings.Development.json.example appsettings.Development.json
```

| Variable | Where to find | Format |
| -------- | ------------- | ------ |
| `Twilio:AccountSid` | [Console](https://console.twilio.com) homepage | Starts with `AC` |
| `Twilio:AuthToken` | Console homepage → click to reveal | 32-char string. Treat as a password. |
| `Twilio:VerificationSid` | Console → Verify → Services | Starts with `VA` |

## Project Structure

- `Program.cs` — Application entry point
- `Startup.cs` — Service configuration and middleware pipeline
- `Controllers/` — MVC controllers for home and API endpoints
- `Areas/Identity/Pages/Account/` — Razor Pages for authentication (Register, Login, Verify)
- `Views/` — Razor views and layout templates
- `wwwroot/css/paste.css` — Twilio Paste design system styling
- `Models/ApplicationUser.cs` — User model with phone verification
- `Services/Verification.cs` — Twilio Verify API integration
- `Data/ApplicationDbContext.cs` — Entity Framework database context

## Agent Boundaries

**Always:**
- Confirm `appsettings.Development.json` is configured before running any command
- Use the Environment Variables section to guide the user to each credential — don't ask them to find values without direction
- Confirm the database is created (`dotnet ef database update`) before running the app
- Confirm the app is running before asking the user to test it

**Never:**
- Run the app with missing or placeholder credentials
- Hardcode credentials or phone numbers in source files
- Skip the `cp appsettings.Development.json.example appsettings.Development.json` step

## Verify It's Working

1. Open http://localhost:5000 and register a new account with your phone number
2. Submit the registration form — you should receive an SMS with a verification code
3. Enter the code on the verify page — you should see the verified dashboard

## Twilio Resources

- [Twilio Console](https://console.twilio.com) — credentials, phone numbers, webhook configuration
- [Twilio Verify Documentation](https://www.twilio.com/docs/verify)
- [Twilio C# SDK](https://www.twilio.com/docs/libraries/reference/twilio-csharp)
