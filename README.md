# ROS2 Workspace del Dron

Este repositorio proporciona un espacio de trabajo ROS2 para simular y controlar un dron utilizando el paquete [ArduPilot Gazebo Bringup](https://github.com/ardupilot/ardupilot_gz_bringup) y MAVProxy. La configuración te permite lanzar la simulación del dron y conectarte a ella usando MAVProxy.

## Prerrequisitos

- **ROS2:** Asegúrate de tener instalada la distribución ROS2 Humble.
- **ArduPilot y Gazebo:** El paquete `ardupilot_gz_bringup` debe estar correctamente configurado en tu espacio de trabajo.
- **MAVProxy:** Instala MAVProxy para conectarte y controlar el dron.
- **Dependencias:** Asegúrate de que todas las dependencias necesarias estén instaladas en tu espacio de trabajo ROS2.

## Instalación

1. **Descargar el workspace:**

   Descarga el espacio de trabajo desde Google Drive en la carpeta `detection_drone`.

2. **Fuente del entorno ROS2:**

   ```bash
   source /opt/ros/humble/setup.bash
   ```

3. **Compilar el espacio de trabajo:**

   Usa `colcon` para compilar el espacio de trabajo:

   ```bash
   colcon build
   ```

4. **Fuente del espacio de trabajo:**

   Después de compilar, fuente el archivo de configuración del espacio de trabajo:

   ```bash
   source install/setup.bash
   ```

## Uso

### Lanzar la simulación del dron

```bash
ros2 launch ardupilot_gz_bringup iris_runway.launch.py
```

### Conectarse con MAVProxy

```bash
mavproxy.py --master udp:127.0.0.1:14550
```

## Solución de problemas

- **Entorno ROS2 no cargado:**  
  Asegúrate de haber cargado el archivo de configuración correcto de ROS2 (`/opt/ros/humble/setup.bash`) y el `install/setup.bash` de tu espacio de trabajo antes de lanzar la simulación.

- **Problemas de conexión con MAVProxy:**  
  Verifica que la simulación esté en ejecución y que el puerto UDP `14550` esté disponible. Ajusta el parámetro `--master` si es necesario.

