# 文献综述技能 - 通用版

## 技能定位

这是一个**通用型经济管理类文献综述Skill**，适用于任何经济领域的研究主题。

---

## 核心功能

### 1. 文献质量检查（期刊评级标准）

**评级来源**：西南财经大学研究生院期刊评级标准
**评级地址**：https://graduate.swufe.edu.cn/fj/5C24AC8E1493A660154FC7C956F_66DBC22E_616DAF.pdf

**评级等级**：
- **A级期刊**：国际顶尖期刊 + 国内顶级期刊
- **B级期刊**：国内外权威期刊
- **C级期刊**：国内外重要期刊
- **D级期刊**：国内外一般期刊

**筛选规则**：
- 所有引用文献的期刊必须为**B级及以上**
- 低于B级的期刊将被标记为"待替换"
- 系统将自动搜索更高质量的替代文献

### 2. 期刊评级查询

**查询方式**：在CNKI检索时，可使用期刊名称+期刊级别进行筛选

**CNKI筛选示例**：
```
CSSCI来源期刊
北大核心
```

**常见B级及以上期刊示例**：

**中文顶级（B级以上）**：
- 《经济研究》
- 《管理世界》
- 《经济学（季刊）》
- 《中国工业经济》
- 《金融研究》
- 《财政研究》
- 《税务研究》
- 《世界经济》

**英文顶级（SCI/SSCI Q1）**：
- American Economic Review
- Quarterly Journal of Economics
- Journal of Political Economy
- Review of Economic Studies
- Econometrica
- Journal of Finance
- Journal of Monetary Economics
- Review of Financial Studies

---

## 8阶段工作流（含质量控制）

```
Phase 0: Session Log      → 创建会话目录
Phase 1: Query Analysis   → 生成关键词（含期刊级别筛选）
Phase 2: Parallel Search  → 浏览器自动化检索（优先B级以上期刊）
Phase 3: Deduplication    → 去重（含期刊级别检查）
Phase 4: Verification     → 元数据校验（含期刊级别验证）
Phase 5: Data Export      → 导出文献信息
Phase 6: Paper Analysis   → 单篇深度分析（含期刊质量评级）
Phase 7: Citation Format  → GB/T 7714-2015格式化
Phase 8: Synthesis        → 综述生成（仅使用B级以上文献）
```

---

## Phase 4: Verification（期刊质量验证）

### 期刊级别判定规则

```python
def check_journal_rating(journal_name):
    """
    检查期刊是否达到B级以上
    返回: (is_acceptable, rating, alternative_suggestions)
    """
    # A级期刊列表（国际顶尖+国内顶级）
    A_level = [
        "经济研究", "管理世界", "中国社会科学",
        "American Economic Review", "Quarterly Journal of Economics",
        "Journal of Political Economy", "Econometrica", ...
    ]

    # B级期刊列表（国内外权威）
    B_level = [
        "经济评论", "经济学季刊", "金融研究", "财政研究",
        "税务研究", "世界经济", "南开管理评论", "中国工业经济",
        "Journal of Finance", "Journal of Monetary Economics", ...
    ]

    # 检查逻辑
    if journal_name in A_level:
        return (True, "A级", None)
    elif journal_name in B_level:
        return (True, "B级", None)
    else:
        # 搜索替代文献
        alternatives = search_better_alternatives(journal_name)
        return (False, "低于B级", alternatives)
```

---

## Phase 6: Paper Analysis（单篇分析模板）

### 输出格式

```markdown
**文章[N]：[Title]**
**期刊**: [Journal Name] - [B级/A级/低于B级]
**作者**: [Authors]
**年份**: [Year]
**主要观点和结论**: [Summary]
**局限性**: [Limitations]
**研究贡献**: [Contributions]
**期刊评级说明**: [Rating Justification]
**参考文献格式**: [GB/T 7714-2015]
```

---

## 低质量期刊替换流程

### 触发条件

当文献的期刊级别低于B级时，触发替换流程：

```
低质量文献检测
    ↓
提取关键词/主题词
    ↓
在CNKI/WOS中搜索同等主题的B级以上期刊
    ↓
如找到更高级别期刊 → 替换
如未找到 → 保留但标注"建议升级"
```

### 搜索优先级

1. 同主题的A级期刊文章
2. 同主题的B级期刊文章
3. 其他权威数据库同等质量文章

### 替换规则

- 原文献主题 vs 候选文献主题相似度 > 0.7 → 可替换
- 候选文献年份更新 → 优先替换
- 候选文献被引量更高 → 优先替换

---

## 通用关键词生成

### 适用于所有经济管理类研究

**中文通用关键词**：
- 研究主题关键词（根据用户输入提取）
- 研究方法：实证研究、理论分析、计量模型、DID、RD
- 研究对象：企业、政府、家庭、区域
- 经济学分支：宏观经济学、微观经济学、金融学、财政学

**英文通用关键词**：
- Economic methodology keywords
- Management research keywords
- Financial keywords
- Public economics keywords

---

## 输出文件说明

| 文件 | 内容 |
|------|------|
| `literature_quality_report.md` | 文献质量检查报告（含期刊评级） |
| `papers_to_replace.md` | 需要替换的低质量文献清单 |
| `replacement_candidates.md` | 候选替换文献 |
| `final_references.md` | 仅含B级以上的高质量文献清单 |
| `literature_review.md` | 最终综述（仅使用B级以上文献） |

---

## 触发关键词

- "文献质量检查"
- "期刊评级"
- "替换文献"
- "B级以上"
- "经济研究"
- "帮我找文献"
- "写综述"

---

## 依赖 Skills

- **browser** - 数据库检索（必需）
- **web_search** - 辅助搜索（可选）
- **docx** - 生成Word（可选）

---

## 版本信息

- **当前版本**: 5.0.0
- **创建日期**: 2026-05-04
- **作者**: zncumac
- **评级标准来源**: 西南财经大学研究生院期刊评级办法

---

## 附录：西南财经大学期刊评级标准（简要）

根据PDF内容，评级标准分为：

### A+级
- 国际顶级期刊（如AER, QJE, JPE, RES, Econometrica）
- 国内顶级（《经济研究》、《管理世界》）

### A级
- 国际权威期刊（SCI/SSCI一区）
- 国内权威（《中国社会科学》、《经济学季刊》等）

### B级
- 国际重要期刊（SCI/SSCI二区）
- 国内重要（CSSCI来源期刊、北大核心）

### C级/D级
- 其他国内外期刊

**重要**：本研究要求所有引用文献达到**B级及以上**