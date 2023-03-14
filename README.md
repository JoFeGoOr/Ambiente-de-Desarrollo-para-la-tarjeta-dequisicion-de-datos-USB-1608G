# Ambiente de desarrollo para la tarjeta dequisicion de datos USB 1608G Series.
--------------------------------------
En estas instrucciones se detallan los pasos para instalar el software necesario para desarrollar codigo en el lenguaje de programación Python para el uso de la tarjeta de aquisicion de datos USB-1608G Series.
Todo esto esta realizado dentro de un PC con Ubuntu 20.04 LTS

- Lo primero que se debe hacer es actializar las librerias necesarias para la instalacion de la llamada "libreria universal" (UL) para dispositivos de medidas DAQ, para ello debemos correr el siguiente comando en la terminal.

   $ sudo apt-get install gcc g++ make
   $ sudo apt-get install libusb-1.0-0-dev
   
- Luego descargamos, descomprimimos e instalamos la ultima version de la libreria, llamada "uldaq"

  $ wget -N https://github.com/mccdaq/uldaq/releases/download/v1.2.1/libuldaq-1.2.1.tar.bz2
  $ tar -xvjf libuldaq-1.2.1.tar.bz2
  $ cd libuldaq-1.2.1
  $ ./configure && make
  $ sudo make install
  
- Ya instaladas las libreria, procedemos a instalar Python en nuestro SO, cabe destacar que muchas veces y por varias razones, puede que alguna version de Python ya este instalada en nuestro SO, afortunadamente para el uso de esta libreria necesitamos la version de Python 3.4 o superior, pero ademas necesitamos algunos paquetes propios de Python como pip, setuptools y wheels, lamentablemente, si es que no se instala Python desde el instalador provisto desde https://Python.org estos no se encontraran presentes.

- Primero nos aseguramos de tener Python instalado y en su version 3.4 o superior, para ello se ejecuta el siguiente comando.

  $ python3 --version

- Si su salida es alguna error como "python3 not define" o algo por el estilo quiere decir que usted no tiene Python instalado, para instalarlo usted debe ir a la pagina https://Python.org para realizar las descarga de una ejecutable con la ultima version (o la que usted estime conveniente), si por el contratio, el comando anterior arrojo una version de Python aceptable, debemos asegurarnos que los paquetes esten presentes, para ello, usamos el siguiente comando.

  $ python3 -m pip --version
  
- Si es que nos da algun error o en su defecto, no nos entrega la version de pip, junto a la version de python correspondiente, quiere decir que necesitamos hacer la instalacion del paquete pip, lo cual tambien es indicador de que los demas paquetes no estan presentes si o si, se puede dar el caso de que pip este presente en el SO pero nos los demas paquetes por lo que se recomienda seguir esta guia hasta el fin. Para instalar pip debemos usar los siguiente comandos.

  $ sudo apt update
  $ sudo apt install python3-venv python3-pip
  
- Una vez instalado pip procedemos a instalar y/o actualizar todos los paquetes, para ello, ejecutamos el siguiente codigo.

  $ python3 -m pip install --upgrade pip setuptools wheel
  
- Ahora debemos hacer la instalacion que hara funcional la libreria "uldaq" en Python, para ellos ejecutamos lo siguiente.

  $ sudo pip install uldaq
  
- Con esto, finalizamos la instalacion de las librerias, a continuacion, se mostrara la forma de obtener programas de ejemplo para USB-1608G Series en el lenguaje de programacion Python, para ello debemos descargar un archivo con la siguiente URL. 

- https://files.pythonhosted.org/packages/9d/9d/cae9cbdb8285730e8c7a6eae85f6120330a8e833a97cec95d9e288c3dfba/uldaq-1.2.3.tar.gz

- Copiamos el archivo comprimido en alguna carpeta que sea conveniente, descomprimimos el contenido, veremos que dentro de la carpeta descomprimida hay una carpeta de ejemplo llamada "examples", abrimos esta carpeta y nos podremos dar cuenta que viene con mucho archivo .py, estos son los ejemplo, y pueden ser ejecutados desde la terminal navegando a la carpeta con los ejemplos.

- Desde aqui ya podria usarse cualquier editor de texto para abrir los ejemplos y ver su codigo o en su defecto generar nuestro propios archivos .py, se recomienda leer la documentacion de uldaq para saber como interactuar con la tarjeta de adquisicion de datos desde Python.

-----------------------------------------------------------
# instalacion del editor de texto VScode junto con github para el desarrollo de codigo y control de versiones

Los siguietes pasos no son obligatorios para generar archivos .py pero el autor de esta guia de instalacion recomienda fuertemente este ambiente de diseño pues es bastante robusto y de acceso gratuito.

- Lara utilizar VScode junto a github, debemos primero que todo tener un cuenta en github y tener a disposicion, el nombre de usuario y el mail de registro.

- Luego instalaremos git, software dedicado al control de version, github es una entidad aparte que permite realizar un control de versiones remoto, pero necesita del software git, para instalarlo debemos ejecutar lo siguiete.

  $ sudo apt-get install git
  
- Luego actualizaremos 2 variables git, inprecindibles al momento de hacer el control de versiones, el Username debe ir entre comilla pero el mail no, tener cuidado en este paso.

  $ git config --global user.name "Username"
  $ git config --global user.email Mail
  
- Por ultimo debemos instalar VScode, para ello debemos ir a la siguiente URL, recordemos que en esta guia se esta utilizando ubunto por lo que el instalador debe ser consecuente al SO, este es el unico programa de toda la guia que posee instlador por lo que realizar esta instalacion sera muy sencillo.

- https://code.visualstudio.com/

- Luego de finalizar la instalacion, debemos añadir 2 extenciones para incluir Python y Github a VScode, para ello debemos abrir VScode, dirigirnos a la pestaña de extensiones que se encuentra en la barra de acceso rapido de la izquierda de la ventana de VScode, aqui buscamos la extension Python que instlara todo lo necesario para integrar Python, luego de finalizar la instalacion, buscamos la extension "GitHub Pull Requests and Issues" y la instalamos, una vez finalizada, ya habremos concluido con la instalacion de un ambiente de desarrollo robusto para la tarjeta de adquisicion de datos USB-1608G
