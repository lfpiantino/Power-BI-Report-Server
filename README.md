# Power-BI-Report-Server
Documentação técnica da implantação e estruturação do Power BI Report Server em ambiente corporativo. Inclui práticas recomendadas, exemplos de relatórios, configurações de segurança e integração com Active Directory.
# Power BI Report Server - Implantação Corporativa

Este documento descreve o processo de instalação, configuração e boas práticas utilizadas na implantação do Power BI Report Server em um ambiente corporativo, com foco em segurança, performance e integração com sistemas legados.

---

## 🔧 Requisitos do Ambiente

- **Sistema Operacional**: Windows Server 2019
- **Banco de Dados**: SQL Server 2019 Standard ou Enterprise
- **Gateway de Dados**: Opcional, usado para integração com serviços externos
- **Ambiente com Active Directory**: Sim

---

## 🛠️ Etapas Realizadas

### 1. Instalação do SQL Server
- SQL Server instalado em servidor dedicado
- Criados bancos `ReportServer` e `ReportServerTempDB`
- Autenticação mista (Windows + SQL Server)

### 2. Instalação do Power BI Report Server
- Instalado via portal oficial da Microsoft
- Licenciamento ativado via chave do SQL Server Enterprise
- Web Service URL e Web Portal configurados

### 3. Configuração do Report Server
- Permissões atribuídas por roles (`System Administrator`, `Publisher`)
- Exportações ativadas: PDF, Excel, PowerPoint
- Suporte a relatórios paginados (.rdl) e Power BI (.pbix) ativado

### 4. Integração com Active Directory
- Autenticação SSO via LDAP
- Acesso segmentado por grupos de segurança (ex: `BI_Equipe`, `BI_Admins`)

### 5. Otimizações Aplicadas
- Estrutura de pastas criada por área (ex: "Financeiro", "TI", "Operações")
- Cache ativado para relatórios com grande volume de dados
- Monitoramento de logs e auditoria habilitados

---

## 📊 Exemplos de Relatórios

| Área         | Nome do Relatório           | Finalidade                                           |
|--------------|-----------------------------|------------------------------------------------------|
| Financeiro   | Painel de Glosas            | Análise detalhada por categoria e origem             |
| TI           | Dashboard de Infraestrutura | Indicadores de servidores, rede e links externos     |
| Operacional  | Produção Assistencial       | Volume de atendimentos por especialidade e unidade   |

---

## 🔐 Segurança

- Backups automatizados do banco `ReportServer`
- Autenticação integrada com o domínio (Kerberos)
- Firewall com regras de acesso segmentadas
- Conexões seguras com SSL/TLS

---

## 📂 Organização de Diretórios

