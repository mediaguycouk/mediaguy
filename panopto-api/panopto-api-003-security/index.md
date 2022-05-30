![Back to the index](../)

If we communicate with the server, we should be checking that it is a valid and secure server.

The following code is taken from the Panopto github: https://github.com/Panopto/ScheduleTool

Add the following name spaces to the top of the application you made in the ![previous posts](..)

```
using System.Net;
using System.Security.Cryptography.X509Certificates;
```

Add this to the top of the application, just above static void Main()

`static bool hasBeenInitialized = false;`

Then add the following to the bottom of the application. Within class Program but outside of static void Main()
```
        /// <summary>
        /// Ensures that our custom certificate validation has been applied
        /// </summary>
        public static void EnsureCertificateValidation()
        {
            if (!hasBeenInitialized)
            {
                ServicePointManager.ServerCertificateValidationCallback += 
                    new System.Net.Security.RemoteCertificateValidationCallback(CustomCertificateValidation);
                hasBeenInitialized = true;
            }
        }

        /// <summary>
        /// Ensures that server certificate is authenticated
        /// </summary>
        private static bool CustomCertificateValidation(object sender, 
            X509Certificate cert, X509Chain chain, System.Net.Security.SslPolicyErrors error)
        {
            return true;
        }
```

With this code you can call

`EnsureCertificateValidation();`

to ensure that the server certificate is valid. We will use this function in all our API calls.

Our full code now looks like this

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Net;
using System.Security.Cryptography.X509Certificates;
using ConsolePanoptoAPI.PanoptoAccessManagement;
using ConsolePanoptoAPI.PanoptoAuth;
using ConsolePanoptoAPI.PanoptoRemoteRecorderManagement;
using ConsolePanoptoAPI.PanoptoSessionManagement;
using ConsolePanoptoAPI.PanoptoUsageReporting;
using ConsolePanoptoAPI.PanoptoUserManagement;


namespace ConsolePanoptoAPI
{
    class Program
    {
        static bool hasBeenInitialized = false;
        
        static void Main(string[] args)
        {
            PanoptoAuth.AuthenticationInfo sessionAuthInfo = new PanoptoAuth.AuthenticationInfo()
            {
                UserKey = "api",
                Password = "s2ezupajePhasaP5"
            };

            IAuth iAuth = new AuthClient();
            Console.WriteLine(iAuth.GetServerVersion());
            Console.ReadLine();


        }

        /// <summary>
        /// Ensures that our custom certificate validation has been applied
        /// </summary>
        public static void EnsureCertificateValidation()
        {
            if (!hasBeenInitialized)
            {
                ServicePointManager.ServerCertificateValidationCallback += 
                    new System.Net.Security.RemoteCertificateValidationCallback(CustomCertificateValidation);
                hasBeenInitialized = true;
            }
        }

        /// <summary>
        /// Ensures that server certificate is authenticated
        /// </summary>
        private static bool CustomCertificateValidation(object sender, 
            X509Certificate cert, X509Chain chain, System.Net.Security.SslPolicyErrors error)
        {
            return true;
        }
    }
}
```
![Next: Authenticating with an identity provider](../panopto-api-004-authenticating-with-an-identity-provider)

![Back to the index](../)
