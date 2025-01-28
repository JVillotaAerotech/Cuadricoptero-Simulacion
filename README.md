# Cuadricoptero-Simulacion

Este repositorio contiene todo lo necesario para la simulación de un cuadricóptero utilizando ROS 2, Gazebo y ArduPilot. A continuación, se detallan las versiones utilizadas, instrucciones de configuración y un problema conocido.

---

## **Versions**
- **Gazebo Garden**: 7.9.0
- **ROS 2**: Humble
- **ArduPilot ArduCopter**: v4.7.0-dev

---

## **Setup**

El proceso de configuración consta de los siguientes pasos:

### **1. Inicialización del Launch File**
Se debe iniciar un launch file del paquete `ardupilot_gz_bringup`. Este archivo puede encontrarse en el directorio `/launch` con el nombre `iris_runway.launch.py`.

Ejecuta el siguiente comando:

```bash
ros2 launch ardupilot_gz_bringup iris_maze.launch.py
```

### **2. Inicialización de MAVProxy**
Asegúrate de iniciar MAVProxy apuntando al puerto maestro especificado en el launch file.

Ejecuta el siguiente comando:

```bash
mavproxy.py --master udp:127.0.0.1:14550
```

Con esto, ya puedes interactuar con el dron mediante los comandos de MAVProxy.

---

## **Problema Conocido**

El launch file inicializado es el encargado de crear el puente (bridge) que permite la comunicación entre ROS 2 y Gazebo. Los bridges se generan con el paquete `ros_gz_bridge`, utilizando el ejecutable `parameter_bridge`. Este ejecutable toma como entrada el archivo YAML `iris_bridge.yaml`, que se encuentra en el directorio `/launch/config`.

### **Observaciones**:
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
## **Ficheros clave**
En los directorios /models se pueden encontrar los modelos sdf sobre los que bebe el launch file.
En el directorio /launch se pueden encontrar los ficheros launch relativos al setup mencionado
En el directorio /launch/config se puede encontrar el fichero YAML que especifica los bridges que se crean.
En el fichero env_bashrc se muestra variables de entorno relevantes sobre las que se ha trabajado.

## **Workspace Completo**

Puedes encontrar el workspace completo y todos los archivos necesarios en el siguiente enlace:

[Enlace al Workspace](https://drive.google.com/file/d/1ZkDIfwzHk8og5frR2m2hEBTuJJRd2brW/view?usp=drive_link)


  

