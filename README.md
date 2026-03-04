# ☸️ CKA Practice Questions

This repository contains hands-on practice questions for the **Certified Kubernetes Administrator (CKA)** exam.

## 📁 Structure

Each folder represents a topic and contains:

| File | Purpose |
|------|---------|
| `question.md` | The practice task |
| `answer.yaml` | Solution YAML |
| `setup.yaml` | Environment setup file |

## 🚀 How to Use

1. Pick a topic folder
2. Read `question.md`
3. Run the setup file to create the practice environment:
   ```bash
   kubectl apply -f setup.yaml
