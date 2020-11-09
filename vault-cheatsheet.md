

#						    VAULT

----
#### Centralized secrets management. 

-------------------------------
1.Start the vault server

`vault server -dev` 

2. Save the unseal key and the root key.


3. Status of vault server

`vault status`

----------------------------------

#### STORING SECRETS

* List all the secret engines available.
`vault secrets list`

*  Put a secret inside the engine.
`vault kv secret/hello name=siddharth `			
(Key-value secrets engine named 'secret')
('secret' is where the secrets can be accessed or written to.)

* Get the secret from.

` vault kv get secret/hello`

* Get a specific field:

`vault kv get -field=name secret/hello`

* Delete a secret:

`vault kv delete secret/hello`

-----------------------------------
#### Dynamic Secrets

1.Enable the AWS secrets engine.
`vault secrets enable -path=aws aws`

2.Configure the access and the secret key.
`Eg :-
vault write aws/config/root 
    access_key=<access-key>
    secret_key=<secret-key> 
    region=<region>`
    
3 .Creating a role 
`ault write aws/roles/my-role 
        credential_type=iam_user 
        policy_document= <policy-document>`
        
4.Generating secret.
`vault read aws/creds/<role-name>`

5.Revoking the secret.
`vault lease revoke <lease-id>`
-----
#### Authentication 

1.Create a new vault token
`vault token create`

2.To login using the newly created token use :
`vault login <token>`

3.Revoke the token 

`vault token revoke <token>`

4.Enable github auth method

`vault auth enable github`

        

    
    