This is a test project used to trigger the execution of the main project.

The main project will have the following functionalities:
- Custom Kubernetes controller/operator (in Go / Python) that automates a useful workflow — e.g., dynamically scaling workloads, cleaning up old pods, or syncing config from Git to cluster.

### AutoScaler Operator
Purpose: A controller that watches deployments and automatically scales them based on custom metrics (like CPU, memory, or queue length from an external API).

Tasks:
- Initialize kubebuilder project or operator-sdk project in Go. Create a CRD called AutoScalePolicy.
- Write controller logic to watch AutoScalePolicy objects and adjust target deployments based on a mock metric (e.g. from a fake Prometheus endpoint).
- Pull live metrics via Kubernetes API or a Prometheus query. Implement scaling algorithm (e.g., PID or threshold-based).
- Add Prometheus metrics, structured logging (zap), and status updates to the CRD.
- Use kind or minikube to deploy locally.
- Expose metrics via /metrics endpoint, containerize via Dockerfile, push image to GHCR, and deploy to GitHub repo.

### [Python] K8s Snapshot Controller
- Use kopf (Kubernetes Operator Framework for Python)
- Build an operator that automatically snapshots PVCs daily
- Reconciler watches for SnapshotSchedule CRD and triggers volume snapshots
- Use asyncio, logging, and metrics collection
