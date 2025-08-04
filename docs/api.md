# API 文档

## 版本信息 API

### 获取版本列表
```
GET https://raw.githubusercontent.com/Bastandern/ar/main/assets/config/versions.json
```

**响应示例：**
```json
{
  "latest": "v1.0.0",
  "stable": "v1.0.0",
  "versions": [
    {
      "version": "v1.0.0",
      "status": "stable",
      "releaseDate": "2024-01-15",
      "fileSize": "2.1MB",
      "checksum": "sha256:your-checksum-here",
      "downloadUrl": "https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/v1.0.0/uap.ar",
      "description": "初始版本的扰动库"
    }
  ]
}
```

## 文件下载 API

### 下载最新版本
```
GET https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/latest/uap.ar
```

### 下载指定版本
```
GET https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/{version}/uap.ar
```

**参数：**
- `{version}`: 版本号，如 `v1.0.0`

### 获取文件元数据
```
GET https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/{version}/metadata.json
```

## 使用示例

### JavaScript
```javascript
// 检查版本
const response = await fetch('https://raw.githubusercontent.com/Bastandern/ar/main/assets/config/versions.json');
const versions = await response.json();
console.log('Latest version:', versions.latest);

// 下载文件
const fileResponse = await fetch(`https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/${versions.latest}/uap.ar`);
const fileData = await fileResponse.arrayBuffer();
```

### Python
```python
import requests

# 检查版本
response = requests.get('https://raw.githubusercontent.com/Bastandern/ar/main/assets/config/versions.json')
versions = response.json()
print(f"Latest version: {versions['latest']}")

# 下载文件
file_response = requests.get(f"https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/{versions['latest']}/uap.ar")
with open('uap.ar', 'wb') as f:
    f.write(file_response.content)
``` 