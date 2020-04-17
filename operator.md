# Hubcapp operator

### Per customer objects

For each customer, we have a kubernetes namespace.

```yaml
kind: Namespace
metadata:
  name: <customer-id>
```

We also have a customer configuration object

```yaml
kind: CustomerConfiguration
metadata:
    namespace: <customer-id>
    name: config
spec:
    logo: <image>
    companyname: <text>
    ...
    ...
```

### Per service objects

For each service of that customer, we have one CustomerService item.

```yaml
kind: CustomerService
metadata:
  namespace: <customer-id>
  name: <user-selected>
spec:
  service: <one of our supported options>
  options: <different data for each service>
status: <details edited by>
```

The operator will take each CustomerService and run the services required, depending on the kind of service requested
