# BOMSenso

[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://docs.docker.com/compose/)
[![CycloneDX](https://img.shields.io/badge/BOM-OWASP_CycloneDX-E3222D)](https://owasp.org/www-project-cyclonedx/)
[![Jupyter Lab](https://img.shields.io/badge/Jupyter-Lab-F37626?logo=jupyter&logoColor=white)](https://quay.io/repository/jupyter/pytorch-notebook?tab=tags&tag=cuda12-python-3.11.8)
[![LangChain](https://img.shields.io/badge/LangChain-1.3.13-white?logo=langchain&logoColor=green)](https://github.com/langchain-ai/langchain/releases/tag/langchain%3D%3D1.3.13)
[![LangChain Core](https://img.shields.io/badge/LangChain_Core-1.4.9-white?logo=langchain&logoColor=green)](https://pypi.org/project/langchain-core/1.4.9/)
[![LangGraph](https://img.shields.io/badge/LangGraph-1.2.9-white?logo=langchain&logoColor=green)](https://github.com/langchain-ai/langgraph/releases/tag/1.2.9)
[![LibOQS (Post-Quantum)](https://img.shields.io/badge/LibOQS_PQC-0.16.0-4B0082?logo=c&logoColor=white)](https://github.com/open-quantum-safe/liboqs/releases/tag/0.16.0)
[![LazyGraphRAG](https://img.shields.io/badge/Feature-LazyGraphRAG-8A2BE2)](#)
[![Ollama](https://img.shields.io/badge/Ollama-0.33.2-white?logo=ollama&logoColor=black)](https://hub.docker.com/r/ollama/ollama?tag=0.33.2)
[![OWASP cdxgen](https://img.shields.io/badge/OWASP_cdxgen-13.0.1-000000?logo=owasp&logoColor=white)](https://github.com/cdxgen/cdxgen/releases/tag/v13.0.1)
[![OWASP dep-scan](https://img.shields.io/badge/OWASP_dep--scan-6.3.0-E3222D?logo=owasp&logoColor=white)](https://github.com/owasp-dep-scan/dep-scan/releases/tag/v6.3.0)
[![PyTorch](https://img.shields.io/badge/PyTorch-CUDA_12.1-EE4C2C?logo=pytorch&logoColor=white)](https://github.com/pytorch/pytorch/releases/tag/v2.11.0)

[![Alibaba Qwen](https://img.shields.io/badge/Alibaba-Qwen[3.8]-FF6A00?logo=alibabacloud&logoColor=white)](https://huggingface.co/collections/Qwen/qwen38)
[![Google Gemma](https://img.shields.io/badge/Google-Gemma[4]-4285F4?logo=google&logoColor=white)](https://huggingface.co/collections/google/gemma-4)
[![IBM Granite](https://img.shields.io/badge/IBM-Granite[4.2]-052FAD?logo=ibm&logoColor=white)](https://huggingface.co/collections/ibm-granite/granite-42-language-models)
[![OpenAI GPT-OSS](https://img.shields.io/badge/OpenAI-GPT--OSS-412991?logo=openai&logoColor=white)](https://huggingface.co/openai)



O BOMSenso combina os conceitos de *Bill of Materials* (BOM) e Senso (do latim *sensus*, associado à percepção e ao entendimento), refletindo sua proposta de atuar como um motor orientado à interpretação de artefatos BOM. Em uma abordagem de autoanálise, o sistema correlaciona artefatos e vulnerabilidades para produzir evidências e apoiar a tomada de decisão. Desenvolvido com modelos *open-weights* e operação *on-premise*, o processamento ocorre localmente, mantendo os dados restritos ao ambiente de execução e preservando a rastreabilidade operacional de ponta a ponta.

---

## 🏗️ Arquitetura e Pilares Técnicos

O projeto sustenta-se em 5 pilares fundamentais:

1. **Roteamento Adaptativo (FinOps):** Detecção física de VRAM in-memory e alocação dinâmica de LLMs (desde abordagens de sobrevivência Single-LLM até a expansão horizontal de Conselhos Globais em hardwares Ultra-scale).
2. **Inventário de Metadados (BOM):** Geração estática da *Software Bill of Materials* utilizando o padrão **OWASP CycloneDX**, criando uma taxonomia clara e estruturada das dependências.
3. **Auditoria de Vulnerabilidades (VDR):** Varredura local via `dep-scan`, gerando evidências (CVEs) em ambiente totalmente isolado.
4. **Indexação Semântica (LazyGraphRAG):** Construção de um Grafo de Conhecimento em memória (via `networkx`) para navegação inteligente dos agentes nas dependências diretas e transitivas.
5. **Orquestração *Zero Trust* (LangGraph):** Deliberação agêntica orientada por criticidade e Segregação de Funções (SoD). A topologia escala de 3 a 8 agentes conforme a política de risco, dividindo o atrito cognitivo em duas frentes:
   - 🕵️ **🏢 Cadeia de Decisão:** Estagiário (Triagem), Analista (Mapeamento Técnico), Supervisor (Veredito Base), Gerente (Visão Cross-Setorial), Diretor (Impacto Financeiro) e Presidente (Autorização de Shutdown).
   - ⚖️ **🛡️ Assurance Independente:** Auditor Interno (aderência técnica e evidências) e Auditor Externo (conformidade regulatória e ISO). Operam fora da cadeia de subordinação para garantir validação imparcial.
6. **Atestação Pós-Quântica (PQC):** Motor criptográfico alinhado ao modelo *Zero Trust*, equipado com `liboqs` por meio de bindings em Python para assinar e validar envelopes de metadados utilizando **ML-DSA (FIPS 204)**, derivado do projeto *CRYSTALS-Dilithium*, além de suportar encapsulamento de chaves com **ML-KEM (FIPS 203)**, derivado do projeto *CRYSTALS-Kyber*.
---

## 🧬 Estrutura do Pipeline (As 7 Células)

O fluxo operacional do unbook é orquestrado de forma encadeada nas seguintes etapas:

- **(i) CÉLULA 1:** Motor BOMSenso - Roteamento Adaptativo de VRAM *(Detecção de hardware e matriz automotiva).*
- **(ii) CÉLULA 2:** Provisionamento Unificado via API REST *(Cache e download em endpoints Ollama e Hugging Face).*
- **(iii) CÉLULA 3:** Inventários Estáticos *(Extração das 6 camadas e federação com UUID Mestre via CycloneDX).*
- **(iv) CÉLULA 4:** Pre-Cache do VDB *(Download do contêiner de Threat Intelligence - CVEs).*
- **(v) CÉLULA 5:** Auditoria de Vulnerabilidades e Atestação *(Execução do OWASP dep-scan no lago de metadados).*
- **(vi) CÉLULA 6:** Motor LazyGraphRAG Oficial *(Ingestão de componentes e vulnerabilidades VDR).*
- **(vii) CÉLULA 7:** Orquestração Agêntica Zero Trust *(LangGraph + RAG com dimensionamento de contexto adaptativo).*

---
## 🚀 Matriz de Roteamento - Absolute Resolve

O sistema classifica o perfil de *hardware* conforme a capacidade de VRAM disponível, abrangendo a partir de 4 GB e escalando para mais de 300 GB, e ajusta a orquestração de abordagens ágeis com modelos SLM (*Ollama*) até estruturas simuladas com múltiplos LLMs de maior escala em paralelo (*Hugging Face/Ollama*). 

> **Atenção à Governança:** O aumento de VRAM não concede maior autoridade a um agente. Ele apenas permite a ativação de papéis especializados adicionais (como diretores e auditores externos) quando a política de risco corporativo exigir.

| VRAM Efetiva | Camada Operacional *(Perfis de Hardware)* | Total de Agentes | Cadeia de Decisão | Assurance (Zero Trust) |
| :--- | :--- | :--- | :--- | :--- |
| **4–24 GB** | **Operacional Base**<br>*(Fusca, Golf, Corolla, Camaro, Mustang, 911)* | **3** | Analista ➔ Supervisor | Auditor Interno |
| **32–64 GB** | **Tático I**<br>*(Gallardo, Centenario, M3 GTR, Chiron)* | **4** | ↳ *Adiciona:* **Estagiário** | Auditor Interno |
| **80–96 GB** | **Tático II**<br>*(Airbus A380, Tupolev Tu-144)* | **5** | ↳ *Adiciona:* **Gerente** | Auditor Interno |
| **141 GB** | **Compliance / Estratégico**<br>*(Antonov An-225 Mriya)* | **6** | *(Mantém Gerente como teto)* | ↳ *Adiciona:* **Auditor Externo** |
| **180 GB** | **C-Level**<br>*(F-39E Gripen)* | **7** | ↳ *Adiciona:* **Diretor** | Aud. Interno & Externo |
| **192–288 GB** | **Alta Presidência**<br>*(Su-57 Felon, F-22 Raptor)* | **8** | ↳ *Adiciona:* **Presidente** | Aud. Interno & Externo |
| **≥ 300 GB** | **Conselho Global**<br>*(Absolute Resolve)* | **Frota** | **Múltiplos** Diretores e Presidentes | Aud. Interno & Externo |
---
### Critério de classificação de SLM

Para fins classificatórios, os modelos de linguagem com até 5 bilhões de parâmetros (≤ 5B) foram categorizados como *Small Language Models* (SLMs). Essa delimitação possui como amparo teórico o trabalho de [Lu et al. (2024)](https://arxiv.org/pdf/2409.15790), dedicado à investigação de SLMs. A definição adotada neste *framework* é exclusivamente operacional, para fins de classificação e roteamento experimental, não constituindo uma definição universal da categoria SLM.

Modelos acima desse limite são tratados, neste *framework*, como *Large Language Models* (LLMs), independentemente de sua quantização ou do consumo efetivo de memória durante a inferência.

---

## 🐳 Ambiente e Contêineres

O ambiente é 100% orquestrado via **Docker Compose**, provendo isolamento lógico e gerando as seguintes imagens e instâncias:

1. **bomsenso-jupyter:1.0.0** → `bomsenso_jupyter` (Contêiner)
2. **ollama/ollama:0.33.2** → `bomsenso_ollama` (Contêiner)

---
*Projeto orquestrado por williansdb. Acesse o repositório em [github.com/williansdb/bomsenso](https://github.com/williansdb/bomsenso).*
