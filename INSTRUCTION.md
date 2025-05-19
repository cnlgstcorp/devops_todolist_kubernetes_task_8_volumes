# INSTRUCTION.md

## 📦 Як застосувати

```bash
kubectl apply -f .infrastructure/namespace.yml
kubectl apply -f .infrastructure/pv.yml
kubectl apply -f .infrastructure/pvc.yml
kubectl apply -f .infrastructure/configMap.yml
kubectl apply -f .infrastructure/secret.yml
kubectl apply -f .infrastructure/clusterIp.yml
kubectl apply -f .infrastructure/nodeport.yml
kubectl apply -f .infrastructure/hpa.yml
kubectl apply -f .infrastructure/deployment.yml
Або просто:

```bash
./bootstrap.sh
✅ Як перевірити, що все працює
🔹 Перевірити, що под запущено:
```bash
kubectl get pods -n todoapp
🔹 Перевірити, що додаток працює:
```bash
curl http://<NodeIP>:<NodePort>/api/health
curl http://<NodeIP>:<NodePort>/api/ready
🔹 Перевірити, що маунти з ConfigMap і Secret як файли:
```bash
kubectl exec -n todoapp -it <pod-name> -- sh
Усередині пода:

```bash
cat /app/configs/PYTHONUNBUFFERED          # має вивести: 1
cat /app/secrets/SECRET_KEY                # має вивести: (секрет)
🔹 Перевірити, що PVC змонтований:
```bash
ls /app/data