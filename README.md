# Cuadricóptero Simulación

Este repositorio contiene todo lo necesario para la simulación de un cuadricóptero utilizando **ROS 2**, **Gazebo** y **ArduPilot**. A continuación, se detallan las versiones utilizadas, instrucciones de configuración y un problema conocido.

---

## 🚀 **Versiones Utilizadas**

- **Gazebo Garden:** 7.9.0  
- **ROS 2:** Humble  
- **ArduPilot ArduCopter:** v4.7.0-dev

---

## 🔧 **Configuración del Entorno**

### 1. **Inicialización del Launch File**

Ejecuta un archivo de lanzamiento del paquete `ardupilot_gz_bringup`. Este archivo se encuentra en el directorio `/launch` bajo el nombre `iris_runway.launch.py`.

Para iniciarlo, ejecuta:

```bash
ros2 launch ardupilot_gz_bringup iris_maze.launch.py
```

### 2. **Inicialización de MAVProxy**

Asegúrate de iniciar MAVProxy apuntando al puerto maestro especificado en el launch file.

Ejecuta el siguiente comando:

```bash
mavproxy.py --master udp:127.0.0.1:14550
```

Con esto, ya podrás interactuar con el dron mediante los comandos de MAVProxy.

---

## ⚠️ **Problema Conocido**

El launch file inicializado es el encargado de crear el puente (bridge) para la comunicación entre **ROS 2** y **Gazebo**. Los bridges se generan con el paquete `ros_gz_bridge`, utilizando el ejecutable `parameter_bridge`. Este ejecutable toma como entrada el archivo YAML `iris_bridge.yaml`, ubicado en el directorio `/launch/config`.

### 🔍 **Observaciones**

1. Los topics son visibles al ejecutar:

   ```bash
   ros2 topic list
   ```

2. Sin embargo, al intentar escuchar un topic específico:

   ```bash
   ros2 topic echo /<nombre_topic>
   ```

   No se muestra información; no se está publicando ningún dato.

---

## 📂 **Estructura de Directorios Clave**

- `/models`: Contiene los modelos SDF utilizados por el launch file.
- `/launch`: Archivos de lanzamiento para la configuración del entorno.
- `/launch/config`: Archivo YAML que especifica los bridges.
- `env_bashrc`: Variables de entorno relevantes utilizadas durante el desarrollo.

---

## 🌐 **Workspace Completo**

Puedes acceder al workspace completo y a todos los archivos necesarios desde el siguiente enlace:

[**Descargar Workspace Completo**](https://drive.google.com/file/d/1ZkDIfwzHk8og5frR2m2hEBTuJJRd2brW/view?usp=drive_link)

