## Trabajo Práctico 5 - Despliegue de aplicaciones con Azure Devops Release Pipelines

### 1- Objetivos de Aprendizaje
 - Adquirir conocimientos acerca de las herramientas de despliegue y releases de aplicaciones.
 - Configurar este tipo de herramientas.
 - Comprender el concepto de recurso en Azure
 - Comprender los conceptos básicos de Release Pipelines en Azure DevOps.
 - Configurar un Release Pipeline para automatizar despliegues en diferentes entornos-

### 2- Unidad temática que incluye este trabajo práctico
Este trabajo práctico corresponde a la unidad Nº: 3 (Libro Continuous Delivery: Cap 10)

### 3- Consignas a desarrollar en el trabajo práctico:
 - Los despliegues (deployments) de aplicaciones se pueden realizar en diferentes tipos de entornos
   - On-Premise (internos) es decir en servidores propios.
   - Nubes Públicas, ejemplo AWS, Azure, Gcloud, etc.
   - Plataformas como servicios (PaaS), ejemplo Heroku, Google App Engine, AWS, Azure WebApp, etc
 - En este práctico haremos despliegue a Plataforma como Servicio utilizando Azure Web Apps

### 4- Desarrollo:
4.1\. Crear una cuenta en Azure
![alt text](1.png)

4.2\. Crear un recurso Web App en Azure Portal y navegar a la url provista
![alt text](2A.png)
![alt text](2B.png)
![alt text](2C.png)

4.3\. Actualizar Pipeline de Build para que use tareas de DotNetCoreCLI@2 como en el pipeline clásico, luego crear un Pipeline de Release en Azure DevOps con CD habilitada
![alt text](3A.png)
![alt text](3B.png)

4.4\. Optimizar Pipeline de Build
![alt text](3AA.png)
![alt text](33.png)

4.5\. Verificar el deploy en la url de la WebApp /weatherforecast
![alt text](AAAA.png)
![alt text](AAA.png)



4.6\. Realizar un cambio al código del controlador para que devuelva 7 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio
![alt text](S1.png)
![alt text](S.png)


4.7\. Clonar la Web App de QA para que contar con una WebApp de PROD a partir de un Template Deployment en Azure Portal y navegar a la url provista para la WebApp de PROD.
![alt text](44C.png)
![alt text](44A.png)
![alt text](44B.png)

4.8\. Agregar una etapa de Deploy a Prod en Azure Release Pipelines 
![alt text](Z.png)


4.9\.  Realizar un cambio al código del controlador para que devuelva 10 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio, verificar que en la url de la webapp_prod/weatherforecast se muestra lo mismo.
![alt text](image-1.png)
![alt text](image-2.png)

4.10\. Modificar pipeline de release para colocar una aprobación manual para el paso a Producción.
![alt text](AP.png)

4.11\. Realizar un cambio al código del controlador para que devuelva 5 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio, verificar que en la url de la webapp_prod/weatherforecast aun se muestra la versión anterior.
![alt text](image-3.png)
![alt text](image-4.png)
![alt text](image-5.png)

4.12\. Aprobar el pase ya sea desde el release o desde el mail recibido. 
![alt text](CC.png)


4.13\. Esperar a la finalización de la etapa de Pase a Prod y luego corroborar que en la url de la webapp_prod/weatherforecast se muestra la nueva versión coinicidente con la de QA.
![alt text](image.png)
![alt text](image-6.png)


4.14\. Realizar un pipeline (no release) que incluya el deploy a QA y a PROD con una aprobación manual. El pipeline debe estar construido en YAML sin utilizar el editor clásico de pipelines ni el editor clásico de pipelines de release.
![alt text](image-7.png)
![alt text](image-8.png)







