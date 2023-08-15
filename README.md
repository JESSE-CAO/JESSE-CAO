- 👋 Hi, I’m @JESSE-CAO
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

chatGPT的源码：
```python
import openai
openai.api_key = "YOUR_API_KEY" # 替换成你的API密钥

def generate_text(prompt):
    response = openai.Completion.create(
        engine="davinci", # 选择GPT的引擎，可选参数包括：davinci, curie, babbage, ada,等等。
        prompt=prompt,
        max_tokens=1024, # 生成的最大长度，单位为token数
        n=1, # 要生成的样本数
        stop=None, # 可选的停止标记，用于指定生成的文本何时停止。可以是单个字符串或字符串列表。
        temperature=0.5, # 生成文本的多样性。较高的值会产生更多的随机性，较低的值会产生更多的确定性。
        frequency_penalty=0, # 建议增加模型避免产生重复的文本。
        presence_penalty=0 # 建议增加模型避免产生与输入无关的文本。
    )
    return response.choices[0].text.strip()

prompt = "Hello, I am ChatGPT! How can I assist you today?"
response = generate_text(prompt)
print(response)
```
或者
```Java
import ai.openai.api.ApiException;
import ai.openai.api.CompletionsApi;
import ai.openai.api.models.CompletionRequest;
import ai.openai.api.models.CompletionResponse;

public class ChatGPT {
    private static final String apiKey = "YOUR_API_KEY"; // 替换成你的API密钥
    private static final String model = "davinci"; // 选择GPT的引擎，可选参数包括：davinci, curie, babbage, ada,等等。
    
    public static String generateText(String prompt) throws ApiException {
        CompletionRequest completionRequest = new CompletionRequest();
        completionRequest.setEngine(model);
        completionRequest.setPrompt(prompt);
        completionRequest.setMaxTokens(1024); // 生成的最大长度，单位为token数
        completionRequest.setN(1); // 要生成的样本数
        completionRequest.setTemperature(0.5); // 生成文本的多样性。较高的值会产生更多的随机性，较低的值会产生更多的确定性。
        completionRequest.setFrequencyPenalty(0); // 建议增加模型避免产生重复的文本。
        completionRequest.setPresencePenalty(0); // 建议增加模型避免产生与输入无关的文本。
        
        CompletionsApi apiInstance = new CompletionsApi();
        apiInstance.getApiClient().setApiKey(apiKey);

        CompletionResponse response = apiInstance.createCompletion(completionRequest);
        return response.getChoices().get(0).getText().trim();
    }

    public static void main(String[] args) throws ApiException {
        String prompt = "Hello, I am ChatGPT! How can I assist you today?";
        String response = generateText(prompt);
        System.out.println(response);
    }
}
```
还有
```go
package main

import (
	"context"
	"fmt"

	"github.com/openai/openai-go/v1"
)

func main() {
	apiKey := "YOUR_API_KEY" // 替换成你的API密钥
	model := "davinci" // 选择GPT的引擎，可选参数包括：davinci, curie, babbage, ada,等等。

	client, err := openai.NewClient(apiKey)
	if err != nil {
		fmt.Printf("Failed to create client: %v\n", err)
		return
	}

	ctx := context.Background()

	prompt := "Hello, I am ChatGPT! How can I assist you today?"

	resp, err := client.Completions.Create(ctx, &openai.CompletionRequest{
		Model:     model,
		Prompt:    prompt,
		MaxTokens: 1024, // 生成的最大长度，单位为token数
		N:         1,    // 要生成的样本数
		Temperature: 0.5, // 生成文本的多样性。较高的值会产生更多的随机性，较低的值会产生更多的确定性。
		FrequencyPenalty: 0, // 建议增加模型避免产生重复的文本。
		PresencePenalty: 0, // 建议增加模型避免产生与输入无关的文本。
	})

	if err != nil {
		fmt.Printf("Failed to generate text: %v\n", err)
		return
	}

	fmt.Println(resp.Choices[0].Text)
}
```
