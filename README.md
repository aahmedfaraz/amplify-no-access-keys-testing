# Steps for testing

Let say I am the new developer just came and company want me to edit amplify backend, it will provide me an IAM User credentials (**not access keys**) with `AdministratorAccess-Amplify` policy, so that I can update the backend, **but what we want to test is**, whenever company **deletes** my IAM User, I **should not be able to modify backend anymore**, following steps we can carry out:

1. Company will create an IAM User (dummy-user) for ahmed with `AdministratorAccess-Amplify` policy, keeping _`☐ Provide user access to the AWS Management Console - optional`_ UNCHECKED, means giving no access keys.
2. Company will create an amplify backend, and leave it for me to modify it.
3. I will login using IAM credentials, and get the `amplify pull` command.
4. I will come to my local repo and run `amplify pull --appId <app-id>`.
5. I need to authorize myself using Amplify Studio.
6. I will create any resource in it (for example, API).
7. I will then run `amplify push`, it will create the resource.
8. Now, here starts the actual test, now Company will `delete` my IAM User or `remove` the policy from my IAM User.
9. Now using the same process (using CLI), I will try to add any resource in the app and push it, and see the result.
