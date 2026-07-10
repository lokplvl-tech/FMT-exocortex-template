# Ontology: IWE Exocortex Template

> Downstream ontology per SPF.SPEC.002 §4.3.
> References Pack DP (Digital Platform) and SPF concepts. Introduces no new concepts — implementation-level only.
> **§1-4: Platform-space** (updated via `update.sh`). **§5-6: User-space** (local only).

---

## 1. Upstream Dependencies

| Upstream | Level | What Is Used |
|----------|-------|--------------|
| SPF (SPF.SPEC.002) | Base | Entity types, ontology rules, abbreviations |
| PACK-digital-platform (DP) | Pack | Domain concepts, distinctions, platform Architecture |

---

## 2. Concepts Used From the Pack

> Reference concepts from PACK-digital-platform. Definitions are in Pack ontology.md. This section describes how they are used in the Template.

| Term (RU) | Term (EN) | Pack Concept | How Used in the Template |
|-----------|-----------|--------------|--------------------------|
| Среда (IWE) | Environment (IWE) | DP.CONCEPT.002 | Root concept — the Template deploys IWE |
| Экзокортекс-интерфейс | Exocortex Interface | DP.EXOCORTEX.001 | CLAUDE.md + memory/ — core of the Template |
| Platform-space | Platform-space | DP.D.011 | Files updated via update.sh (CLAUDE.md, memory/*.md) |
| User-space | User-space | DP.D.011 | User files (MEMORY.md, DS-strategy/, personal plans) |
| Экстракция знаний | Knowledge Extraction | DP.M.001 | Capture-to-Pack Method in the work Protocol |
| Адаптивная персонализация | Adaptive Personalization | DP.M.004 | MCP ddt — digital twin of the learner |
| Цифровой двойник | Digital Twin | DP.CONCEPT.001 | MCP ddt — metamodel, goals, self-assessment |
| Навигация знаний | Knowledge Navigation | DP.NAV.001 | Gateway iwe-knowledge (mcp.aisystant.com/mcp) — hybrid search across Pack and guides |
| IPO-паттерн | IPO Pattern | DP.ARCH.001 | Component description contract in CLAUDE.md |
| Архитектурная характеристика | Architectural Characteristic | DP.D.010 | ArchGate (ЭМОГССБ) in CLAUDE.md §5 |
| Файл контекста РП | WP Context File | DP.EXOCORTEX.001 | inbox/WP-*.md in DS-strategy |
| Harness (упряжь) | Harness | DP.D.025 | IWE as harness for intellectual work |
| ИИ-система | AI System | DP.ROLE.001 | Claude Code, bot — Role Performers |
| ИТ-система | IT System | DP.SYS.001 | MCP servers, WakaTime — deterministic Components |

---

## 3. Implementation Terminology

> Template-specific concepts at the implementation level. Bound to Pack concepts.

| Term (RU) | Term (EN) | Definition | Pack Concept |
|-----------|-----------|------------|--------------|
| Слой памяти | Memory Layer | Exocortex instruction storage level (Layer 1: MEMORY.md, Layer 2: CLAUDE.md, Layer 3: memory/*.md) | DP.EXOCORTEX.001 |
| Контур системы | Platform Contour | IWE nesting level (L1 Ecosystem → L2 Platform → L3 Template → L4 Personal) | DP.ARCH.001 |
| Ритуал ОРЗ | ORZ Ritual | Session Protocol implementation: Opening → Work → Closing | DP.M.003 |
| WP Gate | WP Gate | Blocking check for the presence of a Work Product in the plan before work begins | DP.EXOCORTEX.001 |
| Capture-to-Pack | Capture-to-Pack | Work milestone check: is there Knowledge to record in the Pack | DP.M.001 |
| АрхГейт (ЭМОГССБ) | ArchGate | Mandatory architectural decision Assessment across 7 characteristics, threshold ≥8 | DP.M.005 |
| Стратегический хаб | Strategy Hub | DS-strategy — governance Repository for plans, Reviews, Sessions | DP.ROLE.012 |
| Placeholder-переменная | Placeholder Variable | `{{VAR}}` — substituted by setup.sh during Template Deployment | — (implementation) |
| Контракт роли | Role Contract | role.yaml + prompts + Scripts in roles/<name>/ | DP.ROLE.001 |
| Реестр РП | WP Registry | Single-source Aggregate of active Work Products: `WP-REGISTRY.md` + `inbox/WP-*.md` in governance Repository, sweep via `scripts/active-wp-sweep.sh` (hub-and-spoke with WORKPLAN.md discontinued, WP-283 Ф-H, May 2026) | DP.ROLE.012 |
| Творческий конвейер | Creative Pipeline | 4 stages of turning a thought into a publication: note → draft → prepared piece → post. Each Artifact must advance or be closed within its TTL | DP.M.003 |
| Guard (страж) | Guard | Automated TTL violation check during strategizing and Day Close | DP.EXOCORTEX.001 |
| DayPlan | DayPlan | Daily plan — Day Open Artifact. Strategist→Human handoff | DP.M.003 |
| WeekPlan | WeekPlan | Weekly plan — strategizing Artifact. Contains Work Products, budgets, focus | DP.M.003 |

---

## 4. Abbreviations (Platform-space)

> Abbreviations used in the Template. Those inherited from upstream are marked with their level.

| Abbreviation | Full Form (RU) | Full Form (EN) | Level |
|--------------|----------------|----------------|-------|
| FPF | Фреймворк первых принципов | First Principles Framework | FPF |
| SPF | Фреймворк вторых принципов | Second Principles Framework | SPF |
| UL | Единый язык | Ubiquitous Language | FPF (DDD) |
| BC | Ограниченный контекст | Bounded Context | FPF (DDD) |
| KE | Экстракция знаний | Knowledge Extraction | SPF |
| FM | Режим ошибки | Failure Mode | SPF |
| WP | Рабочий продукт | Work Product | SPF |
| IPO | Вход-Обработка-Выход | Input-Processing-Output | SPF |
| DP | Цифровая платформа | Digital Platform | Pack |
| IWE | Среда интеллектуальной работы | Intellectual Work Environment | Pack |
| MCP | Протокол контекста модели | Model Context Protocol | Pack |
| ОРЗ | Открытие-Работа-Закрытие | Open-Work-Close | Pack |
| РП | Рабочий продукт (экземпляр) | Work Product (instance) | Pack |
| ЦД | Цифровой двойник | Digital Twin | Pack |
| ЭМОГССБ | 7 арх. характеристик | Evolvability, Scalability, Learnability, Generativity, Speed, Modernity, Security | Pack |
| DS | Downstream-репозиторий | Downstream Repository | Template |
| FMT | Формат (шаблон) | Format (Template) | Template |
| TTL | Срок жизни артефакта | Time To Live | Template |
| HD | Жёсткое различение | Hard Distinction | Template |
| SOTA | Современное состояние практик | State Of The Art | Template |
| SOP | Стандартная операционная процедура | Standard Operating Procedure | FPF |
| DDD | Предметно-ориентированное проектирование | Domain-Driven Design | FPF |
| CLI | Интерфейс командной строки | Command-Line Interface | general |
| API | Программный интерфейс | Application Programming Interface | general |
| LMS | Система управления обучением | Learning Management System | Pack |
| S2R | Формат «Системы-к-ролям» | Systems-to-Roles | SPF |
| PII | Персональные данные | Personally Identifiable Information | general |
| RSS | Лента новостей | Really Simple Syndication | general |
| TG | Telegram | Telegram | general |
| ZP | Нулевые принципы | Zero Principles | Base |

---

<!-- ═══════════════════════════════════════════════════════ -->
<!-- USER-SPACE: Sections below are NOT updated via update.sh -->
<!-- ═══════════════════════════════════════════════════════ -->

## 5. My Glossary

> Your own concepts. Add terms that are important to your work here.
> If a term turns out to be domain-level (useful to other users), the Knowledge Extractor will suggest adding it to the Pack.

| Term (RU) | Term (EN) | Definition | Link to Pack |
|-----------|-----------|------------|--------------|
| _Пример: Утренний ритуал_ | _Morning Ritual_ | _My sequence of session-prep + day-plan_ | _DP.M.003 (ORZ Protocol)_ |

---

## 6. My Abbreviations

> Abbreviations specific to your work. Platform-level abbreviations are in §4 above.

| Abbreviation | Full Form (RU) | Full Form (EN) |
|--------------|----------------|----------------|
| _ПР_ | _Пример расшифровки_ | _Example abbreviation_ |

---

_Downstream ontology per SPF.SPEC.002 §4.3. Upstream: Pack DP (Digital Platform)_
