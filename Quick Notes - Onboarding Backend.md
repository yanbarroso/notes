Front: React, 


Apps servindo basicamente consulta via APIs na primeira camada

Iaas, Paas, Aas

Diagrama C4: representando em forma de cascata: Onde está hospedado o recurso

App service azure (Paas): sobe um app pra nuvem, hospedagem focado no uso, se ninguém usa zera o custo, estrutura em nuvem descentralizada (varia conforme o usuário)
![[Pasted image 20261020091150.png]]

Azure Functions (Paas): sobe um código pra nuvem, event-driven, focada em serverless, aconteceu algo -> reage, padrão próprio de comunicação
![[Pasted image 20261020091130.png]]

Azure Virtual Machine (Iaas): máquina virtual rodando 24h, responsável por disponibilização, hospedagem, recursos e lidar com eventos
![[Pasted image 20261020091141.png]]


Azure Kubernetes Service (meio termo entre Iaas e Paas): aplicação executando dentro de um cluster da kubernetes (pesquisar cluster computing), executa dentro de uma pod, que executa dentro de uma node, que executa dentro de uma cluster.![[Pasted image 20261020091344.png]]

Azure Storage Account: blob fileserver, um armazenamento na nuvem
![[Pasted image 20261020100644.png]]

Por que separar os serviços em diferentes hospedagens: resiliência; se um cai outro não; importante para segmentar partes do negócio para futuras oportunidades (por exemplo se quiser vender apenas o oilspill para outros usos)

Middleware: camada de software que atua como ponte entre diferentes partes da aplicação

Digital Backend (digital-web-backend): construído usando blueprint do flask, swagger, monolito, não está padronizado, repo velho herdado

Oilspill (digital-micro-oilspill): server e worker (ambos no mesmo repositório), server  -> fila do redis -> worker (consulta a exec externo feito por pesquisador) (consome dados metaoceanográficos) 
![[Pasted image 20261020103440.png]]

RBAC (Role Based Access Control) (digital-micro-rbac) (app service): Linguagem go framework gin, grant: acesso individual de recursos, role: acesso conforme conjunto de negócios (admin), plano: limite superior do que uma empresa pode ver (empresa que não precisa de simulação de deriva de óleo não vê isso)
![[Pasted image 20261020103455.png]]

Function Cache (digital-functions-cache): consome dados de embarcação do redis, reconcilia com banco (quando precisa)  

Apache Airflow (ocp-digital-airflow): kubernetes, centralizador de recorrencias, DAG (directed acyclic graph) pequenas etapas sequenciais


tabelas banco importantes:
nautical position nautical sat position

event nautical unified (...)

Pesquisar depois 

Timescale db postgresql OLTP (online transaction process) OLAP (Online Analytical Processing)