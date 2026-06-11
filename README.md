<a href="https://www.twilio.com">
<img src="https://static0.twilio.com/marketing/bundles/marketing/img/logos/wordmark-red.svg" alt="Twilio" width="250" />
</a>

# SMS Phone Verification with ASP.NET Core

![.NET Core Build](https://github.com/TwilioDevEd/verify-v2-quickstart-csharp/workflows/dotNETCore/badge.svg)

An ASP.NET Core MVC application demonstrating user registration, authentication, and SMS phone verification using Twilio Verify API.

## Prerequisites

- [.NET SDK 10.0+](https://dotnet.microsoft.com/download)
- A Twilio account - [sign up for free](https://www.twilio.com/try-twilio)

## Setup

### 1. Clone and Navigate

```bash
git clone https://github.com/twilio-samples/sms-phone-verification-csharp.git
cd sms-phone-verification-csharp/VerifyV2Quickstart
```

### 2. Install Dependencies

```bash
dotnet build
```

### 3. Install Entity Framework CLI (if not already installed)

```bash
dotnet tool install --global dotnet-ef
```

### 4. Configure Twilio Credentials

Copy the example config file and add your credentials:

```bash
cp appsettings.Development.json.example appsettings.Development.json
```

Open `appsettings.Development.json` and replace the placeholder values with your actual credentials:

| Config Value | Description | Where to Find |
| :----------- | :---------- | :------------ |
| **Account SID** | Your primary Twilio account identifier | [Console homepage](https://www.twilio.com/console) |
| **Auth Token** | Used to authenticate API requests | [Console homepage](https://www.twilio.com/console) (click to reveal) |
| **Verification SID** | Verify Service identifier | [Verify Services](https://www.twilio.com/console/verify/services) (starts with `VA`) |

### 5. Create Database

```bash
dotnet ef database update
```

### 6. Run the Application

```bash
dotnet run
```

Navigate to [http://localhost:5000](http://localhost:5000)

## Usage

1. **Register**: Create a new account with username, password, and phone number
2. **Receive Code**: Get a verification code via SMS or voice call
3. **Verify**: Enter the 6-digit code to verify your phone number
4. **Access Dashboard**: Once verified, access the secure dashboard

## Docker Support

Build and run with Docker:

```bash
# Make sure appsettings.Development.json is configured
docker-compose up
```

## Running Tests

```bash
dotnet test
```

## Troubleshooting

### EF Core Tools Version Error

If you get an error like "You must install or update .NET to run this application" when running `dotnet ef`:

```bash
# Uninstall and reinstall EF Core tools to match your .NET version
dotnet tool uninstall --global dotnet-ef
dotnet tool install --global dotnet-ef
```

### Framework Version Mismatch

This project targets .NET 10.0. If you have a different .NET version installed:
- Check your version: `dotnet --version`
- Download .NET 10.0 from [dotnet.microsoft.com/download](https://dotnet.microsoft.com/download)

## Project Structure

```
VerifyV2Quickstart/
├── Areas/Identity/Pages/Account/   # Authentication pages (Register, Login, Verify)
├── Controllers/                    # MVC controllers
├── Data/                          # Entity Framework DbContext
├── Models/                        # Data models
├── Services/                      # Twilio Verify integration
├── Views/                         # Razor views
├── wwwroot/css/                   # Twilio Paste styling
└── Startup.cs                     # App configuration
```

## Key Technologies

- **ASP.NET Core 10.0** - Web framework
- **Entity Framework Core** - ORM for database access
- **SQLite** - Lightweight database
- **Twilio Verify API** - Phone verification service
- **Twilio Paste** - Design system for consistent UI

## Resources

- [Twilio Verify API Documentation](https://www.twilio.com/docs/verify/api)
- [Twilio C# SDK Documentation](https://www.twilio.com/docs/libraries/reference/twilio-csharp)
- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [Code Exchange](https://github.com/twilio-labs/code-exchange/)

## Contributing

This template is open source and welcomes contributions. All contributions are subject to our [Code of Conduct](https://github.com/twilio-labs/.github/blob/master/CODE_OF_CONDUCT.md).

## License

[MIT](LICENSE)

## Disclaimer

No warranty expressed or implied. Software is as is.
