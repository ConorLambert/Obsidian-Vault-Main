### Authentication and Authorisation
- Windows authentication
- User must be setup in specific **Active Directory** group related to Actuarial Reporting
- User must be added to the **AspNetUsers** table
- All custom roles defined by the platform are stored in **AspNetRoles** table
- The **AspNetUserRoles** table joins the two tables.

### `[Authorize]` attribute
- Placed above multiple controllers and actions depending on access requirements
- What happens internally when a request is received is explained [[Authorization#`[Authorize]` Attribute|here]]:
```c#
[Authorize(Roles="Admin")]
[ApiController]
public AdminController : Controller
{
	// LOGIC HERE
}

[Authorize(Roles="Admin,RunGroupUser,RunGroupCreator")]
[ApiController]
public RunGroupController : Controller
{
	[Authorize(Roles="RunGroupCreator")]
	public async Task<int> CreateRunGroup(CreateRunGroupCommand command)
	{
		// LOGIC HERE
	}

	// MORE LOGIC HERE
}
```

### CORS
- [[CORS]]
- `AddCors` in `Startup.cs`.

### .NET
###### Startup.cs
- `.AddCors`
	- Allows Angular or other client access the API
	- `.AllowCredentials` is important too
- `.AddAuthentication(IISDefaults.AuthenticationScheme)`
	- Adds Windows Authentication
- `AddIdentity`.`AddRoleManager`.`AddEntityFrameworkStore`
	- Define what classes are used for the DbContext (`ApplicationUserDbContext`), the User class (`ApplicationUser`) and the Role (`ApplicationRole`) class.
- `.UseCors`
- `.UseAuthentication`
###### launchSettings.json
- `windowsAuthentication: true`
- `anonymousAuthentication: true`
###### HttpContextAccessor
- Get current user from request.
- `httpContextAccessor.HttpContext.User.Identities.First().Name`

### Angular
###### Setup
- Singleton class called `UserAuthenticationService` provided in `root`
- On initialization, it calls backend service for authenticating user
- The returned object contains the user information including their roles.
- This object is then accessible by any component that requires it
###### Roles
- Component in question accesses `user` object from `UserAuthenticationService` class
- The roles property of the `user` object is used in directives to restrict/allow access.
###### Windows Authentication
- HTTP Interceptor
	- `{ withCredentials: true }`
	- Appended to every outgoing request
- Update `appsettings.json`
	- `"require_windows_authentication": true`
###### Route Guards
- `canActivate`
- `canLoad` for lazy loaded modules

### Server Setup and Configuration
- Medium [article](https://lukelindner.medium.com/windows-authentication-with-net-core-api-and-angular-project-on-iis-ae16a573902e)
- Must install and enable modules/components on the server
- IIS
	- Anonymous and windows authentication settings should be enabled.