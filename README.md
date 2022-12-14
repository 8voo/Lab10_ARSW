### Escuela Colombiana de Ingeniería
### Arquitecturas de Software - ARSW

## Escalamiento en Azure con Maquinas Virtuales, Sacale Sets y Service Plans

### Dependencias
* Cree una cuenta gratuita dentro de Azure. Para hacerlo puede guiarse de esta [documentación](https://azure.microsoft.com/es-es/free/students/). Al hacerlo usted contará con $100 USD para gastar durante 12 meses.
Antes de iniciar con el laboratorio, revise la siguiente documentación sobre las [Azure Functions](https://www.c-sharpcorner.com/article/an-overview-of-azure-functions/)

### Parte 0 - Entendiendo el escenario de calidad

Adjunto a este laboratorio usted podrá encontrar una aplicación totalmente desarrollada que tiene como objetivo calcular el enésimo valor de la secuencia de Fibonnaci.

**Escalabilidad**
Cuando un conjunto de usuarios consulta un enésimo número (superior a 1000000) de la secuencia de Fibonacci de forma concurrente y el sistema se encuentra bajo condiciones normales de operación, todas las peticiones deben ser respondidas y el consumo de CPU del sistema no puede superar el 70%.

### Escalabilidad Serverless (Functions)

1. Cree una Function App tal cual como se muestra en las  imagenes.

![](images/part3/part3-function-config.png)

![](images/part3/part3-function-configii.png)

2. Instale la extensión de **Azure Functions** para Visual Studio Code.

![](images/part3/part3-install-extension.png)

3. Despliegue la Function de Fibonacci a Azure usando Visual Studio Code. La primera vez que lo haga se le va a pedir autenticarse, siga las instrucciones.

![](images/part3/part3-deploy-function-1.png)

![](images/part3/part3-deploy-function-2.png)

4. Dirijase al portal de Azure y pruebe la function.

![](images/part3/part3-test-function.png)

5. Modifique la coleción de POSTMAN con NEWMAN de tal forma que pueda enviar 10 peticiones concurrentes. Verifique los resultados y presente un informe.

6. Cree una nueva Function que resuleva el problema de Fibonacci pero esta vez utilice un enfoque recursivo con memoization. Pruebe la función varias veces, después no haga nada por al menos 5 minutos. Pruebe la función de nuevo con los valores anteriores. ¿Cuál es el comportamiento?.

**Preguntas**

* ¿Qué es un Azure Function?
- Es un servicio que proporciona la nube de azure que sirve para tener toda la infraestrctura y recursos que se necesitan para las aplicaciones
* ¿Qué es serverless?
- Es un modelo de computacion que funciona como su nombre lo dice sin servidor fisico, en lugar de eso usa servidores virtuales en la nube la cual se encarga de asignar los recursos necesarios para todas las peticones que se realices
* ¿Qué es el runtime y que implica seleccionarlo al momento de crear el Function App?
- Se usa para pasar o retornar valores desde funciones o a las funciones. Lo creamos por que, en este caso, no sirve para pasarle un valor a la funcion de fibonacci, el cual queremos que calcule
* ¿Por qué es necesario crear un Storage Account de la mano de un Function App?
Para guardar datos de la funcion
* ¿Cuáles son los tipos de planes para un Function App?, ¿En qué se diferencias?, mencione ventajas y desventajas de cada uno de ellos.
![image](https://user-images.githubusercontent.com/98189066/202346870-b45369a2-2594-42b5-bb42-60ade5a0bd2e.png)
Tanto el plan de consumo como el plan premium escalan de forma automatica . El plan de consumo es dinamivo para el trato y manejo de las funciones. El plan premium ejecuta instancias de forma eficaz y ejecuta aplicaciones sin retraso. Por ultimo, el plan dedicado es mucho memjor para planes de ejecucion prolongada.
* ¿Por qué la memoization falla o no funciona de forma correcta?
* ¿Cómo funciona el sistema de facturación de las Function App?
Consta de dos planes
1. Pago por uso: Se paga por capacidad de proceso por segundo, sin compromisos a largo plazo ni pagos por adelantado. 
2. Plan de ahorro de Azure para Compute: omprometerse a gastar una cantidad fija por hora durante 1 o 3 años, desbloqueando los precios más bajos hasta que alcance su compromiso por hora
* Informe
![image](https://cdn.discordapp.com/attachments/898369871912534016/1042590153434206208/image.png)
