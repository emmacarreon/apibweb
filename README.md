# Documentación de la API Brazo Web de Vstour

Este repositorio contiene la especificación OpenAPI (Swagger) para la API de Brazo Web. 
Utilicé Docker Desktop para visualizar la documentación en vivo.


Para levantar el .yaml de forma local los requisitos son:
Tener docker desktop instalado. 
Una vez instalado correr el siguiente código en el directorio donde tenemos clonado el proyecto

NOTA ANTES DE EJECUTAR EL COMANDO DOCKER: 
"C:/ruta/openapi.yaml", ruta se debe modificar por la ruta del proyecto.
Por ejemplo, si tenemos una carpeta "api" en el C:, y clonamos el proyecto dentro de esa carpeta seguramente tenemos esta ruta "C:/api/apibweb/openapi.yaml". esa es la ruta que tien que ir

>docker run -d -p 8080:8080 -e SWAGGER_JSON=/tmp/openapi.yaml -v "C:/ruta/openapi.yaml":/tmp/openapi.yaml --name swagger-viewer swaggerapi/swagger-ui
