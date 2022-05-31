## Panopto API
I’m learning how to use the Panopto API. The trouble is that there seems to be a lot of technical resource, and a few people that seem to be a dab hand, but no middle ground.

I’m hoping to fill that gap. Any questions let me know in the comments.

In these examples I’m going to be using Visual Studio 2010 using C# as the language. I have ReSharper on my computer, just in case any of the colours or tooltips look slightly different. I’ve tried using PHP, but the ease of communicating with Panopto in C# is so large compared to PHP, I’d recommend switching.

> Mediaguy.co.uk’s Panopto API code samples are free software: you can redistribute
it and/or modify it under the terms of the GNU General Public License as published
by the Free Software Foundation, either version 3 of the License, or (at your option)
any later version.
> 
> Mediaguy.co.uk’s Panopto API code samples are distributed in the hope that it will be
useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
>
> You should have received a copy of the GNU General Public License along with
Mediaguy.co.uk’s Panopto API code samples. If not, see <http://www.gnu.org/licenses/>.

*These pages have been moved to github.io. Please do let me know if any of the styling 
has failed to migrate as I've had to convert from html to markdown manually*


[001: Connecting to the server](panopto-api-001-connecting-to-the-server/)

[002: Adding all web services](panopto-api-002-adding-all-web-services/)

[003: Security](panopto-api-003-security/)

[004: Authenticating with an identity provider](panopto-api-004-authenticating-with-an-identity-provider/)

 

[100: Starting code – The upcoming pages will need you to create a new console application with the following code](/panopto-api-100-starting-code)

[101: Getting folders](panopto-api-101-getting-folders)

102: Searching for folders and getting IDs from folder names

103: Organise course folders into subfolders

104: Adding group permissions to the parent folders

201: Getting sessions

202: User details and session details

203: Looping through more than one page

204: Renaming videos older than a set retention date

205: Moving sessions into a folder

301: Creating users and groups from AD (improved in 401)

 

400: Starting code – From this point on I’m using a C# aspx website for the API. I’ve not done much aspx so a lot of the web code is poor, you should take this into account.
The code is available from https://github.com/mediaguycouk/WebPanoptoAPI

401: Creating users and groups from AD
