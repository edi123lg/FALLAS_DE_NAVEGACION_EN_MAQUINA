# Fallas de navegación en máquina virtual — INC-02

## Descripción del proyecto

Este repositorio documenta la atención y resolución del incidente **INC-02**, relacionado con la imposibilidad de navegar por Internet desde una máquina virtual utilizada en el entorno de trabajo.

El trabajo se realizó como parte de la actividad de Mesa de Servicio de TI de la materia Sistemas Operativos, de la carrera de Ingeniería de Sistemas de la Universidad Privada Franz Tamayo.

El objetivo fue identificar la causa de la falla, ejecutar las comprobaciones necesarias, corregir la configuración de red y verificar la recuperación del acceso a Internet, dejando constancia del procedimiento y de las evidencias obtenidas.

## Estado del incidente

**Estado: RESUELTO**

Se identificó una configuración incorrecta de los servidores DNS en las propiedades de red de la máquina. Aunque existía conectividad con una dirección IP pública, no era posible navegar correctamente mediante nombres de dominio.

La configuración de TCP/IPv4 se modificó para obtener automáticamente la dirección IP y los servidores DNS mediante DHCP. Después del cambio, se verificó que la navegación web funcionaba nuevamente.

## Diagnóstico y solución

### Síntoma inicial

La máquina virtual no podía acceder correctamente a sitios web, incluido YouTube, pese a que las pruebas de conectividad directa por IP respondían satisfactoriamente.

### Comprobaciones realizadas

Se ejecutaron las siguientes acciones durante el diagnóstico:

1. Verificación del estado inicial de la navegación web.
2. Ejecución del comando `ping 8.8.8.8` desde la consola de Windows.
3. Inspección de las propiedades del adaptador de red y de la configuración TCP/IPv4.
4. Identificación de servidores DNS configurados manualmente que no permitían la resolución de nombres.
5. Modificación de las propiedades de red para obtener automáticamente la dirección IP y los servidores DNS.
6. Validación del acceso a Internet después de aplicar los cambios.

### Causa identificada

La configuración manual de los servidores DNS utilizaba las direcciones `192.168.201.201` y `192.168.10.10`, que no permitían resolver correctamente los nombres de dominio en el entorno analizado.

La respuesta satisfactoria del comando `ping 8.8.8.8` permitió comprobar que existía conectividad IP hacia una dirección pública, orientando la investigación hacia la configuración DNS.

### Solución aplicada

Se accedió a las propiedades del protocolo de Internet versión 4 (TCP/IPv4) del adaptador de red y se seleccionaron las opciones:

- **Obtener una dirección IP automáticamente.**
- **Obtener la dirección del servidor DNS automáticamente.**

De esta manera, la máquina pudo recibir su configuración de red mediante DHCP.

### Validación del resultado

Después de aplicar la corrección, se comprobó que:

- La máquina obtenía automáticamente los parámetros de red.
- La navegación web se había restablecido.
- YouTube cargaba correctamente.
- El incidente de acceso a Internet quedaba resuelto.

## Estructura del repositorio

```text
FALLAS_DE_NAVEGACION_EN_MAQUINA/
├── README.md
├── EQUIPO
├── GUIA_ACTIVIDAD/
│   └── MESA DE SERVICIO DE TI_Incidente02.docx
└── _EQUIPO PROFESIONAL DE TI.pdf
```

### Documentación disponible

- **[Guía de la actividad y registro del incidente](GUIA_ACTIVIDAD/MESA%20DE%20SERVICIO%20DE%20TI_Incidente02.docx):** documento de trabajo de la Mesa de Servicio de TI.
- **[Informe del equipo profesional de TI](%5FEQUIPO%20PROFESIONAL%20DE%20TI.pdf):** contiene la documentación del diagnóstico, las evidencias visuales, la solución aplicada y las conclusiones.
- **[Integrantes y distribución de responsabilidades](EQUIPO):** identifica a los responsables de las distintas funciones del equipo.

## Equipo de trabajo

| Integrante | Responsabilidad |
|---|---|
| Josías Arze | Coordinación del incidente y operación técnica |
| Edilson Lazarte | Análisis e investigación |
| Max Mamani | Evidencias y documentación |
| Gabriel Oconor | Continuidad y relevo |

## Conclusiones

El incidente permitió comprobar la importancia de diferenciar los problemas de conectividad IP de los problemas de resolución DNS.

La respuesta satisfactoria del comando `ping 8.8.8.8` fue un elemento importante para orientar el diagnóstico. La inspección de las propiedades TCP/IPv4 permitió identificar la configuración DNS incorrecta y aplicar una solución acorde con el entorno de red.

Finalmente, la recuperación de la navegación web confirmó la efectividad de la corrección aplicada.

## Información académica

- **Universidad:** Universidad Privada Franz Tamayo (UNIFRANZ)
- **Carrera:** Ingeniería de Sistemas
- **Materia:** Sistemas Operativos
- **Paralelo:** 1
- **Docente:** Ing. Diego Patrick Cardenas Sejas
- **Ubicación:** Cochabamba, Bolivia
- **Fecha:** Octubre de 2026
