
# 🌟 Cellence — AI-Driven Drug Discovery Platform  

**Cellence** is an AI-powered biomedical pipeline that combines deep learning, cheminformatics, and bioinformatics to accelerate early-stage drug discovery.  
It generates, validates, and ranks novel, drug-like molecules tailored to a given protein target — all served through a clean, modular Flask-based API.  

---

## 🚀 Features  

✅ Generate valid, novel SMILES molecules conditioned on a chemical prompt (via MolGPT)  
✅ Validate, clean, and deduplicate molecules using RDKit  
✅ Evaluate **drug-likeness (Lipinski’s Rule of 5)**  
✅ Predict **ADMET** properties for pharmacokinetic assessment  
✅ Predict binding affinity of molecules to a protein sequence (DeepPurpose)  
✅ Output results as **CSV**, including molecular structure images  
✅ REST API endpoints for easy integration  

---

## 🧬 Pipeline  

```
User → /generate → [MolGPT → RDKit] → Valid SMILES  
     → /score → [Lipinski → ADMET → DeepPurpose] → Ranked molecules + CSV + Images
```

---

## 📄 API Endpoints  

| Method | Endpoint    | Input Example | Output |
|--------|-------------|----------------|--------|
| POST   | `/generate` | `{ "prompt": "C" }` | `[ "CCO", "CCC", ... ]` |
| POST   | `/score`    | `{ "smiles": ["CCO", "CCC"], "target": "<protein sequence>" }` | `[ [ "CCO", 0.82 ], [ "CCC", 0.74 ] ]` |

Results also include Lipinski & ADMET evaluation, molecular images, and a downloadable CSV.

---

## 🗂 Directory Structure  

```
cellence/
├── app.py                  # Flask app with endpoints
├── molgpt.py               # MolGPT SMILES generation
├── rdkit_utils.py          # RDKit validation & Lipinski
├── admet_utils.py          # ADMET prediction
├── deeppurpose_utils.py    # Binding affinity scoring
├── image_utils.py          # Molecular image generation
├── requirements.txt        # Python dependencies
├── output/                 # Results CSVs and images
├── venv/                   # (optional) virtual environment
```

---

## 🔷 Setup  

### 1️⃣ Clone & Install  
```bash
git clone https://github.com/yourusername/cellence.git
cd cellence
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 2️⃣ Run Server  
```bash
python app.py
```

### 3️⃣ Test Endpoints with curl  
```bash
curl -X POST http://127.0.0.1:5000/generate -H "Content-Type: application/json" -d '{"prompt": "C"}'

curl -X POST http://127.0.0.1:5000/score -H "Content-Type: application/json" -d '{"smiles": ["CCO", "CCC"], "target": "MVKVGVNGFGRIGRLVTRAAFNSGKVDIVAINDPFIDLNYMVYMF"}'
```

---

## 🧪 Technologies & Tools  

| Component         | Role |
|-------------------|------|
| **MolGPT**        | Generate novel SMILES strings |
| **RDKit**         | Validate, canonicalize, Lipinski evaluation |
| **DeepPurpose**   | Predict binding affinity |
| **ADMET predictor** | Estimate ADMET properties |
| **Flask**         | REST API backend |
| **Python**        | Core implementation |

---

## 📈 Future Roadmap  

✨ Interactive AI chatbot advisor  
✨ 3D protein–ligand visualization  
✨ Diversity clustering & synthetic accessibility scoring  
✨ Multi-objective optimization  

---

## 📜 License  

MIT License — feel free to use, modify, and contribute!  

---

## 🤝 Contributing  

Contributions, issues, and feature requests are welcome!  
Please open an issue to discuss changes before submitting a PR.  

---

## 🌐 Connect  

If you’re interested in AI for healthcare, computational biology, or drug design — feel free to connect with me on [LinkedIn](https://linkedin.com/in/your-link) or open a discussion here.  

---

> *Cellence — bridging AI and biomedical science for smarter drug discovery.*  
