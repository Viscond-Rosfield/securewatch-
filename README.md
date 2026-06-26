# 🛡️ SecureWatch — Plataforma de Análise de Segurança

Plataforma web para análise de ameaças cibernéticas: URLs maliciosas, malware, reputação de IPs e vulnerabilidades conhecidas (CVEs). Roda 100% no navegador — sem instalação, sem backend, sem dados armazenados em servidores próprios.

🔗 **Demo:** https://viscond-rosfield.github.io/securewatch-/

---

## Funcionalidades

### 🔗 Análise de URLs
- Verifica se links são maliciosos ou de phishing via **VirusTotal** (70+ engines)
- Consulta paralela na base pública do **URLhaus (abuse.ch)**
- Suporte a **análise em lote** (várias URLs de uma vez)
- Exibe detalhamento por engine com nome da ameaça detectada

### 🦠 Análise de Arquivos / Malware
Três formas de analisar sem executar nada na sua máquina:

| Modo | Como funciona |
|---|---|
| **Verificar Hash** | Cole um MD5, SHA-1 ou SHA-256 e consulte no VirusTotal |
| **Enviar Arquivo** | Arquivo vai do browser direto à API do VT — nunca é salvo ou executado localmente |
| **Analisar por Link** | Cole o link de download (ex: anexo de e-mail) — o VT busca e analisa por você |

Inclui calculadora de hash SHA-256 local: o hash é gerado no próprio browser, sem upload.

### 🌐 Análise de IP e Domínio
- Reputação de IPs via **AbuseIPDB** (score de abuso, total de relatórios, ISP, país)
- Análise de domínios via **VirusTotal**
- Identifica IPs usados em ataques, proxies maliciosos e botnets

### 🛡️ Pesquisa de CVEs
- Busca vulnerabilidades na base oficial **NIST NVD** — sem necessidade de chave de API
- Suporte a busca por ID (`CVE-2021-44228`) ou palavra-chave (`Apache`, `Log4j`)
- Exibe score CVSS, severidade, descrição e link direto para o NVD
- Atalhos rápidos para CVEs famosas (Log4Shell, PrintNightmare, etc.)

### 📄 Gerador de Relatório
- Compila todas as análises em um relatório HTML formatado
- Campos configuráveis: organização, analista, nível de confidencialidade, destinatários
- Gera resumo executivo com contagem de ameaças, suspeitos e itens limpos
- Seção automática de **ações recomendadas** para cada ameaça detectada
- Copia o HTML pronto para colar no corpo de um e-mail

---

## APIs utilizadas

| API | Uso | Chave necessária |
|---|---|---|
| [VirusTotal v3](https://developers.virustotal.com/) | URLs, arquivos, hashes, domínios | ✅ Gratuita |
| [AbuseIPDB](https://www.abuseipdb.com/api) | Reputação de IPs | ✅ Gratuita |
| [URLhaus (abuse.ch)](https://urlhaus-api.abuse.ch/) | Verificação de URLs maliciosas | ❌ Sem chave |
| [NIST NVD](https://nvd.nist.gov/developers) | Busca de CVEs | ❌ Sem chave |

> Sem chaves configuradas, a plataforma opera em **modo demo** com dados simulados para visualização das funcionalidades.

---

## Como usar

### 1. Acessar online
Abra diretamente: **https://viscond-rosfield.github.io/securewatch-/**

### 2. Rodar localmente
Baixe o `index.html` e abra no navegador. Nenhuma dependência ou instalação necessária.

### 3. Configurar APIs
Acesse ⚙️ **Config** na plataforma e insira suas chaves de API. Elas ficam salvas apenas no `localStorage` do seu navegador — nunca são enviadas a terceiros.

Para obter as chaves gratuitamente:
- **VirusTotal:** https://www.virustotal.com/gui/join-us
- **AbuseIPDB:** https://www.abuseipdb.com/register

---

## Fluxo recomendado para análise de anexos suspeitos

```
Recebeu arquivo suspeito por e-mail?
        │
        ▼
Copie o link do anexo (botão direito → "Copiar link")
        │
        ▼
Cole em: 🦠 Arquivos → aba "Analisar por Link"
        │
        ▼
VT baixa e analisa nos servidores dele
        │
        ▼
Resultado + adicione ao Relatório para enviar ao time
```

---

## Privacidade e segurança

- Nenhum dado é enviado a servidores próprios — toda comunicação é direta entre o browser e as APIs (VirusTotal, AbuseIPDB, NIST)
- Chaves de API ficam apenas no `localStorage` do seu navegador
- O cálculo de hash local **nunca faz upload** do arquivo — o hash é gerado em memória pelo browser
- Arquivos enviados via "Enviar Arquivo" vão direto à API do VirusTotal sem intermediários

---

## Tecnologias

- HTML5 / CSS3 / JavaScript puro (zero dependências, zero frameworks)
- Web Crypto API (cálculo de hash SHA-256 local)
- GitHub Pages (hospedagem)

---

## Licença

MIT — livre para uso, modificação e distribuição.
