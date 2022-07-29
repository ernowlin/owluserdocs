# Securing Passwords

Security is the utmost importance for Collibra DQ and our customers. In order to not send around plain text passwords when owlchecks are executed from the CLI users/admins can encrypt passwords and execute owlchecks using the encrypted passwords instead of plain text. To encrypt your password execute the command below\\

The output password will look something like the following\\

Now you can use this password in any owlcheck from the command line where you would normally place a plain text password. Example owlcheck with encrypted password in place of plain text password highlighted in bold.\\

\
If executing a DQ Job from within the Owl-web the owl-web will automatically encrypt your password for you -- so you do not have to encrypt it. All passwords are masked out of the logs in order not to store plan passwords for security purposes.
