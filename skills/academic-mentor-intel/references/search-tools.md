# 已验证的搜索工具清单

## ✅ 可用工具

### 1. 微信搜一搜（wechat-article-search）
**Skill:** `wechat-article-search`  
**功能:** 搜索所有公众号文章中提到目标人物的内容  
**命令:**
```bash
cd skills/wechat-article-search
node scripts/search_wechat.js "关键词" -n 10
```
**优势:**
- ✅ 时效性最强（能找到最近几天的文章）
- ✅ 覆盖广（所有公众号文章）
- ✅ 返回结构化数据（标题、链接、摘要、时间、来源）

**示例结果:**
- 2026年3月16日：龙虾派对活动
- 2026年2月6日：央视AI迎春夜
- 2026年1月29日：钙钛矿量子点研究

---

### 2. arXiv 论文搜索
**方法:** 直接 web_fetch  
**URL:** `https://arxiv.org/search/?query=作者英文名&searchtype=author`  
**功能:** 搜索学术论文（AI/CS领域）

**命令:**
```bash
web_fetch "https://arxiv.org/search/?query=He+Jiyan&searchtype=author"
```

**优势:**
- ✅ 学术成果完整记录
- ✅ 可按时间排序
- ✅ 显示合作者信息

**示例结果:**
- 2026年3月：数学问题AI求解
- 2026年1月：GUI隐私保护、代码仓库导航
- 2025年12月：工具模拟、进化算法推理

---

### 3. Google Scholar
**Skill:** `scholar`（已安装，但被墙）  
**状态:** ❌ 中国大陆无法直接访问  
**替代方案:** 使用 arXiv + 百度学术

---

### 4. 百度新闻
**方法:** web_fetch  
**URL:** `https://www.baidu.com/s?wd=关键词 2025 2026`  
**功能:** 搜索新闻报道、活动信息

**优势:**
- ✅ 适合搜索会议、活动、获奖信息
- ✅ 时效性较好

---

## ❌ 不可用工具

### 豆瓣学术（paper.dou.ac）
**状态:** ❌ 搜索结果为空或无实际内容  
**结论:** 不推荐使用

---

## 🎯 标准搜索流程（更新版）

```
输入：学者姓名
  ↓
1. 微信搜一搜 (wechat-article-search) - 最新动态
  ↓
2. arXiv 搜索 - 学术论文
  ↓
3. 百度新闻 - 活动报道
  ↓
4. 整合 + 生成报告
```

---

## 📝 使用示例

### 完整搜索[目标导师]

```bash
# Step 1: 微信搜一搜
cd skills/wechat-article-search
node scripts/search_wechat.js "[目标导师]" -n 10 > /tmp/wechat_results.json

# Step 2: arXiv 搜索
web_fetch "https://arxiv.org/search/?query=He+Jiyan&searchtype=author" > /tmp/arxiv_results.txt

# Step 3: 百度新闻
web_fetch "https://www.baidu.com/s?wd=[目标导师] 2025 2026" > /tmp/baidu_results.txt

# Step 4: 整合生成报告
# (由 OpenClaw 主系统完成)
```

---

## 🔧 故障排除

### 问题：Node.js command not found
**解决:**
```bash
export PATH="/home/batchcom/.nvm/versions/node/v24.14.0/bin:$PATH"
```

### 问题：cheerio module not found
**解决:**
```bash
cd skills/wechat-article-search
npm install cheerio
```

### 问题：Google Scholar 无法访问
**解决:** 使用 arXiv + 百度学术替代

---

**更新时间:** 2026-03-19  
**验证状态:** ✅ 已在[目标导师]案例中验证有效
