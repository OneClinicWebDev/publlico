# OneClinic

**Sistema de Gestão Inteligente para Clínicas de Estética (SaaS Profissional)**

---

## Aviso Legal

Este projeto é de propriedade intelectual privada. Todo o conceito, arquitetura, fluxos de negócio, documentação e código-fonte são protegidos por direitos autorais.

**É estritamente proibido:**
- Copiar, reproduzir ou distribuir qualquer parte deste projeto sem autorização expressa  
- Utilizar a ideia, os fluxos ou a estrutura como base para projetos derivados  
- Comercializar, sublicenciar ou compartilhar o acesso ao sistema ou sua documentação  

O uso não autorizado está sujeito às penalidades previstas na legislação brasileira de propriedade intelectual (Lei 9.609/98 e Lei 9.610/98) e na Lei Geral de Proteção de Dados (Lei 13.709/18).

Todos os direitos reservados.

---

## O Problema

Clínicas de estética de pequeno porte no Brasil ainda operam com:

- **Agendas em papel** — sem controle de horários, conflitos e cancelamentos  
- **Planilhas manuais** — financeiro fragmentado, sem visão real do caixa  
- **Estoque no "olhômetro"** — produtos acabam sem aviso, compras por impulso  
- **Fichas de papel** — histórico do cliente perdido, sem rastreabilidade  
- **Zero controle de inadimplência** — sessões realizadas e nunca cobradas  
- **Comunicação desorganizada** — lembretes esquecidos, clientes que não voltam  

O resultado: perda de receita, retrabalho, clientes insatisfeitos e um dono de clínica sobrecarregado.

---

## A Solução

O **OneClinic** é um sistema SaaS completo, desenvolvido especificamente para a realidade de clínicas de estética. Ele substitui cadernos, planilhas e aplicativos desconectados por uma única plataforma integrada.

O sistema foi projetado para ser:

- **Simples** → uso imediato, sem treinamento técnico  
- **Flexível** → regras adaptáveis por clínica  
- **Escalável** → preparado para crescimento e monetização  

---

## Arquitetura do Sistema

O OneClinic foi projetado como um sistema **multi-tenant**, onde múltiplas clínicas utilizam a mesma aplicação com isolamento total de dados.

### 🔑 Princípios Técnicos

- Uso de **UUID** como chave primária  
- Isolamento por `clinica_id`  
- Estrutura preparada para **Row Level Security (RLS)**  
- Modelagem orientada a domínio (DDD simplificado)  

---

## Engine de Configuração Dinâmica

O sistema utiliza uma tabela central chamada `parametros`, que funciona como um motor de regras configurável.

Com isso, cada clínica pode definir:

- Status de agendamento (Confirmado, Cancelado, Em espera, etc)  
- Status de parcelas (Pago, Pendente, Atrasado)  
- Métodos de pagamento (Pix, Cartão, Dinheiro)  
- Canais de comunicação (WhatsApp, Email)  

**Benefício:**  
Não é necessário alterar o código para mudar regras de negócio.

---

## O Que o OneClinic Faz

### Gestão de Clientes (CRM)
Cadastro completo com histórico unificado: sessões, pagamentos, planos, cupons e comunicações em um único lugar.

---

### Agenda Inteligente
- Agendamentos por cliente e profissional  
- Status dinâmico configurável  
- Controle de presença e histórico  

---

### Planos e Assinaturas (Recorrência)

O sistema permite vender pacotes e planos recorrentes.

Controle automático de:
- Sessões restantes  
- Validade  
- Consumo por agendamento  

---

### Cupons e Anti-Fraude

Sistema completo de cupons com:

- Limite de uso  
- Aplicação direta no agendamento  
- Rastreamento via `cupons_usos`  

**Benefício:** evita fraudes e garante controle total.

---

### Controle de Estoque

- Registro de movimentações (entrada/saída)  
- Rastreabilidade completa  
- Base para automação de consumo por atendimento  

---

### Financeiro Profissional

- Registro de pagamentos por agendamento  
- Suporte a múltiplos métodos (dinâmicos)  
- Parcelamento  
- Controle de inadimplência  

---

### Comunicação com Clientes

- Registro de mensagens enviadas  
- Controle de status (enviado, erro, lido)  
- Preparado para integração com APIs externas  

---

## Fluxo Principal do Sistema

### Criação de um Agendamento

1. Validação de horário disponível  
2. Aplicação de cupom (opcional)  
3. Verificação de assinatura ativa  
4. Consumo de sessão **ou** geração de pagamento  
5. Criação de parcelas (se necessário)  

---

## Controle de Acesso

O sistema possui três níveis:

**Administrador**
- Controle total do sistema  
- Configurações, financeiro e relatórios  

**Secretário(a)**
- Operação da clínica  
- Agenda, clientes, financeiro básico  

**Profissional**
- Acesso à própria agenda  
- Registro de atendimentos  

---

## Para Quem é

- Clínicas de estética (1 a 10 profissionais)  
- Studios de beleza  
- Espaços terapêuticos  
- Negócios de serviços recorrentes  

---

## Diferenciais do Sistema

- Arquitetura SaaS pronta para escala  
- Motor de regras dinâmico (sem hardcode)  
- Controle real de recorrência (planos e sessões)  
- Sistema antifraude de cupons  
- Financeiro estruturado (nível ERP leve)  

---

## Status do Projeto

Em desenvolvimento ativo.

A arquitetura e modelagem já estão consolidadas e prontas para produção.  
Os próximos passos envolvem implementação de backend, frontend e deploy.

---

## Roadmap

- [ ] Backend (API e regras de negócio)  
- [ ] Interface da agenda  
- [ ] Módulo financeiro completo  
- [ ] Integração com WhatsApp  
- [ ] Deploy em ambiente SaaS  

---

## Autor

**Wedley Silva Schmoeller**  
Engenharia de Software  

---

## Licença

Uso restrito. Todos os direitos reservados.

---

*OneClinic ® — Sistema SaaS para clínicas modernas*
