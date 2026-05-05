# Economics-Literature-Review-Skills
在现有高star文献综述skill的基础上，采取更加针对经济学的框架进行训练，一键生成一篇完整的经济学文献综述。可以进行长篇文献综述撰写，也可以修改成投稿类段落文献综述。

│  🎯 核心功能                                                         │
│  ├── 1. 文献质量检查（期刊评级标准）                                    │
│  │   ├── 评级来源：西南财经大学研究生院期刊评级标准                       │
│  │   ├── 筛选规则：所有引用文献必须达到B级及以上                          │
│  │   └── 低于B级 → 自动标记并搜索替代文献                               │
│  │                                                                  │
│  ├── 2. 期刊评级查询                                                  │
│  │   ├── 中文顶级：经济研究、管理世界、中国社会科学、金融研究等            │
│  │   └── 英文顶级：AEQ、QJE、JPE、RES、Econometrica等                  │
│  │                                                                  │
│  └── 3. 低质量期刊自动替换                                            │
│      ├── 触发条件：期刊低于B级                                         │
│      ├── 搜索优先级：A级 > B级 > 保留标注                              │
│      └── 替换规则：主题相似度>0.7 + 年份更新 + 被引量优先               │

│  🔄 8阶段工作流                                                       │
│  ├── Phase 0: Session Log      → 创建会话目录                         │
│  ├── Phase 1: Query Analysis   → 生成关键词（含期刊级别筛选）           │
│  ├── Phase 2: Parallel Search   → 浏览器自动化检索                     │
│  ├── Phase 3: Deduplication     → 去重（含期刊级别检查）                 │
│  ├── Phase 4: Verification      → 元数据校验（含期刊级别验证）            │
│  ├── Phase 5: Data Export       → 导出文献信息                        │
│  ├── Phase 6: Paper Analysis    → 单篇深度分析（含期刊质量评级）          │
│  ├── Phase 7: Citation Format    → GB/T 7714-2015格式化                │
│  └── Phase 8: Synthesis         → 综述生成（仅使用B级以上文献）           │

│  📊 输出文件                                                           │
│  ├── literature_quality_report.md  → 文献质量检查报告                  │
│  ├── papers_to_replace.md          → 待替换低质量文献清单                │
│  ├── replacement_candidates.md     → 候选替换文献                      │
│  ├── final_references.md           → 仅含B级以上的高质量文献             │
│  └── literature_review.md          → 最终综述                          │

│  ⚡ 触发关键词                                                         │
│  "文献质量检查" | "期刊评级" | "替换文献" | "B级以上" | "帮我找文献"     │
│                                                                     │

│  🔗 依赖                                                               │
│  ├── browser  → 数据库检索（必需）                                      │
│  ├── web_search → 辅助搜索（可选）                                     │
│  └── docx     → 生成Word（可选）                                       │

需校园网认证
版本	v3.1.0	v5.0.0（站在巨人肩上再开发）
