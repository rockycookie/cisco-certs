# Username-Password Device-Local Authentication

## Create username and password
```
Router(config)#username luke ?
  password   Specify the password for the user
  privilege  Set user privilege level
  secret     Specify the secret for the user
  <cr>

Router(config)#username luke secret myrouter
```

## Apply Username-Password in a Line
From `line vty` or `line console`
```
Router(config-line)# login local
```
