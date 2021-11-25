### Escuela Colombiana de Ingeniería
### Arquitecturas de Software - ARSW

## Escalamiento en Azure con Maquinas Virtuales, Sacale Sets y Service Plans

### Dependencias
* Cree una cuenta gratuita dentro de Azure. Para hacerlo puede guiarse de esta [documentación](https://azure.microsoft.com/en-us/free/search/?&ef_id=Cj0KCQiA2ITuBRDkARIsAMK9Q7MuvuTqIfK15LWfaM7bLL_QsBbC5XhJJezUbcfx-qAnfPjH568chTMaAkAsEALw_wcB:G:s&OCID=AID2000068_SEM_alOkB9ZE&MarinID=alOkB9ZE_368060503322_%2Bazure_b_c__79187603991_kwd-23159435208&lnkd=Google_Azure_Brand&dclid=CjgKEAiA2ITuBRDchty8lqPlzS4SJAC3x4k1mAxU7XNhWdOSESfffUnMNjLWcAIuikQnj3C4U8xRG_D_BwE). Al hacerlo usted contará con $200 USD para gastar durante 1 mes.

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

Azure Functions es un servicio en la nube disponible a petición que proporciona toda la infraestructura y los recursos, que se actualizan continuamente, necesarios para ejecutar las aplicaciones. Usted se centra en los fragmentos de código que más le importan y Functions se ocupa del resto.
* ¿Qué es serverless?

La computación sin servidor es una tecnología, también conocida como función como servicio, que brinda al proveedor de la nube una administración completa sobre el contenedor en el que se ejecutan las funciones según sea necesario para atender las solicitudes. Al hacerlo, estas arquitecturas eliminan la necesidad de sistemas en ejecución continua y sirven como cálculos controlados por eventos.
* ¿Qué es el runtime y que implica seleccionarlo al momento de crear el Function App?

El tiempo de ejecución o entorno de ejecución es la parte de una implementación de lenguaje que ejecuta código y está presente en tiempo de ejecución.
* ¿Por qué es necesario crear un Storage Account de la mano de un Function App?

Es neceario para el almacenamiento de los servicios que ofrece un Function App, por ejemplo los triggers.
* ¿Cuáles son los tipos de planes para un Function App?, ¿En qué se diferencias?, mencione ventajas y desventajas de cada uno de ellos.
  - *Consumo*: El plan de consumo de Azure Functions se factura en función del consumo de recursos y las ejecuciones por segundo. Los precios del plan de consumo incluyen una    concesión gratuita mensual de 1 millones de solicitudes y 400.000 GB-segundos de consumo de recursos por suscripción en el modelo de precios de pago por uso, para todas las aplicaciones de funciones de esa suscripción. El plan Azure Functions Premium proporciona un rendimiento mejorado y se factura por segundo en función del número de vCPU/s y de GB/s que consuman sus funciones premium. Los clientes también puede ejecutar Functions dentro de su plan de App Service a las tarifas normales del plan de App Service.
  - *Plan Premium*: ofrece a los clientes las mismas características y el mismo mecanismo de escalado que se utilizan en el plan Consumo (basado en el número de eventos) sin arranque en frío, con rendimiento mejorado y acceso a VNET. La facturación del plan Prémium se basa en el número de núcleos por segundo y en la memoria asignada en todas las instancias. No hay ningún cargo por la ejecución con el plan Prémium. Debe haber al menos una instancia asignada en todo momento en cada plan. Si desea obtener más información, consulte los detalles del plan Prémium de Azure.

* ¿Por qué la memoization falla o no funciona de forma correcta?


* ¿Cómo funciona el sistema de facturación de las Function App?

![Consumo](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/consumo.bmp)
![Premium](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/premium.bmp)

* Informe
  - Function App
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/Function%20App.bmp)
  - Extensión VS
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/Extensión.png)
  - Despliegue Azure
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/Despliegue.bmp)
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/Código.bmp)
   - Prueba
    ![](https://github.com/gabrielaasilva/SilvaAnaGabriela_Lab09ARSW/blob/master/images/Imagenes%20Readme/Prueba.png)
  
