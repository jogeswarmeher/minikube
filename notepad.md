Here is a complete step-by-step flow using Minikube from start to accessing your app 🚀

🧱 Step 1: Start Minikube
minikube start
🔍 Step 2: Verify Cluster
kubectl get nodes

👉 You should see Ready

🐳 Step 3: Use Minikube’s Docker (IMPORTANT)
eval $(minikube docker-env)

👉 This ensures image builds inside Minikube (no push needed)

📦 Step 4: Build Docker Image
docker build -t my-python-app .
📄 Step 5: Update deployment.yaml

Make sure it has:

containers:
- name: python-app
  image: my-python-app
  imagePullPolicy: Never
🚀 Step 6: Deploy Application
kubectl apply -f deployment.yaml
🔍 Step 7: Check Pods
kubectl get pods

👉 Wait until:

STATUS = Running
🌐 Step 8: Create Service
kubectl apply -f service.yaml
🔍 Step 9: Verify Service
kubectl get svc
🌍 Step 10: Access Application
minikube service python-service

👉 This will:

Open browser automatically
Or give a URL
🧪 Step 11: Test via curl (optional)
curl $(minikube service python-service --url)
📊 Step 12: Check Logs (optional)
kubectl logs -l app=python-app
🔄 Step 13: Scale Application (optional)
kubectl scale deployment python-app --replicas=3
🧹 Step 14: Cleanup (when needed)
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
minikube stop
🧠 Full Flow (Quick Copy)
minikube start
kubectl get nodes
eval $(minikube docker-env)
docker build -t my-python-app .
kubectl apply -f deployment.yaml
kubectl get pods
kubectl apply -f service.yaml
minikube service python-service
🔥 If you want next level

I can help you:

Add Ingress (custom domain like app.local)
Add Auto Scaling
Convert this into a CI/CD pipeline
Deploy same app to AWS EKS / Azure AKS

Just tell me 👍
