# Anonymisation des Contrats Juridiques par Extraction d’Entités Nommées

Ce projet a pour objectif d’**anonymiser des contrats juridiques** en détectant et masquant les entités nommées sensibles (personnes, organisations, adresses, etc.).  
L’approche repose sur plusieurs modèles de **Named Entity Recognition (NER)**, avec différentes phases de **prétraitement, entraînement, évaluation et combinaison de modèles**.

---

##  Organisation du projet

### 1. Prétraitement des contrats
- **`pretraitementcontrats_camembert.ipynb`**  
  Première phase de test pour :
  - Nettoyer les contrats.
  - Découper en chunks (chunking).
  - Essayer une première extraction d’entités avec le modèle [`Jean-Baptiste/camembert-ner`](https://huggingface.co/Jean-Baptiste/camembert-ner).

---

### 2. Essai de plusieurs modèles
- **`essai_plusieurs_modeles.ipynb`**  
  Met en place le **prétraitement final** et la méthode de chunking appliquée à tous les modèles.  
  Modèles testés :
  - [`Jean-Baptiste/camembert-ner`](https://huggingface.co/Jean-Baptiste/camembert-ner)  
  - [Flair](https://github.com/flairNLP/flair)  
  - [`Alizee/xlm-roberta-large-finetuned-wikiner-fr`](https://huggingface.co/Alizee/xlm-roberta-large-finetuned-wikiner-fr)

- **`spacy_trials.ipynb`**  
  Expérimentations avec un modèle **spaCy** pour la reconnaissance d’entités.

---

### 3. Fine-tuning des modèles
- **`FinetuneFlair.ipynb`** : Fine-tuning du modèle Flair sur des extraits de contrats.  
- **`FinetuneRoberta.ipynb`** : Fine-tuning du modèle RoBERTa sur des extraits de contrats.  
- **`finetuneflair_spacy_with_onedataset.ipynb`** : Fine-tuning de Flair avec le dataset [`taln-ls2n/Adminset-NER`](https://huggingface.co/datasets/taln-ls2n/Adminset-NER).  
- **`finetune_flair_spacy_2datasets.ipynb`** : Fine-tuning sur deux datasets combinés :  
  - [`taln-ls2n/Adminset-NER`](https://huggingface.co/datasets/taln-ls2n/Adminset-NER)  
  - [`Jean-Baptiste/wikiner_fr`](https://huggingface.co/Jean-Baptiste/wikiner_fr)

---

### 4. Méthodes d’ensemble et évaluation
- **`ensemble_method.ipynb`**  
  Code principal pour **combiner les résultats de plusieurs modèles** afin d’améliorer la robustesse.

- **`evaluation_models.ipynb`**  
  Évaluation des performances avec deux approches :
  - Métriques classiques (précision, rappel, F1).  
  - Évaluation par **fuzzy matching** pour tolérer de légères variations.

---

### 5. Anonymisation
- **`anonymisation_contract1.ipynb`**  
  Application finale : masquage automatique des entités détectées dans les contrats.

---

##  Rapport
- **`14_04_rapport_fin_de_projet.pdf`**  
  Rapport de synthèse du projet.

---

##  Conclusion
Ce projet explore différentes approches de NER (CamemBERT, Flair, RoBERTa, spaCy),  
met en œuvre du fine-tuning sur des jeux de données adaptés au domaine juridique,  
et propose une **méthode d’ensemble** ainsi qu’un **processus complet d’anonymisation des contrats juridiques**.
