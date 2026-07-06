---
card_type: conveyor-task
double_exit:
  capture: что появится в знании (distinctions / memory / Pack)
  code: что появится в коде / артефакте
estimate: 45m
name: краткое-имя-задачи
stations:
- Постановка
- Открытие
- Проектирование
- Работа
- Проверка
- Закрытие
tags:
- platform/scripts
tier: T4+
verification_class: closed-loop
wp: WP-NNN
---
<body>

# Card: <task name>

> Fill in this template and complete all 6 Pipeline stations. Dual output is required.

## Trigger

What happened? Why did this task appear?

## Inputs

- Which files / data / access are required?
- Which dependencies (Work Products, people, Infrastructure)?

## Outputs

1. **Code:** what will change / be created?
2. **Capture:** what Knowledge will be recorded?

## Stations

1. **Framing** — this card is the input.
2. **Opening** — WP Gate: Role = ..., class = ..., model = ...
3. **Design** — IntegrationGate/ArchGate (if needed).
4. **Work** — code + capture simultaneously.
5. **Review** — checklist:
   - [ ] criterion 1
   - [ ] criterion 2
   - [ ] capture added
6. **Closing** — PR, merge (lead developer TD1+TA4 / pilot), Registry update.

## Acceptance Criterion

What does "done" mean? A list of verifiable conditions.

## Failure Mode

If not closed within N — escalate to ...

</body>