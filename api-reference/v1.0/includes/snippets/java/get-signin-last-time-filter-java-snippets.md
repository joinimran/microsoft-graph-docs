---
description: "Automatically generated file. DO NOT MODIFY"
---

```java

IGraphServiceClient graphClient = GraphServiceClient.builder().authenticationProvider( authProvider ).buildClient();

LinkedList<Option> requestOptions = new LinkedList<Option>();
requestOptions.add(new QueryOption("$filter", "startswith(displayName,'Eric'),"));

IUserCollectionPage users = graphClient.users()
	.buildRequest( requestOptions )
	.select("displayName,signInActivity")
	.get();

```