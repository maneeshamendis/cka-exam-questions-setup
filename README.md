<div align="center">
🚀 CKA Exam Practice Lab
https://img.shields.io/badge/kubernetes-%2523326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white
https://img.shields.io/badge/CKA-Certified%2520Kubernetes%2520Administrator-blue?style=for-the-badge
https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge

🎯 Hands-on practice environment for CKA certification aspirants
Features • Quick Start • Structure • How to Use

</div>
✨ Features
📚 Structured Practice - Each topic has dedicated folder with questions and solutions

⚡ Auto-Setup Environment - Just apply the YAML files to get a pre-configured practice environment

🔧 Real Scenarios - Questions based on real CKA exam patterns

🛠️ Killercoda Ready - Works perfectly with any Kubernetes playground

🚀 Quick Start
bash
# Clone the repository
git clone https://github.com/yourusername/cka-practice-lab.git

# Navigate to any practice folder
cd cka-practice-lab/pod-network

# Deploy the environment
kubectl apply -f setup.yaml

# Start practicing!
📂 Repository Structure
text
📦 cka-practice-lab
 ┣ 📁 pod-network
 ┃ ┣ 📜 README.md        # Question statement
 ┃ ┣ 📜 setup.yaml       # Environment setup
 ┃ ┗ 📜 solution.yaml    # Answer/solution
 ┣ 📁 services
 ┃ ┣ 📜 README.md
 ┃ ┣ 📜 setup.yaml
 ┃ ┗ 📜 solution.yaml
 ┗ 📁 storage
   ┣ 📜 README.md
   ┣ 📜 setup.yaml
   ┗ 📜 solution.yaml
🎯 How to Use
Choose a topic - Browse through the folders based on the concept you want to practice

Read the question - Each folder contains a README.md with the practice question

Setup the environment - Apply the setup.yaml file to create the practice environment

Solve & verify - Try to solve the task, then check your answer against solution.yaml

💡 Pro Tip: You can run this on any Kubernetes environment - local cluster, Killercoda, or cloud playground!

📋 Prerequisites
Basic understanding of Kubernetes concepts

Access to a Kubernetes cluster (local, cloud, or Killercoda)

kubectl configured to communicate with your cluster

🎓 About CKA
The Certified Kubernetes Administrator (CKA) program ensures that CKAs have the skills, knowledge, and competency to perform the responsibilities of Kubernetes administrators.

https://img.shields.io/badge/CKA-Curriculum-blue?style=flat-square

<div align="center">
⭐ Found this helpful? Star the repo to support!
Happy Learning! May the kubeconfig be with you 🖖

</div>
