## Trabajo Práctico 9 - Implementación de Contenedores en Azure Parte 2
### 4- Desarrollo:

#### 4.1 Modificar nuestro pipeline para incluir el deploy en QA y PROD de Imagenes Docker en Servicio Azure App Services con Soporte para Contenedores
- Desarrollo del punto 4.1: 
	
  	- ##### 4.1.1 - Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Construcción y Pruebas y de la etapa de Construcción de Imagenes Docker y subida a ACR realizada en el TP08
  	    
  	  - Agregar tareas para crear un recurso Azure Container Instances que levante un contenedor con nuestra imagen de back utilizando un AppServicePlan en Linux
	  	![alt text](image-3.png)
  	    ![alt text](image.png)
  	     
#### 4.2 Desafíos:
- 4.2.1 Agregar tareas para generar Front en Azure App Service con Soporte para Contenedores
![alt text](image-6.png)

- 4.2.2 Agregar variables necesarias para el funcionamiento de la nueva etapa considerando que debe haber 2 entornos QA y PROD para Back y Front.
![alt text](image-2.png)
![alt text](image-4.png)

- Funcionando
![alt text](image-5.png)
![alt text](image-7.png)


- 4.2.3 Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en Azure App Services con Soporte para Contenedores. 


- 4.2.4 Agregar etapa que dependa de la etapa de Deploy en QA que genere un entorno de PROD.
![alt text](image-8.png)
![alt text](image-9.png)
![alt text](image-10.png)
![alt text](image-11.png)
![alt text](image-12.png)

- 4.2.5 Entregar un pipeline que incluya:

    ![alt text](image-13.png)
    ![alt text](image-14.png)

  - A) Etapa Construcción y Pruebas Unitarias y Code Coverage Back y Front
      ![alt text](image-15.png)

  - B) Construcción de Imágenes Docker y subida a ACR
      ![alt text](image-16.png)

  - C) Deploy Back y Front en QA con pruebas de integración para Azure Web Apps
      ![alt text](image-17.png)

  - D) Deploy Back y Front en QA con pruebas de integración para ACI
      ![alt text](image-18.png)

  - E) Deploy Back y Front en QA con pruebas de integración para Azure Web Apps con Soporte para contenedores
      ![alt text](image-19.png)

  - FRONTS DE QA y PIPELINE
      ![alt text](image-26.png)
      ![alt text](image-20.png)
      ![alt text](image-21.png)


  - F) Aprobación manual de QA para los puntos C,D,E
      ![alt text](image-22.png)


  - G) Deploy Back y Front en PROD para Azure Web Apps
      ![alt text](image-23.png)

  - H) Deploy Back y Front en PROD para ACI
      ![alt text](image-24.png)


  - I) Deploy Back y Front en PROD para Azure Web Apps con Soporte para contenedores
      ![alt text](image-25.png)

  - FRONTS DE PROD y PIPELINE
      ![alt text](image-27.png)
      ![alt text](image-28.png)


###### Se borraron servicios pagos despues de su uso