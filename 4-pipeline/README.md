# Pipeline
## Azure DevOps Pipelines

###  Breve descripción de Azure DevOps Pipelines: 
* Azure DevOps Pipelines es un servicio que automatiza la construcción, prueba y despliegue de aplicaciones en múltiples entornos. Facilita la integración continua (CI) y la entrega continua (CD), mejorando la calidad del software y permitiendo un desarrollo más rápido.

#### Tipos de Pipelines:
* Build Pipelines: Se encargan de compilar y probar tu código. Suelen ser la primera fase en un proceso CI/CD.
* Deploy Pipelines: Se encargan de desplegar tu aplicación en entornos de producción o de prueba.


### Diferencias entre el editor clásico y YAML:
* Editor Clásico: Ofrece una interfaz gráfica para configurar los pipelines mediante tareas predefinidas.
* YAML: Es un archivo de texto que define el pipeline de forma declarativa, lo que permite un mayor control y portabilidad del pipeline.



### Agentes MS y Self-Hosted:
* Microsoft-hosted: Son agentes administrados por Microsoft, fáciles de configurar y usar, aunque limitados en cuanto a personalización.
* Self-Hosted: Corren en servidores propios, ofrecen más control sobre el entorno, pero requieren más mantenimiento.

## Desarollo
### Verificacion
![alt text](1.png)

### Tarea publish
![alt text](2.png)

### Explicación de la tarea de Publish en un agente MS
* La tarea de Publish es esencial para almacenar los artefactos generados, especialmente cuando el pipeline se ejecuta en un agente en la nube, donde el entorno es temporal y los artefactos se deben almacenar externamente.

### Pipe local
![alt text](4.png)
![alt text](4A.png)
![alt text](4B.png)

### Habilitar Clasico
![alt text](5A.png)

### Clasico y resultados
![alt text](6.png)
![alt text](6A.png)

### Config CL result de manera auto
![alt text](7A.png)
![alt text](7B.png)

### Diferencias entre agentes MS y Self-Hosted
* Un agente Self-Hosted te da control sobre el entorno, mientras que uno Microsoft-hosted es más fácil de configurar pero tiene menos personalización. Usar un agente Self-Hosted es ideal cuando necesitas software específico o acceso a recursos internos.

### Pool agentes
![alt text](8.png)

### Agente local
![alt text](9A.png)
![alt text](10.png)

### Pipe con host local
![alt text](11.png)

### Pipe local con host
![alt text](11A.png)

### 12- Angular
![alt text](12.png)

### Pipeline de angular conCI
![alt text](13.png)
![alt text](13A.png)

### cambio en archivo
![alt text](15.png)

### Descargar pipeline
![alt text](16.png)
![alt text](17A.png)

### Cambio
![alt text](17C.png)
![alt text](17B.png)
