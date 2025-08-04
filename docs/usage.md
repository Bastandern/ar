# 使用说明

## 快速开始

### 1. 获取最新版本信息
```bash
curl https://raw.githubusercontent.com/Bastandern/ar/main/assets/config/versions.json
```

### 2. 下载扰动文件
```bash
# 下载最新版本
curl -O https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/latest/uap.ar

# 下载指定版本
curl -O https://raw.githubusercontent.com/Bastandern/ar/main/assets/perturbations/v1.0.0/uap.ar
```

## 在 EchoShield 中使用

### 环境配置
在你的 `.env` 文件中添加：
```bash
VITE_BASE_URL = 'https://raw.githubusercontent.com/Bastandern/ar/main'
VITE_PERTURBATION_PATH = '/assets/perturbations/latest/uap.ar'
VITE_VERSION_CHECK_URL = 'https://raw.githubusercontent.com/Bastandern/ar/main/assets/config/versions.json'
```

### 代码示例
```javascript
import { checkPerturbationVersion, downloadPerturbation } from './utils/version.js';

// 检查版本
const versionInfo = await checkPerturbationVersion();
console.log('Latest version:', versionInfo.latest);

// 下载扰动文件
const perturbationData = await downloadPerturbation('latest');
```

## 版本管理

### 版本号规则
- 格式：`v主版本.次版本.修订版本`
- 示例：`v1.0.0`, `v1.1.0`, `v2.0.0`

### 版本状态
- `stable`: 稳定版本，推荐使用
- `beta`: 测试版本，谨慎使用
- `alpha`: 开发版本，不推荐使用

## 文件格式

### uap.ar 文件
- 格式：AR (Audio Response)
- 用途：音频扰动响应文件
- 大小：约 2.1MB

### 元数据文件
- `metadata.json`: 版本详细信息
- `changelog.md`: 更新日志
- `versions.json`: 全局版本信息

## 故障排除

### 常见问题

1. **文件下载失败**
   - 检查网络连接
   - 确认文件URL正确
   - 验证GitHub仓库可访问

2. **版本信息获取失败**
   - 检查 `versions.json` 文件格式
   - 确认JSON语法正确
   - 验证网络连接

3. **文件校验失败**
   - 检查文件完整性
   - 重新下载文件
   - 验证checksum值

### 联系支持
如有问题，请在GitHub仓库中提交Issue。 