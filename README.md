# browserstack-local-java(MITM)

[![Build Status](https://travis-ci.org/browserstack/browserstack-local-java.svg?branch=master)](https://travis-ci.org/browserstack/browserstack-local-java)

Java bindings for BrowserStack Local.

## Installation

Add this dependency to your project's POM:
```xml
<dependency>
    <groupId>com.browserstack</groupId>
    <artifactId>browserstack-local-java</artifactId>
    <version>1.0.3</version>
</dependency>
```

## Example

```java
import com.browserstack.local.Local;

# creates an instance of Local
Local bsLocal = new Local();

# replace <browserstack-accesskey> with your key. You can also set an environment variable - "BROWSERSTACK_ACCESS_KEY".
HashMap<String, String> bsLocalArgs = new HashMap<String, String>();
bsLocalArgs.put("key", "<browserstack-accesskey>");bsLocalArgs.put("mitmProxyHost", "127.0.0.1");
bsLocalArgs.put("mitmProxyPort", "8000");
bsLocalArgs.put("mitmProxyUser", "user");
bsLocalArgs.put("mitmProxyPass", "password");
bsLocalArgs.put("forcelocal", "true");
bsLocalArgs.put("forceproxy", "true");
        
# starts the Local instance with the required arguments
bsLocal.start(bsLocalArgs);

# check if BrowserStack local instance is running
System.out.println(bsLocal.isRunning());

#stop the Local instance
bsLocal.stop();
```

## Arguments

Apart from the key, all other BrowserStack Local modifiers are optional. For the full list of modifiers, refer [BrowserStack Local modifiers](https://www.browserstack.com/local-testing#modifiers). For examples, refer below -





#### Force Start
To kill other running Browserstack Local instances -
```java
bsLocalArgs.put("force", "true");
```




#### Force Local
To route all traffic via local(your) machine -
```java
bsLocalArgs.put("forcelocal", "true");
```

#### Force Proxy
To route all traffic via the proxy specified.
```java
bsLocalArgs.put("forceproxy", "true");
```

#### Proxy
To use a proxy for MITM proxy testing -

* mitmproxyHost: Hostname/IP of proxy, remaining proxy options are ignored if this option is absent
* mitmproxyPort: Port for the proxy, defaults to 3128 when -proxyHost is used
* mitmproxyUser: Username for connecting to proxy (Basic Auth Only)
* mitmproxyPass: Password for USERNAME, will be ignored if USERNAME is empty or not specified

```java
bsLocalArgs.put("mitmProxyHost", "127.0.0.1");
bsLocalArgs.put("mitmProxyPort", "8000");
bsLocalArgs.put("mitmProxyUser", "user");
bsLocalArgs.put("mitmProxyPass", "password");
```
#### Local Proxy
To use local proxy in local testing -

* localProxyHost: Hostname/IP of proxy, remaining proxy options are ignored if this option is absent
* localProxyPort: Port for the proxy, defaults to 8081 when -localProxyHost is used
* localProxyUser: Username for connecting to proxy (Basic Auth Only)
* localProxyPass: Password for USERNAME, will be ignored if USERNAME is empty or not specified

```java
bsLocalArgs.put("localProxyHost", "127.0.0.1");
bsLocalArgs.put("localProxyPort", "8000");
bsLocalArgs.put("-localProxyUser", "user");
bsLocalArgs.put("-localProxyPass", "password");
```

