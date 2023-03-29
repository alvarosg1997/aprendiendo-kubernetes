Un pod de Kubernetes es un conjunto de uno o varios conetenedores de linux y constituye la unidad más pequeña de las aplicaciones de Kubernetes. Puede estar compuesto por un solo contenedor, en un caso de uso común, o por varios con conexión directa, en un caso de uso avanzado.

![image](https://user-images.githubusercontent.com/75830958/228514343-a7986836-1d64-4919-a581-05fa6fb159c3.png)

### 1.1 Estructura de un pod

La estructura básica de un archivo **`pod.yml`** en Kubernetes incluye:

- **`apiVersion`**: La versión de la API de Kubernetes que se está utilizando.
- **`kind`**: El tipo de objeto que se está definiendo. En este caso, será **`Pod`**.
- **`metadata`**: Información sobre el pod, como su nombre y etiquetas.
- **`spec`**: La definición del pod, incluyendo la especificación de los contenedores que se ejecutarán en el pod.
- Estructura YAML de pod
    
    ```yaml
    apiVersion: v1 
    # La versión de la API de Kubernetes que se está utilizando
    kind: Pod 
    # El tipo de recurso que se está definiendo, en este caso un pod
    metadata: 
    # Metadatos sobre el pod
      name: my-pod 
      # El nombre del pod
      labels: 
      # Etiquetas para organizar y seleccionar pods
        app: my-app
        tier: frontend
    spec: 
    # La especificación del pod
      containers: 
      # Una lista de contenedores que se ejecutarán en el pod
      - name: my-app-container 
      # El nombre del contenedor
        image: my-app:latest 
        # La imagen del contenedor
        ports: 
        # Una lista de puertos que se expondrán desde el contenedor
        - containerPort: 8080 
        # El puerto que se está exponiendo del contenedor
        env:
         # Una lista de variables de entorno que se establecerán en el contenedor
        - name: DB_HOST
          value: my-database
        resources: 
        # Recursos de computación que se asignarán al contenedor
          limits:
            memory: "128Mi" 
            # Límite máximo de memoria
            cpu: "500m" 
            # Límite máximo de CPU
    ```
