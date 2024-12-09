# pgAdmin and PostgreSQL Deployment on Kubernetes

This project demonstrates how to deploy **pgAdmin** and **PostgreSQL** on a Kubernetes cluster. The configuration includes separate YAML files for deploying the PostgreSQL database, pgAdmin, services, and secrets.

## Project Structure

- `config.yml`  
  Contains configuration settings for the deployment.

- `pgadmin-deployment.yml`  
  Deployment configuration for pgAdmin.

- `pgadmin-service.yml`  
  Service configuration for exposing pgAdmin.

- `postgres-db.yml`  
  Deployment configuration for PostgreSQL.

- `postgres-db-svc.yml`  
  Service configuration for exposing PostgreSQL.

- `secret.yml`  
  Configuration for Kubernetes secrets (e.g., credentials for PostgreSQL and pgAdmin).

## Prerequisites

Ensure the following tools are installed and configured:

1. Kubernetes Cluster (Minikube, EKS, GKE, etc.)
2. kubectl CLI
3. Helm (Optional, if you're using Helm for deployment)

## Deployment Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/boateng0303/pgadmin-postgres-kubernetes.git
   cd pgadmin-postgres-kubernetes

2. Create secrets for PostgreSQL and pgAdmin
    ```bash
    kubectl apply -f secret.yml

3. Deploy PostgreSQL:
   ```bash
   kubectl apply -f postgres-db.yml
   kubectl apply -f postgres-db-svc.yml

4. Deploy pgAdmin:
   ```bash
   kubectl apply -f pgadmin-deployment.yml
   kubectl apply -f pgadmin-service.yml

5. Verify that all components are running:
   ```bash
   kubectl get pods
   kubectl get services

6. Access pgAdmin:
   Use the external service IP or port-forward the service:
   ```bash
   kubectl port-forward svc/pgadmin-service <local-port>:<service-port>

Open your browser and navigate to http://localhost:<local-port>. Use the credentials defined in the secret.yml file to log in.

## Configuration

To customize the deployment, update the following files:

- **Secrets:**  
  Update `secret.yml` with your custom credentials for PostgreSQL and pgAdmin.

- **Persistent Volumes (Optional):**  
  Modify `postgres-db.yml` and `pgadmin-deployment.yml` to configure persistent storage for data persistence.

- **Networking:**  
  Adjust `pgadmin-service.yml` and `postgres-db-svc.yml` to expose services as required by your Kubernetes environment.

## Resources

For additional information, refer to the following resources:

- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [pgAdmin Documentation](https://www.pgadmin.org/docs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)




