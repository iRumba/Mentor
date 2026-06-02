# OWASP Top 10

## OWASP Top 10 (2021)
- Список наиболее критичных рисков безопасности веб-приложений.
- Обновляется каждые 3-4 года.

## Основные категории
1. **Broken Access Control** — неправильное разграничение доступа. Самая частая проблема.
2. **Cryptographic Failures** — проблемы с шифрованием (HTTP вместо HTTPS, слабые хеши).
3. **Injection** — SQL, NoSQL, OS Command, LDAP injection.
4. **Insecure Design** — архитектурные недостатки (отсутствие rate limiting, небезопасный reset пароля).
5. **Security Misconfiguration** — дефолтные учетки, не отключенные отладка/метаданные.
6. **Vulnerable and Outdated Components** — устаревшие библиотеки с CVE.
7. **Identification and Authentication Failures** — слабые пароли, отсутствие MFA.
8. **Data Integrity Failures** — обновления ПО без верификации, небезопасные десериализации.
9. **Security Logging and Monitoring Failures** — отсутствие логов, недостаточный мониторинг.
10. **SSRF** (Server-Side Request Forgery) — сервер делает запросы по невалидированному URL.

## Важно для интервью
- OWASP Top 10 — базовая грамотность безопасности для любого веб-разработчика.
- Не только знать категории, но и примеры уязвимостей по каждой.
- Инструменты: SAST (SonarQube, Roslyn analyzers), DAST (OWASP ZAP), SCA (Dependabot, Snyk).
- ASVS (Application Security Verification Standard) — детальный стандарт проверки безопасности.
