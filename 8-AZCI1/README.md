## Trabajo Práctico 8 - Implementación de Contenedores en Azure y Automatización con Azure CLI

### 4- Desarrollo:

#### 4.1 Modificar nuestro pipeline para construir imágenes Docker de back y front y subirlas a ACR
- Desarrollo del punto 4.1: 
	- ##### 4.1.1 Crear archivos DockerFile para nuestros proyectos de Back y Front
   	  
	  ![alt text](image-2.png)



   	- ##### 4.1.2 Crear un recurso ACR en Azure Portal siguiendo el instructivo 5.1
      ![alt text](image-1.png)



  	- ##### 4.1.3 Modificar nuestro pipeline en la etapa de Build y Test
   	  - Luego de la tarea de publicación de los artefactos de Back agregar la tarea de publicación de nuestro dockerfile de back para que esté disponible en etapas posteriores:
   	     ```yaml
	     - task: PublishPipelineArtifact@1
   	       displayName: 'Publicar Dockerfile de Back'
   	         inputs:
		   targetPath: '$(Build.SourcesDirectory)/docker/api/dockerfile'
		   artifact: 'dockerfile-back'
   	     ```
   	  - Luego de la tarea de publicación de los artefactos de Front agregar la tarea de publicación de nuestro dockerfile de front para que esté disponible en etapas posteriores:
   	     ```yaml
	     - task: PublishPipelineArtifact@1
   	       displayName: 'Publicar Dockerfile de Back'
   	         inputs:
		   targetPath: '$(Build.SourcesDirectory)/docker/front/dockerfile'
		   artifact: 'dockerfile-front'
   	     ```

      ![alt text](image-7.png)

  	- ##### 4.1.4 En caso de no contar en nuestro proyecto con una ServiceConnection a Azure Portal para el manejo de recursos, agregar una service connection a Azure Resource Manager como se indica en instructivo 5.2 
      ![alt text](image.png)



  	- ##### 4.1.5 Agregar a nuestro pipeline variables 
	  ![alt text](image-6.png)
  	- ##### 4.1.6 Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Build y Test
  	  - Agregar tareas para generar imagen Docker de Back
   	  
   	  ![alt text](image-5.png)
  	
  	- ##### 4.1.7 - Ejecutar el pipeline y en Azure Portal acceder a la opción Repositorios de nuestro recurso Azure Container Registry. Verificar que exista una imagen con el nombre especificado en la variable backImageName asignada en nuestro pipeline
  	  ![alt text](image-3.png)
      ![alt text](image-4.png)

	- ##### 4.1.8 - Agregar tareas para generar imagen Docker de Front (DESAFIO)
  	  - A la etapa creada en 4.1.6 Agregar tareas para generar imagen Docker de Front
      ![alt text](image-10.png)
      ![alt text](image-9.png)
      ![alt text](image-8.png)
  	- ##### 4.1.9 - Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Construcción de Imagenes Docker y subida a ACR
	  - Agregar variables a nuestro pipeline:
  	    ```yaml
  	    ResourceGroupName: 'NOMBRE_GRUPO_RECURSOS' #Por ejemplo 'TPS_INGSOFT3_UCC'
	    backContainerInstanceNameQA: 'NOMBRE_CONTAINER_BACK_QA' #Por ejemplo 'as-crud-api-qa'
	    backImageTag: 'latest' 
	    container-cpu-api-qa: 1 #CPUS de nuestro container de QA
	    container-memory-api-qa: 1.5 #RAM de nuestro container de QA
  	    ```
        ![alt text](image-11.png)

  	  - Agregar variable secreta cnn-string-qa desde la GUI de ADO que apunte a nuestra BD de SQL Server de QA como se indica en el instructivo 5.3
  	  ![alt text](image-12.png)

  	  - Agregar tareas para crear un recurso Azure Container Instances que levante un contenedor con nuestra imagen de back
      ![alt text](image-14.png)
  	  ![alt text](image-13.png)

  	  - ##### 4.1.10 - Ejecutar el pipeline y en Azure Portal acceder al recurso de Azure Container Instances creado. Copiar la url del contenedor y navegarlo desde browser. Verificar que traiga datos.
      ![alt text](image-15.png)
      ![alt text](image-16.png)


  	  - ##### 4.1.11 - Agregar tareas para generar un recurso Azure Container Instances que levante un contenedor con nuestra imagen de front (DESAFIO)
  	  	- A la etapa creada en 4.1.9 Agregar tareas para generar contenedor en ACI con nuestra imagen de Front
  	        - Tener en cuenta que el contenedor debe recibir como variable de entorno API_URL el valor de una variable container-url-api-qa definida en nuestro pipeline.
			![alt text](image-17.png)
  	        - Para que el punto anterior funcione el código fuente del front debe ser modificado para que la url de la API pueda ser cambiada luego de haber sido construída la imagen. Se deja un ejemplo de las modificaciones a realizar en el repo https://github.com/ingsoft3ucc/CrudAngularConEnvironment.git
			![alt text](image-18.png)
			![alt text](image-19.png)
			![alt text](image-20.png)
			![alt text](image-22.png)


  	  - ##### 4.1.12 - Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI.
  	     
#### 4.2 Desafíos:
- [X] 4.2.1 Agregar tareas para generar imagen Docker de Front. (Punto 4.1.8)
- [x] 4.2.2 Agregar tareas para generar en Azure Container Instances un contenedor de imagen Docker de Front. (Punto 4.1.11)
- [ ] 4.2.3 Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI. (Punto 4.1.12)
- [x] 4.2.4 Agregar etapa que dependa de la etapa de Deploy en ACI QA y genere contenedores en ACI para entorno de PROD.

	- ##### 4.2.4 Agregar etapa que dependa de la etapa de Deploy en ACI QA y genere contenedores en ACI para entorno de PROD.
		- Api del back-prod

		    ![alt text](image-23.png)

		- Pipeline con Approval de Enviroment PROD

			![alt text](image-30.png)
			![alt text](image-24.png)
			![alt text](image-25.png)
			![alt text](image-27.png)

		- ACI de Back y Front

			![alt text](image-26.png)
			![alt text](image-28.png)
			![alt text](image-29.png)


