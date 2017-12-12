# Translating Text Using the AWS SDK for Java<a name="examples-java"></a>

The following example demonstrates using the [TranslateText](API_TranslateText.md) operation in Java\. To run this example, you need the AWS SDK for Java\. For instructions for installing the SDK for Java, see [ Set up the AWS SDK for Java](http://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-install.html)\. 

```
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.translate.AWSTranslate;
import com.amazonaws.services.translate.AmazonTranslateClient;
import com.amazonaws.services.translate.model.TranslateTextRequest;
import com.amazonaws.services.translate.model.TranslateTextResult;

public class App {
    private static final String ENDPOINT = "endpoint";
    private static final String REGION = "region";

    public static void main( String[] args ) {

        BasicAWSCredentials awsCredentials = new BasicAWSCredentials("access key ID", "secret access key");
        AwsClientBuilder.EndpointConfiguration endpointConfiguration = new AwsClientBuilder.EndpointConfiguration(ENDPOINT, REGION);

        AWSTranslate translate = AmazonTranslateClient.builder()
                .withCredentials(new AWSStaticCredentialsProvider(awsCredentials))
                .withEndpointConfiguration(endpointConfiguration)
                .build();

        TranslateTextRequest request = new TranslateTextRequest()
                .withText("Hello, world")
                .withSourceLanguageCode("en")
                .withTargetLanguageCode("es");
        TranslateTextResult result  = translate.translateText(request);
        System.out.println(result.getTranslatedText());
    }
}
```

You can change the source and target languages subject to the following constraints:

+ If the source language is English, you can translate the source text to any of the other supported languages\. For a list of supported languages, see [ How It Works](how-it-works.md)\.

+ If the source language is not English, the target language must be English\.