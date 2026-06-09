# 🧩 MLOps CI/CD Pipeline – Modelo de Regressão Linear

Este repositório apresenta um exemplo prático de **automação de pipeline de Machine Learning** utilizando **GitHub Actions**.  
O objetivo é demonstrar como aplicar **boas práticas de CI/CD** no contexto de MLOps, garantindo **reprodutibilidade, rastreabilidade e qualidade** em todo o ciclo de vida de um modelo de Machine Learning.

---

## 🎯 Objetivo

Automatizar as etapas de:
1. **Commit** – versionar código e dados.  
2. **Teste de Dados** – validar integridade e consistência do dataset.  
3. **Treinamento** – gerar automaticamente o modelo de regressão linear.  
4. **Avaliação** – calcular métricas de desempenho e registrar resultados.  
5. **Deploy (disponibilização)** – publicar o modelo e as métricas como artefatos no GitHub Actions.

O pipeline executa tudo automaticamente a cada commit ou pull request.

---

## 🧱 Estrutura do Projeto

```
mlops-ci-cd/
│
├── data/
│   └── houses.csv               # Dataset de exemplo
│
├── src/
│   ├── utils.py                 # Funções auxiliares (carregar e validar dados)
│   ├── validate_data.py         # Validação automática do dataset
│   ├── train.py                 # Treinamento do modelo
│   ├── evaluate.py              # Avaliação do modelo e geração de métricas
│
├── tests/
│   └── test_utils.py            # Testes unitários com pytest
│
├── requirements.txt             # Dependências do projeto
│
└── .github/
    └── workflows/
        └── mlops-pipeline.yml   # Pipeline CI/CD do GitHub Actions
```

---

## ⚙️ Instalação e Execução Local

### 1️⃣ Clonar o repositório
```bash
git clone https://github.com/LauroDF/mlops-cicd.git
cd mlops-automation-handson
```

### 2️⃣ Criar e ativar um ambiente virtual
```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/Mac
source .venv/bin/activate
```

### 3️⃣ Instalar dependências
```bash
pip install -r requirements.txt
```

### 4️⃣ Executar scripts localmente
```bash
# Validação de dados
python src/validate_data.py

# Treinamento do modelo
python src/train.py

# Avaliação do modelo
python src/evaluate.py
```

Os arquivos `model.joblib` e `metrics.json` serão gerados na pasta raiz do projeto.

---

## 🧪 Testes automatizados
Execute os testes com **pytest**:
```bash
pytest
```
> Todos os testes devem passar antes de subir o código para o GitHub.

---

## 🚀 Pipeline de CI/CD (GitHub Actions)

O arquivo `.github/workflows/mlops-pipeline.yml` define um pipeline automatizado com as seguintes etapas:

| Etapa | Descrição |
|--------|------------|
| 🔍 **Validar dados** | Executa o script `validate_data.py` para checar a integridade do dataset. |
| 🧪 **Testes automatizados** | Roda os testes com `pytest`. |
| 🧮 **Treinar modelo** | Executa `train.py`, treinando automaticamente o modelo. |
| 📊 **Avaliar modelo** | Calcula métricas e salva o resultado em `metrics.json`. |
| 📦 **Publicar artefatos** | Envia `model.joblib` e `metrics.json` como artefatos disponíveis no pipeline. |

Após o commit, o pipeline pode ser visualizado na aba **Actions** do repositório.

Exemplo de resultado ao final do pipeline:
```
Artifacts:
 ┣ model.joblib      ← Modelo treinado
 ┗ metrics.json      ← Métricas de avaliação
```

---

## 📈 Exemplo de Saída

Durante a execução do pipeline ou localmente, você verá mensagens como estas:

```
🔍 Iniciando validação de dados...
✅ Validação de dados concluída com sucesso!

🚀 Iniciando treinamento do modelo...
✅ Treinamento concluído. R² = 0.9534

📊 Iniciando avaliação do modelo...
✅ Avaliação concluída. R² = 0.9534
```

---

## 🧠 Conceitos abordados

- CI/CD aplicado a Machine Learning  
- Automação com GitHub Actions  
- Testes de dados e código  
- Versionamento de modelos e métricas  
- Geração e publicação de artefatos de ML  

---

## 🔮 Próximos Passos

- Integrar o modelo com uma API (FastAPI ou Flask).  
- Empacotar o ambiente com Docker.  
- Adicionar repositório de modelos (ex: MLflow).  
- Automatizar re-treinos com novos dados.  
- Implementar monitoramento de métricas e *drift detection*.

---

## 👨‍💻 Autor

**Jaison Schmidt**  

---

> 💬 *Este repositório faz parte de uma aula prática sobre automação em MLOps, demonstrando como pipelines simples podem garantir qualidade e reprodutibilidade em modelos de Machine Learning.*
