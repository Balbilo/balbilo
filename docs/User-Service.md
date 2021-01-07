# User Service

User Service its responsible to :

#### 1) Register User:

* Clients will request service with Users details (Email, Full Name, Date of Birth, Password).
* Validate Details
* Bcrypt Password + Salt  
* User details will be stored to the database with (Email and Unique Generated UserID) as primary key 
  and (Full Name, DOB, Hashed Password, Salt, EmailVerified)
* An email will be sent to the User's Email to verify email
* A token will be generated and stored to DB along with users email  
* A pair of (Refresh token & Access token) will be generated to provide certain Permissions and Refresh Access Token
* Refresh token will be stored to DB along with User's ID
* A (Refresh token & Access token) will return back to the client to generate short-lived JWTs.

#### 2) Log in User:
* Clients will request service with Users (Email & Password)
* Validate Details (Email & Password)
* Authenticate users credentials
* A (Refresh token & Access token) will be generated to provide certain Permissions and Refresh Access Token
* Refresh token will be stored to DB along with User's ID
* A (Refresh token & Access token) will return back to the client to generate short-lived JWTs.

#### 3) Log out User
* Client will request to log out with (Access Token, Refresh Token)
* Client will delete local tokens
* Service will delete all tokens related to account.

#### 4) Update Details:
* Client will request service with (Access Token, Refresh Token, Map[Fields -> Value])
* Update User's Details in DB

#### 6) Update Email:
* Client will request service with (Access Token, Refresh Token, Old Email, New Email)
* Verify Old Email
* Validate New Email
* A token will be generated and stored to DB along with new user's email
* An email will be sent to the User's Old and New Email to verify email
* Set Users EmailVerified to false

#### 7) Verify Email:
* Client will request service with token Id generated in Update Email or Register Endpoint.
* Set Users EmailVerified to true

#### 8) Forgot Password
* Client will request service with email 
* Service will send to the email a link to redirect user to update password

### 9) Refresh Token
* Client will request to log out with (Expired Access Token, Refresh Token, UserId)

![User Service](../images/User%20Service%20.png)