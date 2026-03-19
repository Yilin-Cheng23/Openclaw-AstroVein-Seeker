# 标准工作流程（规范化）

**重要原则：只用真实搜索到的信息，不用对话历史！**

---

## 输入

```
姓名：xxx
机构：xxx（可选）
导师：xxx（可选）
```

---

## 第1步：微信公众号搜索（最重要！时效性第一）

### 策略A：搜索学者姓名
```bash
web_fetch "https://www.baidu.com/s?wd=site:mp.weixin.qq.com [学者姓名]"
```

**如果被验证码拦截：**
```bash
web_fetch "https://www.baidu.com/s?wd=[学者姓名] 微信公众号 文章"
```

### 策略B：搜索机构公众号
```bash
web_fetch "https://www.baidu.com/s?wd=[机构名] 微信公众号"
web_fetch "https://www.baidu.com/s?wd=[机构名] [学者姓名] 文章"
```

### 策略C：搜索导师/实验室公众号
```bash
web_fetch "https://www.baidu.com/s?wd=[导师姓名] 实验室 微信公众号"
```

### 如果找到公众号文章链接
```bash
python3 skills/wechat-article/scripts/wechat_article.py "https://mp.weixin.qq.com/s/xxx"
```

---

## 第2步：百度实时新闻（最近6个月）

```bash
web_fetch "https://www.baidu.com/s?wd=[学者姓名] [机构] 2025 2026"
web_fetch "https://www.baidu.com/s?wd=[学者姓名] 最新动态"
```

**重点关注：**
- 会议发言
- 项目发布
- 采访报道
- 奖项荣誉

---

## 第3步：arXiv 最新论文（最近6个月）

```bash
web_fetch "https://arxiv.org/search/?query=[学者英文名]&searchtype=author&order=-announced_date_first"
```

或者用百度搜索：
```bash
web_fetch "https://www.baidu.com/s?wd=site:arxiv.org [学者英文名] 2025 2026"
```

---

## 第4步：小红书（如果有）

```bash
web_fetch "https://www.baidu.com/s?wd=site:xiaohongshu.com [学者姓名]"
```

---

## 第5步：Google Scholar（如果可访问）

```bash
web_fetch "https://scholar.google.com/scholar?q=[学者英文名]"
```

如果被墙，跳过这一步。

---

## 第6步：整合信息

### 只用搜索到的真实信息！

**❌ 禁止：**
- 使用对话历史中的信息
- 凭空推断未搜索到的内容
- 用"可能"、"应该"填充信息

**✅ 允许：**
- 明确标注来源的信息
- 从搜索结果中提取的事实
- 基于真实信息的合理洞察（标注"洞察"）

### 信息分类

1. **最新动态（2025-2026）**
   - 来源：公众号文章 / 百度新闻
   - 标注：📱 公众号 / 📰 百度新闻

2. **历史成果（2024年及之前）**
   - 来源：百度搜索 / arXiv
   - 标注：📚 历史成果

3. **待验证信息**
   - 只有单一来源
   - 标注：⚠️ 待验证

---

## 第7步：生成报告

### 报告结构

```html
1. 基本信息
   - 姓名、职位、机构
   - 数据来源标注

2. 最新动态（最近6个月）
   - 按时间倒序
   - 每条标注来源

3. 当前研究方向
   - 基于最新动态推断
   - 不基于历史论文

4. 关系网络
   - 导师、同事、合作者
   - 基于搜索结果

5. 性格与工作风格
   - 基于公开言行推断
   - 标注"洞察"

6. 沟通建议
   - 基于最新动态和性格分析
   - 可操作、具体

7. 搜索局限性说明
   - 列出未搜索到的信息
   - 建议下一步搜索方向
```

---

## 第8步：输出

### HTML 报告
- 精美排版
- 信息来源标注清晰
- 区分"事实"和"洞察"

### 队列文件
```json
{
  "task": "academic_mentor_intel",
  "name": "xxx",
  "sources_found": ["公众号", "百度新闻", "arXiv"],
  "sources_missing": ["小红书", "Google Scholar"],
  "output": "path/to/result.html"
}
```

---

## 关键检查点

### ✅ 信息来源
- [ ] 每条信息都有来源标注
- [ ] 区分"事实"和"洞察"
- [ ] 未验证信息明确标注

### ✅ 时效性
- [ ] 最新动态优先（6个月内）
- [ ] 不用历史论文判断当前关注点

### ✅ 规范性
- [ ] 没有使用对话历史信息
- [ ] 没有凭空推断
- [ ] 搜索流程完整

---

## 示例：规范 vs 不规范

### ❌ 不规范
```
[目标导师]是中科大博士生，参与DiG蛋白质预测、钙钛矿量子点研究，是Z Bar主理人。
（来源：对话历史，不是搜索结果）
```

### ✅ 规范
```
[目标导师]在2025年1月11日参加科学护卫项目展演，展示AI安全风险。
来源：📰 百度新闻

其他信息未在公开渠道找到。建议搜索：
- 中关村学院官网
- MSRA实习生名单
- 中科大博士生数据库
```

---

**严格遵守这个流程，确保每次分析都是规范化的、可复现的！**
