# Azure CosmosDb Junit(5) Extension

I created this extension after introducing Azure CosmosDb testcontainers plugin.

WARNING!

This project is still in WIP! After new testcontainers release, project will be in its own release cycle.

See https://github.com/testcontainers/testcontainers-java/pull/4303

## Usage

````java
import com.azure.cosmos.CosmosAsyncClient;
import com.okohub.azure.cosmosdb.junit.AsyncClientCosmosDataExtension;
import com.okohub.azure.cosmosdb.junit.CosmosData;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.RegisterExtension;

public class MyAwesomeTests {

  //here may be some awesome testcontainers code, you can check module tests!

  @RegisterExtension
  AsyncClientCosmosDataExtension cosmosDataExtension =
      new AsyncClientCosmosDataExtension("endpoint", "key");

  @CosmosData(path = "data.json", partitionKey = "id")
  @Test
  public void shouldDoSomething(CosmosAsyncClient client) {
    //do something
  }
}
````
## Features

- Supported data loading from resources or absolute path.
- Use autoconfigured cool CosmosAsyncClient by injecting to test method. Neat!
- `@CosmosData` annotation has sensible defaults, so you don't need to provide every detail. Just test your code!

## License
Azure CosmosDb Junit Extension is licensed under the [MIT](/LICENSE.md) license.
