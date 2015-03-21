<h1>Checking for Internet Connection</h1>
<p>This is a background service that constantly checks if connection is available. You can select the URL to ping and the interval of this action.</p>

<h1>How to</h1>

In your activity, where you want to start this service:

```java
        Intent intent = new Intent(this, ConnectionService.class);
        // Interval in seconds
        intent.putExtra(ConnectionService.TAG_INTERVAL, 100);
        // URL to ping
        intent.putExtra(ConnectionService.TAG_URL_PING, "http://www.google.com");
        // Name of the class that is calling this service
        intent.putExtra(ConnectionService.TAG_ACTIVITY_NAME, this.getClass().getName());
        // Starts the service
        startService(intent);
```

Implement ConnectionService.ConnectionServiceCallback on your activity and override the methods:

```java
    @Override
    public void hasInternetConnection() {
       // has internet
    }

    @Override
    public void hasNoInternetConnection() {
       // no internet :(
    }
```

Stop the service

```java
 	stopService(new Intent(this, ConnectionService.class));
```
