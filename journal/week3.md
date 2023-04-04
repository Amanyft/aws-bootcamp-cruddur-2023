# Week 3 — Decentralized Authentication
### Provision Cognito User Group

![1](https://user-images.githubusercontent.com/80603078/229393975-49208a28-2992-42b2-b42a-fbf92f16f896.PNG)

### Install AWS Amplify 

```sh
npm i aws-amplify --save
```

![2](https://user-images.githubusercontent.com/80603078/229394702-2fc181a2-df87-4cb7-9de1-45713afa0450.PNG)

### Configure Amplify


Configure cognito pool to our code in the `App.js`

```js
import { Amplify } from 'aws-amplify';
Amplify.configure({
  "AWS_PROJECT_REGION": process.env.REACT_AWS_PROJECT_REGION,
  "aws_cognito_identity_pool_id": process.env.REACT_APP_AWS_COGNITO_IDENTITY_POOL_ID,
  "aws_cognito_region": process.env.REACT_APP_AWS_COGNITO_REGION,
  "aws_user_pools_id": process.env.REACT_APP_AWS_USER_POOLS_ID,
  "aws_user_pools_web_client_id": process.env.REACT_APP_CLIENT_ID,
  "oauth": {},
  Auth: {
    // We are not using an Identity Pool
    // identityPoolId: process.env.REACT_APP_IDENTITY_POOL_ID, // REQUIRED - Amazon Cognito Identity Pool ID
    region: process.env.REACT_AWS_PROJECT_REGION,           // REQUIRED - Amazon Cognito Region
    userPoolId: process.env.REACT_APP_AWS_USER_POOLS_ID,         // OPTIONAL - Amazon Cognito User Pool ID
    userPoolWebClientId: process.env.REACT_APP_AWS_USER_POOLS_WEB_CLIENT_ID,   // OPTIONAL - Amazon Cognito Web Client ID (26-char alphanumeric string)
  }
});



```
And here it is !
<br>

![3](https://user-images.githubusercontent.com/80603078/229653222-b6c8d87f-0ac2-42e0-b282-e8f8d84ae5e6.PNG)

### Conditionally show components based on logged in or logged out

#### Inside our HomeFeedPage.js we add the following code

```js
import { Auth } from 'aws-amplify';
```

```
// set a state
const [user, setUser] = React.useState(null);
```

```
// check if we are authenicated
const checkAuth = async () => {
  Auth.currentAuthenticatedUser({
    // Optional, By default is false. 
    // If set to true, this call will send a 
    // request to Cognito to get the latest user data
    bypassCache: false 
  })
  .then((user) => {
    console.log('user',user);
    return Auth.currentAuthenticatedUser()
  }).then((cognito_user) => {
      setUser({
        display_name: cognito_user.attributes.name,
        handle: cognito_user.attributes.preferred_username
      })
  })
  .catch((err) => console.log(err));
};

```
![5](https://user-images.githubusercontent.com/80603078/229930064-97f8dc29-d01e-4bab-a675-356282e04dd3.PNG)

We'll update `ProfileInfo.js`

```js
import { Auth } from 'aws-amplify';
const signOut = async () => {
  try {
      await Auth.signOut({ global: true });
      window.location.href = "/"
  } catch (error) {
      console.log('error signing out: ', error);
  }
}
```

![6](https://user-images.githubusercontent.com/80603078/229934727-d48b6c1a-0671-4d54-9134-6d6dcab59c64.PNG)




