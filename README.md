# Portefólio de Cibersegurança - Projetos Autónomos

Bem-vindo ao meu portefólio. Este espaço é dedicado à documentação de laboratórios práticos e cenários reais resolvidos durante o meu percurso de especialização em Cibersegurança.

---

## Projeto 1: Análise e Classificação de Indicadores de Compromisso (IoCs) com a Pyramid of Pain

### 1. Introdução e Objetivo
Como futuro Analista de SOC (Security Operations Center), compreender a eficácia das defesas de uma infraestrutura é fundamental. Este projeto demonstra a aplicação prática do conceito da **Pyramid of Pain (Pirâmide da Dor)**, focado em entender o impacto e a "dor" que causamos a um cibercriminoso ao bloquear diferentes tipos de Indicadores de Compromisso (IoCs).

O objetivo principal foi analisar cenários práticos e categorizar os artefactos deixados por um atacante de acordo com o nível de dificuldade que ele enfrentará para contornar as nossas defesas.

---

### 2. O Conceito Técnico
A pirâmide está dividida em 6 camadas. Quanto mais alto subimos na pirâmide, mais difícil e dispendioso é para o atacante alterar o seu comportamento, tornando a nossa deteção muito mais robusta:

* **Hash Values (Trivial):** Assinaturas únicas de ficheiros (MD5, SHA-256). Mudar um único bit no ficheiro altera o hash.
* **IP Addresses (Easy):** Endereços de rede. O atacante pode mudar de IP facilmente usando VPNs ou proxies.
* **Domain Names (Simple):** Nomes de domínio (ex: `malicious-site.com`). Exige registo, mas continua a ser simples de alterar.
* **Network/Host Artifacts (Annoying):** Rastros na rede (User-Agents) ou no sistema operativo (chaves de registo). Dá trabalho ao atacante modificar.
* **Tools (Challenging):** Software usado para o ataque (ex: Mimikatz, Nmap). Obriga o atacante a reconfigurar ou programar ferramentas novas.
* **TTPs (Tough):** Táticas, Técnicas e Procedimentos. O comportamento/metodologia do atacante. Mudar as TTPs obriga o adversário a reaprender o seu próprio *modus operandi*.

<br>
<img src="piramide.jpg.jpg" alt="Estrutura da Pirâmide da Dor" width="500">
<br>

---

### 3. Resolução do Caso Prático
Utilizando o ambiente laboratorial simulado do TryHackMe, foi necessário analisar seis descrições de comportamentos e infraestruturas de um atacante para associá-las corretamente aos níveis correspondentes da pirâmide. 

A análise baseou-se nos seguintes critérios:
1. Identificação de assinaturas e artefactos específicos de campanhas de *typo-squatting* (Domínios).
2. Associação de tráfego de Comando e Controlo (C2) a artefactos de rede.
3. Mapeamento dos planos gerais do adversário diretamente ao nível de TTPs (o topo da pirâmide).

<br>
<img src="cartoes.jpg.jpg" alt="Mapeamento de Indicadores Práticos" width="500">
<br>

Após a correta distribuição de todos os vetores e prompts no simulador, o desafio foi concluído com sucesso, gerando a assinatura de validação técnica (*flag*) do laboratório.

<br>
<img src="flag.jpg.jpg" alt="Validação Final do Laboratório" width="500">
<br>

---

### 4. Conclusão e Mitigação no Mundo Real
A conclusão deste laboratório reforça que uma defesa de SOC moderna não pode depender apenas de listas de IPs ou Hashes conhecidos (a base da pirâmide), pois são fáceis de contornar. 

Para criar resiliência a longo prazo, as equipas de Blue Team devem focar-se na criação de regras de deteção baseadas em **TTPs** e **Ferramentas** (recorrendo a frameworks como o MITRE ATT&CK), garantindo que, mesmo que o atacante mude de infraestrutura, o seu comportamento suspeito seja detetado e bloqueado imediatamente.
