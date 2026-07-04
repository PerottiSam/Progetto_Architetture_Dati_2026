# Valutazione dell'Impatto del Rumore sulla Predizione dei Modelli di Machine Learning

## Descrizione del Progetto
Questo repository contiene il codice e l'analisi per il progetto del corso di **Architetture Dati** (A.A. 2025-2026) presso l'Università degli Studi di Milano-Bicocca.

Il progetto analizza in modo sistematico l'impatto di diverse tipologie di corruzione dei dati (valori mancanti, record duplicati e rumore gaussiano/swap) sulle prestazioni predittive di tre algoritmi di Machine Learning in un dominio diagnostico clinico:
* **Decision Tree**
* **Support Vector Machine (SVM)**
* **Neural Network (Multi-Layer Perceptron)**

L'obiettivo principale è quantificare il degrado prestazionale causato dal rumore e testare l'efficacia di varie pipeline di mitigazione (imputazione multivariata tramite KNN e Iterative Imputer, filtraggio con PCA, e tecniche di regolarizzazione come pruning, soft margin e dropout).

## Autori
* **Alen Bicanic** (Matr. 945230)
* **Samuele Perotti** (Matr. 899817)

## Struttura del Repository

```text
├── dataset/                  # Contiene il dataset utilizzato per l'analisi
├── progetto/                 # Contiene il file Jupyter Notebook con l'intero codice del progetto
├── relazione/                # Contiene la relazione in formato PDF
└── README.md                 # Questo file descrittivo
```

## Tecnologie usate
* Linguaggio: Python 3.x
* Librerie principali: Pandas, NumPy, Scikit-Learn
* Visualizzazione dati: Matplotlib, Seaborn

## Come riprodurre gli esperimenti
1. Clona il repository sul tuo ambiente locale:

   ```bash
   git clone https://github.com/PerottiSam/Progetto_Architetture_Dati_2026.git
   cd nome-repo
   ```
2. Installazione delle librerie neccassarie per l'esecuzione del codice:

    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn
    ```
3. Esegui il codice: Apri la cartella progetto/, avvia il file .ipynb contenuto al suo interno ed esegui le celle sequenzialmente per riprodurre l'intera pipeline, dalla pulizia iniziale fino alla Cross-Validation sui dati corrotti.

## Risultati Principali
Dall'analisi validata tramite K-Fold Cross Validation è emerso che:

* L'assenza di dati (NaN) è mitigabile algoritmicamente, mantenendo i modelli su livelli predittivi affidabili.

* I duplicati agiscono in modo ingannevole, causando data leakage e fornendo metriche sovrastimate se non isolati correttamente.

* L'immissione di dati errati (rumore attivo) è la criticità più distruttiva, distorcendo irreversibilmente il segnale informativo. La SVM si è confermata l'architettura più resiliente e strutturata, mentre il Decision Tree è risultato il più vulnerabile in contesti di elevata incertezza.