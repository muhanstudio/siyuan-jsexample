# 执行SQL查询

### 说明：

执行SQL查询

### 执行代码：

```javascript
const axios = require('axios');

// 定义 SQL 查询语句
const stmt = "要执行的SQL语句";

async function executeSQLQuery(stmt) {
  try {
    const response = await axios.post('http://127.0.0.1:6806/api/query/sql', {
      stmt: stmt
    });

    if (response.data.code === 0) {
      const data = response.data.data;
      console.log(data);
      // 在这里处理返回的数据
    } else {
      console.log('执行查询失败:', response.data.msg);
    }
  } catch (error) {
    console.error('执行查询时出现错误:', error);
  }
}

// 调用函数
executeSQLQuery(stmt);
```
