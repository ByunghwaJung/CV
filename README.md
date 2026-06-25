# 👋 안녕하세요, 정병화 (Byunghwa Jung)입니다

<div align="center">

**MES/CIM 시스템 수석 엔지니어 | AI·스마트팩토리 연구자 | 성균관대학교 석사과정**

[![GitHub](https://img.shields.io/badge/GitHub-ByunghwaJung-181717?style=flat&logo=github)](https://github.com/ByunghwaJung/smartfactory)
[![Email](https://img.shields.io/badge/Email-archzero@skku.edu-0078D4?style=flat&logo=microsoft-outlook)](mailto:archzero@skku.edu)

</div>

---

## 🧑‍💻 About Me

제조 현장의 MES/CIM 시스템 개발 전문가로 **16년 이상의 경력**을 보유하고 있습니다.  
현재 LS티라유텍 Manufacturing Business MOS팀 수석 엔지니어로 재직 중이며,  
성균관대학교 스마트팩토리융합학과 석사과정(4학기)에서 **AI × 제조 융합 연구**를 수행하고 있습니다.

> *"제조 현장의 데이터를 자연어로 묻고 답하는 세상을 만들고 있습니다."*

---

## 🔬 Research

### 🏭 NeuroFactory: Ontology-Grounded Hybrid RAG for MES

> **[캡스톤디자인 | IEEE BigData 2026 논문 제출 완료]**

**연구 배경:** 제조 현장 MES DB는 LOT 추적·생산 실적·설비 이력 등 방대한 공정 데이터를 축적하나,  
비전문 사용자가 직접 조회하려면 복잡한 SQL 작성 능력이 필요해 데이터 활용에 높은 기술 장벽이 존재.

**핵심 기여:** OWL 온톨로지 기반 도메인 지식(스키마·FK 관계·155개 한국어 개념 매핑)을 주입한  
하이브리드 RAG 아키텍처로 Dijkstra 알고리즘 기반 FK-path JOIN 자동 추론 및 쿼리 안전성 검증 포함.

| 구성 요소 | 기술 스택 |
|-----------|-----------|
| 온톨로지 | OWL/Turtle (19 classes, 155 concept aliases, 477 triples) |
| 스키마 | THiRA MES 3.1.0 (19 tables, 457 columns, ~270M rows) |
| 임베딩 | bge-m3 (1024-dim) + ChromaDB (top-k=8) |
| SQL 생성 | Qwen3.5-9B (Q4_K_M) via Ollama on RTX 4090 |
| JOIN 최적화 | Dijkstra-based FK-path hint injection |
| 안전 검증 | Parse-tree 기반 Query Safety Layer (DR 100%, FPR 3%) |
| 백엔드/프론트 | FastAPI + React + Cloudflare Tunnel |

**Ablation Study 결과 (MES-NL2SQL-Gold, n=200):**

| Stage | Description | EX_exec | EX_loose | Table F1 | VS |
|-------|-------------|---------|----------|----------|----|
| B0 | Schema Only (no RAG) | 37.0% | 38.5% | 0.740 | 100% |
| B1 | +ChromaDB RAG | 68.5% | 69.0% | 0.773 | 100% |
| B2 | B1 + FK JOIN hint | 66.0% | 66.5% | 0.752 | 100% |
| B3 | B1 + Ontology Concept Mapping | 80.0% | 80.5% | **0.913** | 100% |
| **FULL** | **B3 + FK (최종 제안)** | **89.5%** | **90.5%** | 0.898 | **100%** |

> FULL 구성: B0 대비 **+52.5pp** 향상 | Hard 쿼리(n=42) EX_exec **85.7%** 달성

**Tech Stack:** `Python` `FastAPI` `React` `MS SQL Server` `ChromaDB` `Ollama` `OWL/RDF` `LangChain`

**팀 구성:** 정병화 (팀장·아키텍처), 김우주, 서경태, 복재민 (Team 11) | 지도교수: 정종필

---

## 🏆 Research Outputs

### 📰 논문 (Papers)

| # | 제목 | 저자 | 학술지/학회 | 상태 |
|---|------|------|------------|------|
| 1 | NeuroFactory: Ontology-Grounded Hybrid RAG for Natural Language Querying in Manufacturing Execution Systems | 정병화, 김우주, 서경태, 복재민, **정종필** | **IEEE BigData 2026**, Phoenix, AZ (Dec 14–17, 2026) | **제출 완료** |

> **Full citation:**  
> Byunghwa Jung, Woojoo Kim, Gyeongtae Suh, Jaemin Bok, Jongpil Jeong, "NeuroFactory: Ontology-Grounded Hybrid RAG for Natural Language Querying in Manufacturing Execution Systems," *IEEE International Conference on Big Data 2026*, Phoenix, AZ, USA, Dec. 14–17, 2026.

### 💾 소프트웨어 저작권 등록 (SW Copyright)

| 제목 | 등록번호 | 등록기관 | 창작일 | 등록일 |
|------|----------|----------|--------|--------|
| **NeuroFactory(제조 관리 시스템 자연어 질의 엔진)** | **C-2026-030625** | 한국저작권위원회 | 2026.06.08 | **2026.06.22** |

- **저작자:** 성균관대학교산학협력단
- **종류:** 컴퓨터프로그램저작물 > 응용프로그램 > 기업관리 > 생산·현장관리 S/W
- **개발 참여:** 정병화, 서경태, 복재민, 김우주, 정종필
- **적용분야:** 제조업 > 스마트팩토리 > MES

### 📋 특허 (Patent)

| 발명명칭 | 관리번호 | 대표발명자 | 접수일 | 상태 |
|---------|----------|-----------|--------|------|
| **제조 실행 시스템에서의 역할 기반 자연어 질의 처리 방법 및 시스템** | R-2026-0542-KR-1 | 김우주 | 2026.06.10 | 제출 (출원 진행 중) |

---

## 📚 Paper Reviews (Related Works)

선행한 연구논문 리스트입니다.

An advanced RAG system for manufacturing quality control — J.A. Heredia Álvaro, J. González Barreda, Advanced Engineering Informatics, 2024

OG-RAG: Ontology-Grounded RAG For LLMs — K. Sharma, P. Kumar, Y. Li (Microsoft Research), arXiv, 2024

Text-to-SQL Empowered by LLMs: A Benchmark Evaluation (DAIL-SQL) — D. Gao et al., Proc. VLDB Endow., 2023

StructRAG: Boosting Knowledge Intensive Reasoning via Inference-time Hybrid Info Structurization — Z. Li et al., arXiv, 2024

Self-RAG: Learning to Retrieve, Generate, and Critique through Self-Reflection — A. Asai et al., ICLR 2024

Seq2SQL: Generating Structured Queries from NL using RL — V. Zhong, C. Xiong, R. Socher, arXiv, 2017

Chat with MES: LLM-driven UI for manipulating garment manufacturing system — Z. Yuan, M. Li et al., Journal of Manufacturing Systems, 2025

## 💼 Work Experience

### LS티라유텍 (LS Tirautech)
**수석 엔지니어 (Senior Engineer)** · Manufacturing Business MOS팀 · *약 12년 재직*

- YG-1(와이지원) MES·FMCS 개발 운영 PM — 서운공장 고도화 및 충주·광주 횡전개 설계 주도 (2023–2026)
- 해성DS 제조 RMS(Recipe Management System) 개발 PL — 디지털 트윈 혁신서비스 사업 참여 (2023–2024)
- 대덕전자 PKG 신공장 MES Tablet·FMB(Dashboard) 개발 PL (2021–2022)
- 에코프로비엠 연구개발 라인 MES 구축 — 서비스·UI 개발 총괄
- 삼성전자 InfraEES 시스템 유지보수 및 UI 개발 (~9년, C#, Oracle/MSSQL)
- THiRA MES 3.1.0 기반 CIM 시스템 운영
- 중국 충칭 Foxconn Industry 4.0 스마트팩토리 Legacy-Hub Interface 개발 (SK C&C 협력, 2016)
- SAP EAI 연동, SQL Server SP 최적화 (재귀 CTE LOT 계층 추적, 커서 병목 해소)

### PS&T
**대리 | 솔루션 개발** · *약 4년 재직 (2009–2013)*

- ERP 시스템 구축, CTI 솔루션 개발 다수

---

## 🎓 Education

| 학위 | 기관 | 전공 | 기간 |
|------|------|------|------|
| **석사과정 (4학기)** | 성균관대학교 (SKKU) | 스마트팩토리융합학과 | 2024.03 ~ 재학 중 |
| **학사** | 평생교육진흥원 | 영어영문학 | 2009.03 – 2011.02 |

**지도교수:** 정종필 교수 (Prof. Jong-Pil Jeong) | jpjeong@skku.edu  
**연구 GitHub:** [github.com/ByunghwaJung/smartfactory](https://github.com/ByunghwaJung/smartfactory)

---

## 🛠 Tech Stack

### Languages & Databases
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL_Server-CC2927?style=flat&logo=microsoftsqlserver&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=flat&logo=oracle&logoColor=white)
![CSharp](https://img.shields.io/badge/C%23-239120?style=flat&logo=csharp&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

### AI / ML
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat&logo=langchain&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat&logo=ollama&logoColor=white)
![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6B35?style=flat)
![OWL/RDF](https://img.shields.io/badge/OWL/RDF-Ontology-6B4FBB?style=flat)

### Web & Infrastructure
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Cloudflare](https://img.shields.io/badge/Cloudflare_Tunnel-F48120?style=flat&logo=cloudflare&logoColor=white)

### Domain Expertise
`MES/CIM` `ERP Integration (SAP)` `Smart Factory` `NL-to-SQL` `Ontology Engineering` `Production Data Analysis`

---

## 📜 Certifications

| 자격증 | 발급기관 | 취득연도 |
|--------|----------|----------|
| 정보처리기사 | 한국산업인력공단 | 2014 |
| OCP Oracle Database 10g | Oracle | 2009 |

---

## 📬 Contact

- 📧 Email: archzero@skku.edu
- 🏢 소속: LS티라유텍 / 성균관대학교 스마트팩토리융합학과
- 📍 Location: Incheon, South Korea
- 💻 GitHub: [github.com/ByunghwaJung/smartfactory](https://github.com/ByunghwaJung/smartfactory)

---

<div align="center">
  <sub>⚡ "제조 데이터와 AI의 경계를 허무는 엔지니어" ⚡</sub>
</div>
