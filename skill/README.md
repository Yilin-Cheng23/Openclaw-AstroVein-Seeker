# 学术导师深度画像 (Academic Mentor Intelligence)

**比 Deep Research 更 Deep 的学术关系分析工具**

## 🎯 这个 Skill 做什么？

深度挖掘学术导师/同门的完整画像，生成可操作的沟通建议和破冰策略。

**核心特点：**
- 📡 **多源实时搜索**：微信公众号、小红书、arXiv、百度、Google Scholar
- 🧠 **深度洞察**：性格、偏好学生类型、人格魅力、人情世故
- ⏰ **实时性优先**：最近3-6个月动态，而非历史论文
- 📊 **完整时间线**：历史成果 + 最新动态
- 💡 **可操作建议**：沟通技巧、破冰方法、项目机会

---

## 📦 安装

```bash
cd ~/.openclaw/workspace
clawhub install academic-mentor-intel
```

---

## 🚀 快速开始

### 基本用法

```bash
python3 skills/academic-mentor-intel/scripts/analyze_mentor.py \
  --name "[目标师兄]" \
  --institution "中关村人工智能研究院" \
  --output result.html
```

### 包含导师网络

```bash
python3 skills/academic-mentor-intel/scripts/analyze_mentor.py \
  --name "[目标导师]" \
  --advisor "[导师的导师]" \
  --output result.html
```

### 多源验证模式

```bash
python3 skills/academic-mentor-intel/scripts/analyze_mentor.py \
  --name "[目标师兄]" \
  --verify \
  --output result.html
```

---

## 📚 示例

查看 `examples/zheng_shuxin.html` 了解完整输出效果。

**示例特点：**
- ✅ 完整时间线：2024 Science论文 → 2026最新动态
- ✅ 核心转变：AI for Science → AI for Scientist
- ✅ 资源解析：[导师的导师]杠杆 + 中关村两院生态
- ✅ 深度洞察：理想主义的实干家、重视产业化、萌生创业想法
- ✅ 可操作建议：参加黑客松、关注OmniScientist、AI商学院活动

---

## 🔧 工作原理

1. **多源搜索**：
   - 微信公众号（wechat-article skill）
   - 小红书（web_fetch）
   - arXiv 最新论文
   - 百度实时新闻
   - Google Scholar（如果可访问）

2. **时间线整合**：
   - 历史成果（代表性论文、奖项）
   - 最新动态（最近3-6个月）

3. **深度分析**：
   - 性格推断（从公开言行）
   - 学生偏好（他喜欢什么特质？）
   - 资源分析（导师杠杆、机构生态）

4. **可操作建议**：
   - 沟通技巧
   - 破冰策略
   - 项目机会
   - 长期维护

5. **生成HTML报告**：
   - 精美排版
   - 数据来源标注
   - 多源验证标记

---

## 📖 相关文档

- `SKILL.md` - 完整 Skill 说明
- `references/search-strategy.md` - 多源搜索策略
- `examples/zheng_shuxin.html` - 完整示例

---

## 🤝 适用场景

- 🎯 研究生选导师前的深度调研
- 💬 准备与导师的第一次见面
- 🤝 寻找学术合作机会
- 📊 了解同门/师兄师姐
- 🚀 加入实验室前的团队分析

---

## ⚠️ 伦理规范

- ✅ 使用公开信息
- ✅ 用于学术交流、合作破冰
- ❌ 不用于隐私侵犯、骚扰、商业利益

---

## 📝 反馈与改进

欢迎提供反馈和改进建议！

---

**让学术人际关系管理变得简单、深入、可操作！**
