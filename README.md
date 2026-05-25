# CIFAR-10 Image Classifier — ICT120 Final Project

**Jezreel — Web Deployment & Documentation Lead**  
Step 6: Deploy the Model on the Web

---

## 🚀 Live Demo

> *(paste your Streamlit Cloud URL here after deploying)*

---

## 📁 File Structure

```
cifar10-webapp/
├── app.py                  ← Streamlit web application
├── requirements.txt        ← Python dependencies
├── README.md               ← This file
└── cifar10_model.keras     ← Your trained model (add this yourself)
```

---

## ⚙️ Setup & Run Locally

### 1 — Clone the repo
```bash
git clone https://github.com/<your-username>/cifar10-webapp.git
cd cifar10-webapp
```

### 2 — Add your trained model
Copy your trained model file into the project folder:
```bash
# If saved as .keras
cp /path/to/cifar10_model.keras .

# If saved as .h5, rename it
cp /path/to/cifar10_model.h5 cifar10_model.keras
```

Or, add this cell to your notebook to save in the right format:
```python
model.save("cifar10_model.keras")
```

### 3 — Install dependencies
```bash
pip install -r requirements.txt
```

### 4 — Run locally
```bash
streamlit run app.py
```
Open http://localhost:8501 in your browser.

---

## ☁️ Deploy to Streamlit Cloud (Free)

1. Push this repo to GitHub (see below)
2. Go to [share.streamlit.io](https://share.streamlit.io)
3. Sign in with GitHub → click **New app**
4. Select your repo, branch `main`, file `app.py`
5. Click **Deploy** — you get a free public URL

> ⚠️ **Important:** You must also upload `cifar10_model.keras` to your GitHub repo.  
> If the file is > 100 MB, use [Git LFS](https://git-lfs.com):
> ```bash
> git lfs install
> git lfs track "*.keras" "*.h5"
> git add .gitattributes
> ```

---

## 📤 Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit — CIFAR-10 Streamlit web app"
git branch -M main
git remote add origin https://github.com/<your-username>/cifar10-webapp.git
git push -u origin main
```

---

## 🌐 Web App Features

| Feature | Details |
|---|---|
| Image upload | JPEG, PNG, WEBP — any resolution |
| Preprocessing | Auto-resize to 32×32, normalize to [0, 1] |
| Prediction | Class name + confidence score (%) |
| All-class scores | Ranked bar chart for all 10 classes |
| Validation suite | Upload 1 image per class, get accuracy + table + confusion matrix |
| Model info | Architecture + training details in sidebar |

---

## 📸 Validation Runs

The app has a built-in **Validation Runs** section.  
Upload one sample image per class (starting with airplane → automobile → bird → cat → deer),  
then screenshot each prediction for your final report.

**Required for report:**
- [ ] Screenshot of airplane prediction
- [ ] Screenshot of automobile prediction
- [ ] Screenshot of bird prediction
- [ ] Screenshot of cat prediction
- [ ] Screenshot of deer prediction
- [ ] Validation summary table
- [ ] Confusion matrix

---

## 🏗️ Model Architecture

```
Input: (32, 32, 3)
→ Conv2D(32 filters, 3×3) → ReLU → MaxPooling2D(2×2)
→ Conv2D(64 filters, 3×3) → ReLU → MaxPooling2D(2×2)
→ Flatten
→ Dense(128) → ReLU
→ Dense(10)  → Softmax
```

Compiled with: `Adam` optimizer, `categorical_crossentropy` loss, 20 epochs, batch size 64.
