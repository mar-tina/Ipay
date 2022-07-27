# Ipay

Ipay SDK for IOS integrations

### How to use
SPM Swift package manager installation through the github url


```
https://github.com/mar-tina/Ipay.git
```

### STEP ONE

initialize Ipay class with the below params
- key
- baseURL

```swift
import Ipay 

struct ContentView: View {
  var pay = Ipay(key:"demoCHANGED", baseURL: "https://payments.ipayafrica.com/v3/ke")
  ...
}

```

### STEP TWO
Call setParams to setup the required gateway payment parameters
Find the full list below

```swift
import Ipay

  ...
  var pay = Ipay(key:"demoCHANGED", baseURL: "https://payments.ipayafrica.com/v3/ke")
  @State private var phonenumber = "0799******"
  
  var body: some View {
    Form {
       TextField("Phone number",text: $phonenumber)
    }
    
    Button(action: {
        pay.setParam(key: "tel", value: phonenumber)
    }) {
      Text("Proceed to Checkout")
    }
  }
  ...
```

### STEP THREE

Call checkout method that returns a valid URL than you can redirect as you wish

```swift 
    ...
    Button(action: {
        pay.setParam(key: "tel", value: phonenumber)
        ....
        let url = pay.checkout()
    }) {
      Text("Proceed to Checkout")
    }
    
    ...
```



### REQUIRED GATEWAY PARAMETERS

```swift
 pay.setParam(key: "live", value: "0")
 pay.setParam(key: "ttl", value: amount)
 pay.setParam(key: "eml", value: email)
 pay.setParam(key: "tel", value: phonenumber)
 pay.setParam(key: "oid", value: "112")
 pay.setParam(key: "inv", value: "112020102292999")
 pay.setParam(key: "vid", value: "demo")
 pay.setParam(key: "curr", value: "KES")
 pay.setParam(key: "p1", value: "airtel")
 pay.setParam(key: "p2", value: "020102292999")
 pay.setParam(key: "p3", value: "")
 pay.setParam(key: "p4", value: "900")
 pay.setParam(key: "cbk", value: "http:\\YOURCALLBACKURL:PORT")
 pay.setParam(key: "cst", value: "1")
 pay.setParam(key: "crl", value: "2")
```

