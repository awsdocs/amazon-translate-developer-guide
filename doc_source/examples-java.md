# Translating text using the AWS SDK for Java<a name="examples-java"></a>

The following example demonstrates using the [TranslateText](https://docs.aws.amazon.com/translate/latest/APIReference/API_TranslateText.html) operation in Java\. To run this example, you need the AWS SDK for Java\. For instructions for installing the SDK for Java, see [ Set up the AWS SDK for Java](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-install.html)\. 

```
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.translate.AmazonTranslate;
import com.amazonaws.services.translate.AmazonTranslateClient;
import com.amazonaws.services.translate.model.TranslateTextRequest;
import com.amazonaws.services.translate.model.TranslateTextResult;
 
public class App {
    private static final String REGION = "region";
 
    public static void main( String[] args ) {
 
        // Create credentials using a provider chain. For more information, see
        // https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
        AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();
        
        AmazonTranslate translate = AmazonTranslateClient.builder()
                .withCredentials(new AWSStaticCredentialsProvider(awsCreds.getCredentials()))
                .withRegion(REGION)
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

For a list of supported languages and language codes, see [Supported languages and language codes](what-is-languages.md)