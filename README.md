# Javacord
A simple to use API to create a discord bot

#Maven
```
<repository>
  <id>javacord-repo</id>
  <url>http://repo.bastian-oppermann.de</url>
</repository>
...
<dependency>
  <groupId>de.btobastian.javacord</groupId>
  <artifactId>javacord</artifactId>
  <version>1.0.0</version>
</dependency>
```

#Download
For those of you how don't use maven: http://bastian-oppermann.de/downloads/javacord-latest.jar

#Javadocs
The javadocs can be found here: http://bastian-oppermann.de/docs/Javacord/

#How to connect
First of all you have to get an api instance:
```java
DiscordAPI api = Javacord.getApi();
```
Now you have to set your email and password:
```java
api.setEmail("your@mail.com");
api.setPassword("creativePassword");
```
Cause the connection is non-blocking the ReadyListener informs you, when the api is connected:
```java
api.connect(new ReadyListener() {

  @Override
  public void onReady() {
    System.out.println("Connected");
    // go on doing funny stuff
  }
  
  @Override
  public void onFail() {
    System.out.println("Connection failed!");
  }

});
```
Now you're connected. :)

#Examples

Creating a simple ping-pong bot:
```java
api = Javacord.getApi();
api.setEmail("your@mail.com");
api.setPassword("creativePassword");

api.connect(new ReadyListener() {

  @Override
  public void onReady() {
    System.out.println("Connected");
    
    // example how to register a listener
    api.registerListener(new MessageCreateListener() {
 
      @Override
      public void onMessageCreate(DiscordAPI api, Message message) {
        if (message.getContent.equals("ping")) {
          message.reply("pong");
        }
      }
    });
    
    // go on doing funny stuff
  }
  
  @Override
  public void onFail() {
    System.out.println("Connection failed!");
    System.exit(-1);
  }

});
```