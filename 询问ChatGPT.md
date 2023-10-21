# 询问ChatGPT

### 说明：

询问ChatGPT

### 执行代码：

```javascript
const apiUrl = 'https://api.openai.com/v1/completions'; // API的URL
const apiKey = 'YOUR_API_KEY'; // 替换为你的OpenAI API密钥

const maxTokens = 100; // 最大生成标记数
const temperature = 0.8; // 回答随机性，范围从0到1，值越高，回答越随机
const topP = 1; // Nucleus采样的截断阈值，范围从0到1，值越低，生成的文本越保守
const question = "你的问题"; //替换为你的问题

// 使用fetch函数向API发送POST请求
async function askGpt(question) {
  const requestBody = {
    prompt: question,
    max_tokens: maxTokens,
    temperature: temperature,
    top_p: topP
  };

  try {
    const response = await fetch(apiUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': `Bearer ${apiKey}`
      },
      body: JSON.stringify(requestBody)
    });

    if (response.ok) {
      const data = await response.json();
      return data.choices[0].text.trim();
    } else {
      throw new Error('请求失败');
    }
  } catch (error) {
    console.error(error);
    return null;
  }
}

// 在控制台中测试
const question = prompt('请输入您的问题：');
askGpt(question)
  .then(answer => {
    console.log('回答：', answer);
  })
  .catch(error => {
    console.error('发生错误：', error);
  });
```
