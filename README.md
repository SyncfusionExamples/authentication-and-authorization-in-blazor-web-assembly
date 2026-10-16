# Authentication and Authorization in Blazor WebAssembly

## Overview

This sample demonstrates authentication and authorization in a hosted Blazor WebAssembly application. The application uses the built-in ASP.NET Core Blazor authentication infrastructure, including `RemoteAuthenticatorView`, `AddApiAuthorization()`, and an authorized `HttpClient` configuration to securely communicate with protected server resources.

The sample provides a practical implementation of client-side authentication routing, anonymous page access, and automatic access token handling for API requests. It serves as a reference for developers building secure Blazor WebAssembly applications that require authenticated user access and protected backend communication.

## Key Features

- Implements authentication routing through `RemoteAuthenticatorView` in `Pages/Authentication.razor` using the route template `/authentication/{action}`.
- Supports built-in Blazor WebAssembly authentication actions including login, logout, registration, profile management, and authentication callbacks.
- Uses the `[AllowAnonymous]` attribute to allow public access to authentication and landing pages.
- Provides a public home page (`Pages/Index.razor`) that is accessible without authentication.
- Displays authentication-aware user interface elements using `AuthorizeView`.
- Shows the authenticated user's identity through `context.User.Identity?.Name`.
- Provides authenticated navigation links for user profile access through `authentication/profile`.
- Supports user registration through the `authentication/register` endpoint.
- Supports user login with return URL handling through the `authentication/login` endpoint.
- Implements secure logout functionality using `NavigationManager.NavigateToLogout()`.
- Provides automatic login redirection through the reusable `RedirectToLogin.razor` component.
- Uses `NavigationManager.NavigateToLogin()` to redirect anonymous users to the authentication system.
- Exposes an OpenID Connect (OIDC) configuration endpoint through `OidcConfigurationController`.
- Uses `IClientRequestParametersProvider` to supply client authentication parameters required by IdentityServer.
- Integrates ASP.NET Core Identity for user management and authentication.
- Uses Duende IdentityServer for OpenID Connect and OAuth 2.0 authentication workflows.
- Includes Entity Framework Core migrations for automatic creation of the Identity and IdentityServer database schema.
- Supports Identity entities including users, roles, claims, logins, tokens, and role assignments.
- Creates and manages IdentityServer persistence tables such as `DeviceCodes`, `PersistedGrants`, and `Keys`.
- Uses the custom `ApplicationUser` model derived from `IdentityUser` for application-specific user management.

## Prerequisites

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) or [Visual Studio Code](https://code.visualstudio.com/)
- [.NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet) compatible with the project's target framework

## How to Run the Project

**Visual Studio 2022**

1. Clone this repository.
2. Open the solution file:

```bash
  BlazorWASMAuthentication.sln
```

3. Restore all NuGet packages.
4. Ensure the hosted application startup configuration is selected if multiple startup projects are available.
5. Build the solution.
6. Press `Ctrl+F5` to build and run the application.
7. The application will launch using the URL configured by the project's launch settings.

**Visual Studio Code**

1. Clone this repository.
2. Open the repository folder in Visual Studio Code.
3. Open a terminal and navigate to the repository root folder.
4. Restore dependencies:

```bash
dotnet restore
```

5. Run the application:

```bash
dotnet run
```

6. Open the URL displayed in the terminal after the application starts successfully.

## Project Structure

`BlazorWASMAuthentication/Client/Pages/Authentication.razor` - Authentication route component that hosts `RemoteAuthenticatorView` and processes login, logout, registration, profile, and authentication callback actions.

`BlazorWASMAuthentication/Client/Pages/Index.razor` - Anonymous landing page displayed when users access the root application route.

`BlazorWASMAuthentication/Client/Pages/SurveyPrompt.razor` - Reusable survey component rendered from the home page and demonstrates component parameter binding.

`BlazorWASMAuthentication/Client/Shared/LoginDisplay.razor` - Authentication-aware navigation component that conditionally displays login, registration, profile, and logout options using `AuthorizeView`.

`BlazorWASMAuthentication/Client/Shared/RedirectToLogin.razor` - Helper component that automatically redirects anonymous users to the authentication system using `NavigateToLogin()`.

`BlazorWASMAuthentication/Server/Areas/Identity/Controllers/OidcConfigurationController.cs` - Controller that exposes OIDC client configuration parameters for authentication requests.

`BlazorWASMAuthentication/Server/Models/ApplicationUser.cs` - Application user entity that inherits from `IdentityUser` and serves as the Identity user model.

`BlazorWASMAuthentication/Server/Data/Migrations/00000000000000_CreateIdentitySchema.cs` - Initial Entity Framework Core migration that creates ASP.NET Core Identity and IdentityServer database tables.

`BlazorWASMAuthentication/Server/Data/Migrations/00000000000000_CreateIdentitySchema.Designer.cs` - Generated migration metadata defining the target database model.

`BlazorWASMAuthentication/Server/Data/Migrations/ApplicationDbContextModelSnapshot.cs` - Entity Framework Core model snapshot used to track schema changes.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- Official Authentication and Authorization documentation: https://blazor.syncfusion.com/documentation/common/security/authentication-and-authorization

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.