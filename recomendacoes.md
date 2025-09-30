# Recomendações de Mitigação (detalhado)

1. Autenticação
   - Habilitar MFA para acessos críticos (SSH, painéis administrativos, FTP corporativo).
   - Implementar passwords policies (complexidade, rotação/expiração controlada).

2. Proteção contra brute force
   - Account lockout após X tentativas falhas.
   - Progressive delay entre tentativas.
   - Rate-limiting por IP e por conta.

3. Proteção de aplicações web
   - WAF (Web Application Firewall) para bloquear padrões maliciosos.
   - Validar e proteger contra CSRF (tokens) e implementar proteções anti-automation.
   - Monitorar e aplicar proteção contra password spraying.

4. Monitoramento e detecção
   - SIEM para correlação de eventos e geração de alertas.
   - IDS/IPS para detectar padrões de ataque (ex.: bursts de tentativas de autenticação).
   - Logs centralizados e retenção apropriada para investigação.

5. Hardening e superfície de ataque
   - Desabilitar serviços desnecessários (ex.: SMBv1).
   - Aplicar patches regulares no sistema e software.
   - Segmentar rede (VLANs, firewalls internos) para reduzir impacto lateral.

6. Treinamento e governança
   - Treinamento de conscientização para administradores e usuários.
   - Processos de resposta a incidentes e playbooks.
   - Política formal de autorização para testes (pentests) e auditorias.
