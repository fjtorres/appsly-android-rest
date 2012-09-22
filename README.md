# Restrung

Restrung is an Android client library for RESTful and HTTP based web services.

# Introduction

Restrung was born out of the need to provide a clear and easy interface for Android apps @ 47 degrees to RESTful and HTTP based web services.
Contributions and constructive feedback will always be welcomed.

## 1. Download

### 1.1. Maven Dependency

Restrung may be automatically imported in your project if you already use [Maven](http://maven.apache.org/). Just declare restrung as a maven dependency.

```xml
<dependency>
    <groupId>org.restrung</groupId>
    <artifactId>restrung</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```
### 1.2. APKLib and others

## 2. Usage

Whether you plan to use Restrung for simple http requests to a RESTful service or you need more control over requests, serialization, etc.
We encourage you to read this short guide to fully understand what RESTRung is and what's not.

### 2.1. Simple

The main interface to send requests and receive serialize responses is through the RestClient which default implementation you can access with the RestClientFactory
The RestClient exposes both Asynchronous and Synchronous operations for the most commons [HTTP verbs](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html).

#### 2.1.1. Async

#### 2.1.1.1 GET

```java
RestClientFactory.getClient().getAsync(new ContextAwareAPIDelegate<Target>(context, Target.class) {

    @Override
	public void onResults(Target response) {
		//handle results here in the main thread
	}

	@Override
	public void onError(Throwable e) {
		//handle error here in the main thread
	}

}, "http://url/%s/%s", "param1", "param2");
```

#### 2.1.1.2 POST

*Simple POST*

```java
//An object that implements JSONSerializable
AnyBeanObject sourceObject = new AnyBeanObject();
sourceObject.setName("name");

RestClientFactory.getClient().postAsync(new ContextAwareAPIDelegate<Target>(context, Target.class) {

    @Override
	public void onResults(Target response) {
		//handle results here in the main thread
	}

	@Override
	public void onError(Throwable e) {
		//handle error here in the main thread
	}

}, "http://url/%s/%s", sourceObject , "param1", "param2");
```

*Multipart POST*

```java
File file = ....;

//An object that implements JSONSerializable
AnyBeanObject sourceObject = new AnyBeanObject();
sourceObject.setName("name");

RestClientFactory.getClient().postAsync(new ContextAwareAPIDelegate<Target>(context, Target.class) {

    @Override
	public void onResults(Target response) {
		//handle results here in the main thread
	}

	@Override
	public void onError(Throwable e) {
		//handle error here in the main thread
	}

}, "http://url/%s/%s", sourceObject, file , "param1", "param2");
```

#### 2.1.1.3 PUT

```java
//An object that implements JSONSerializable
AnyBeanObject sourceObject = new AnyBeanObject();
sourceObject.setName("name");

RestClientFactory.getClient().putAsync(new ContextAwareAPIDelegate<Target>(context, Target.class) {

    @Override
	public void onResults(Target response) {
		//handle results here in the main thread
	}

	@Override
	public void onError(Throwable e) {
		//handle error here in the main thread
	}

}, "http://url/%s/%s", sourceObject , "param1", "param2");
```

#### 2.1.1.4 DELETE

```java
RestClientFactory.getClient().deleteAsync(new ContextAwareAPIDelegate<Target>(context, Target.class) {

    @Override
	public void onResults(Target response) {
		//handle results here in the main thread
	}

	@Override
	public void onError(Throwable e) {
		//handle error here in the main thread
	}

}, "http://url/%s/%s", "param1", "param2");
```

### 2.2. Advanced

If you don't wish to use the RestClientFactory and RestClient interfaces you can get finer control by directly utilizing any of the
loaders, asynctasks or runnable classes for each one of the operations.

#### 2.2.1. Loaders

#### 2.2.1.1 GET

[org.restrung.rest.async.loaders.APIGetLoader](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/loaders/APIGetLoader.java)

#### 2.2.1.2 POST

[org.restrung.rest.async.loaders.APIPostLoader](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/loaders/APIPostLoader.java)

#### 2.2.1.3 PUT

[org.restrung.rest.async.loaders.APIPutLoader](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/loaders/APIPutLoader.java)

#### 2.2.1.4 DELETE

[org.restrung.rest.async.loaders.APIDeleteLoader](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/loaders/APIDeleteLoader.java)

#### 2.2.2. AsyncTasks

#### 2.2.2.1 GET

[org.restrung.rest.async.asynctasks.APIGetAsyncTask](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/asynctasks/APIGetAsyncTask.java)

#### 2.2.2.2 POST

[org.restrung.rest.async.asynctasks.APIPostAsyncTask](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/asynctasks/APIPostAsyncTask.java)

#### 2.2.2.3 PUT

[org.restrung.rest.async.asynctasks.APIPutAsyncTask](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/asynctasks/APIPutAsyncTask.java)

#### 2.2.2.4 DELETE

[org.restrung.rest.async.asynctasks.APIDeleteAsyncTask](https://github.com/47deg/restrung/blob/master/src/main/java/org/restrung/rest/async/asynctasks/APIDeleteAsyncTask.java)

#### 2.2.3. Runnables

#### 2.2.4. Cache

#### 2.2.5. Serialization

#### 2.2.6. Interceptors


