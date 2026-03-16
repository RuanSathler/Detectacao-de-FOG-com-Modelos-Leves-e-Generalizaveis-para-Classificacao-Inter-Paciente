# 🚶‍♂️ Detecção de Freezing of Gait (FoG) com Deep Learning

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=for-the-badge&logo=mlflow&logoColor=white)
![DagsHub](https://img.shields.io/badge/DagsHub-000000?style=for-the-badge&logo=github&logoColor=white)

Projeto de Iniciação Científica (PIBIC) focado na classificação e detecção do *Freezing of Gait* (Congelamento da Marcha) em pacientes com a Doença de Parkinson, utilizando dados de sensores inerciais (wearables) e arquiteturas de Deep Learning.

## 🧠 O Problema
O *Freezing of Gait* (FoG) é um sintoma motor debilitante comum no mal de Parkinson, caracterizado pela incapacidade repentina e episódica de iniciar ou continuar a caminhada. A detecção automática e precisa do FoG através de sensores pode ajudar na criação de sistemas de biofeedback em tempo real, melhorando a qualidade de vida dos pacientes e prevenindo quedas.

## ⚙️ Tecnologias e Ferramentas
* **Linguagem:** Python
* **Deep Learning:** PyTorch
* **Processamento de Dados:** Pandas, NumPy, Scikit-learn
* **Visualização:** Matplotlib, Seaborn
* **MLOps / Tracking:** MLflow integrado ao DagsHub

## 🔬 Metodologia

### 1. Conjunto de Dados
O modelo foi treinado utilizando o **Daphnet Freezing of Gait Dataset**. Os dados são compostos por leituras de acelerômetros 3D posicionados no tornozelo, coxa e tronco dos pacientes.

### 2. Validação Robusta (LOSO)
Para garantir que o modelo não memorizou o padrão de caminhada de um paciente específico (overfitting), foi adotada a técnica de validação **Leave-One-Subject-Out (LOSO)**. O modelo é treinado com os dados de N-1 pacientes e testado no paciente que foi isolado, garantindo a capacidade de generalização para indivíduos inéditos.

## 📊 Rastreamento de Experimentos (MLOps)
Todo o ciclo de vida dos modelos é monitorado rigorosamente usando **MLflow** hospedado no **DagsHub**. Para cada fold (paciente isolado), o repositório salva automaticamente:
* Métricas completas de Treino e Teste (Acurácia, Sensibilidade, Especificidade, F1-Score).
* Matrizes de confusão geradas a partir do melhor peso alcançado.
* Gráficos das curvas de aprendizado por época (Loss e F1).
* Os próprios artefatos dos modelos (`.pth`).

*(Acesse a aba `Experiments` no repositório do DagsHub para visualizar os resultados interativos).*

## 🚀 Como Executar

1. Clone este repositório:
```bash
git clone https://github.com/RuanSathler/PIBIC-FOG.git
cd PIBIC-FOG
```

2. Instale as dependências:
```bash
pip install torch pandas numpy matplotlib seaborn scikit-learn mlflow dagshub
```

3. Configure o DagsHub (para logar as execuções):
```python
import dagshub
dagshub.init(repo_owner='RuanSathler', repo_name='PIBIC-FOG', mlflow=True)
```

## 👨‍💻 Autor
**Ruan Sathler**
* Estudante de Engenharia de Software - Universidade Federal do Amazonas (UFAM)
* [LinkedIn](www.linkedin.com/in/ruan-sathler) | [GitHub](https://github.com/RuanSathler)
