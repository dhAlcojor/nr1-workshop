# Setup de New Relic One

Con esta guía aprenderemos a crear [aplicaciones New Relic One](https://docs.newrelic.com/docs/new-relic-programmable-platform-introduction). Configuraremos el sistema para lanzar un servidor local que establezca una conexión a la plataforma de New Relic One. Esto permite crear aplicaciones de forma fácil y rápida porque se pueden ver los cambios en tiempo real.

# Instrucciones

1. Abre [one.newrelic.com](https://one.newrelic.com/) en un navegador y selecciona [**build your own application**](https://one.newrelic.com/launcher/developer-center.launcher#pane=eyJuZXJkbGV0SWQiOiJkZXZlbG9wZXItY2VudGVyLmRldmVsb3Blci1jZW50ZXIifQ==). Sigue las instrucciones.

2. A continuación, clónate este repositorio:

    ```bash
    git clone https://github.com/dhAlcojor/nr1-workshop.git
    ```
    _Nota: Cada ejercicio está en una carpeta diferente. Para seguir el ejercicio hay que ir al directorio correspondiente, ejecutar `npm install`, arrancar el servidor local ejecutando `nr1 nerdpack:serve` y seguir las instrucciones del fichero INSTRUCTIONS.md en dicha carpeta._

3. Arranca el paquete `setup`:

    ```bash
    cd nr1-workshop/setup
    npm install
    nr1 nerdpack:uuid -gf
    nr1 nerdpack:serve
    ```
    
    La salida del terminal debería ser algo parecido a esto:
    ![terminal](screenshots/setup_screen04.png)

4. Abre [one.newrelic.com?nerdpacks=local](https://one.newrelic.com?nerdpacks=local) en un navegador. Deberías ver lo siguiente:
![Congratulations](screenshots/setup_screen05.png)

¿Bien?. [Empecemos.](https://github.com/dhAlcojor/nr1-workshop)
