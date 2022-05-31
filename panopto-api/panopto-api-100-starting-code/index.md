![Back to the index](../)

For the following pages we will be expanding on the following code. You should paste this code into a new C# console application.

None of the features will work until you add the service references to the solutions explorer and created a local user called API with the appropriate permissions.

The upcoming pages will tell you start writing between the // START WRITING CODE HERE and the // STOP WRITING CODE HERE lines.

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

// ANY NEW NAMESPACES SHOULD BE ADDED HERE

// END OF NAMESPACES

namespace ConsolePanoptoAPI
{
    class Program
    {
        static bool hasBeenInitialized = false;
        
        static void Main(string[] args)
        {
            // PUT YOUR AUTHENTICATION DETAILS HERE

            // END OF AUTHENTICATION DETAILS

            EnsureCertificateValidation();

            // START WRITING CODE HERE

            // STOP WRITING CODE HERE

            Console.WriteLine("Press Enter to exit");
            Console.ReadLine();
        }

        /// 
        /// Ensures that our custom certificate validation has been applied
        /// 
        public static void EnsureCertificateValidation()
        {
            if (!hasBeenInitialized)
            {
                ServicePointManager.ServerCertificateValidationCallback += 
                    new System.Net.Security.RemoteCertificateValidationCallback(CustomCertificateValidation);
                hasBeenInitialized = true;
            }
        }

        /// 
        /// Ensures that server certificate is authenticated
        /// 
        private static bool CustomCertificateValidation(object sender, 
            X509Certificate cert, X509Chain chain, System.Net.Security.SslPolicyErrors error)
        {
            return true;
        }

        /// 
        /// Creates an auth code. Used when we want to authenticate a user, but don't know their password.
        /// 
        ///The instance name as set in Panopto > System > Identity Providors
        ///Username as defined by Panopto
        ///The full server name as defined by Panopto > System > Settings > General site settings > Web server FQDN
        ///The key produced through Panopto > System > Identity Providors
        /// 
        private static string CreateAuthCode(string identityProviderInstanceName, string username, string serverFqdn, string applicationKey)
        {
            string payload = identityProviderInstanceName + @"\" + username + "@" + serverFqdn.ToLower() + "|" + applicationKey.ToLower();

            var data = Encoding.ASCII.GetBytes(payload);
            var hashData = new System.Security.Cryptography.SHA1Managed().ComputeHash(data);

            var hash = string.Empty;

            foreach (var b in hashData)
                hash += b.ToString("X2");

            return hash;
        }
    }
}

```

![Next: Getting folders](../panopto-api-101-getting-folders)

![Back to the index](../)
