# Licensing

## Evaluation Period
- You can evaluate the library for several months before purchasing it.
- The latest version always contains a trial that expires at the **end of the month**. 
- You can extend your trial for several months by downloading the latest version at the start of every month.
- If you want to use the library for personal use or educational purpose, it's possible by downloading the latest version once per month.

## How can I purchase the library?
- You can purchase the library [here](http://dapper-plus.net/pricing)
- Upon purchase, you will receive an email with a license name and a license key.
- Make sure to check your **SPAM** folder if you don't receive the license within 24h.

## Setup License from config file
The license name and key can be added directly in the app.config or web.config file in the appSettings section.


```csharp
<appSettings>
	<add key="Z_Dapper_Plus_LicenseName" value="[licenseName]"/>
	<add key="Z_Dapper_Plus_LicenseKey" value="[licenseKey]"/>
</appSettings>
```

## Setup License from code
The license can be added directly in the code of your application. Make sure to follow recommendations about where to add this code. Upon purchase completion, an email will be sent with your license key information.


```csharp
// using Z.Dapper.Plus; // Don't forget to include this.

string licenseName = //... PRO license name
string licenseKey = //... PRO license key

DapperPlusManager.AddLicense(licenseName, licenseKey);

```

**ENSURE** to always test the license the first time you setup it

### Recommendations
- Use the config file to store your license name and license key.
- **Web App:** Use Application_Start in global.asax to activate your license.
- **WinForm App:** Use the main thread method to activate your license.
- **Win Service:** Use the OnStart method to activate your license

> The AddLicense must be set before the first call to the library. Otherwise, the monthly trial will start.

## How can I check if my license is valid?

The validate method allow you to know whether your license is valid or not.


```csharp
// CHECK if the license if valid for the default provider (SQL Server)
string licenseErrorMessage;
if (!Z.Dapper.Plus.DapperPlusManager.ValidateLicense(out licenseErrorMessage))
{
    throw new Exception(licenseErrorMessage);
}

// CHECK if the license if valid for a specific provider
string licenseErrorMessage;
if (!Z.Dapper.Plus.DapperPlusManager.ValidateLicense(out licenseErrorMessage, DapperProviderType.SqlServer))
{
   throw new Exception(licenseErrorMessage);
}
```

Another way to check if your license is valid is simply adding an invalid license instead.

The following error should be raised:

***ERROR_001: The provided license key is invalid or trial period is expired. Please buy a product license or go to [http://www.zzzprojects.com](http://www.zzzprojects.com) and download the latest trial version. License Count: 1***
