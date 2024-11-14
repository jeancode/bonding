## Script de Enlace para Linux
====================

Este script se utiliza para configurar enlaces en máquinas Linux y para determinar qué grupos de interfaces (pares) están disponibles para el enlace.

**Características**
--------

* Determinación de grupos de interfaces (pares)
* Configuración de enlaces de interfaces en Linux

**Sistemas operativos compatibles**
---------------------------

* Red Hat Enterprise Linux (Versiones >= 5)
* CentOS (Versiones >= 5)
* Fedora (Versiones >= 10)
* Debian (Versiones >= 5)
* Ubuntu (Versiones >= 10.04)

**Uso**
-----

    $ python bonding.py --help
    Uso:
      bonding.py [--nopeers]
      bonding.py --onlypeers
      bonding.py --automated
      bonding.py --unattend --bond=BOND --ip=ADDR --netmask=MASK --iface=IFACE1 
                 --iface=IFACE2 [--iface=IFACE3 ...] [--gateway=GW] [--mode=MODE]

    Un script utilizado para configurar enlaces en máquinas Linux y para determinar qué
    grupos de interfaces (pares) están disponibles para el enlace.
    ------------------------------------------------------------------------------
    https://github.com/sivel/bonding

    Opciones:
      -h, --help           mostrar este mensaje de ayuda y salir
      --version            Mostrar el número de versión y salir

      Pares:
        --onlypeers        Solo ejecutar la parte de pares de esta utilidad, para identificar
                           las interfaces pares enlazadas
        --nopeers          No ejecutar la parte de pares de esta utilidad
        --peerswait=SECS   El número de segundos para esperar la negociación del puerto del conmutador. Predeterminado 5

      Sin supervisión:
        --automated        Si ejecutar este comando de forma automatizada, esto es
                           diferente a sin supervisión, que requiere información
                           sobre cómo configurar el enlace. Esta opción no requiere
                           opciones adicionales y las ignorará
        --unattend         Si ejecutar este comando sin supervisión
        --bond=BOND        El nombre de la interfaz maestra enlazada. Requerido al utilizar
                           --unattend
        --ip=IP            La dirección IP a utilizar en el enlace. Requerido al utilizar
                           --unattend
        --netmask=NETMASK  La máscara de red a utilizar en el enlace. Requerido al utilizar
                           --unattend
        --iface=IFACE      Las interfaces a utilizar en el enlace, especifique varias veces
                           para varias interfaces. Requerido al utilizar
                           --unattend
        --gateway=GATEWAY  La puerta de enlace predeterminada a utilizar para el sistema, si esto está
                           especificado, se actualizarán la puerta de enlace y el dispositivo de puerta de enlace.
                           predeterminado: ninguno
        --mode=MODE        El modo de enlace a utilizar. predeterminado: activo-backup

**Códigos de Salida**
----------

### Genérico

    1: Error genérico
    2: No se proporcionaron todas las opciones para una configuración sin supervisión

### Automatizado

    100: No hay interfaces que contengan la ruta predeterminada
    101: El dispositivo de puerta de enlace ya es una interfaz maestra/enlazada
    102: No hay una dirección IP configurada en el dispositivo que contiene la ruta predeterminada.
    103: No hay una máscara de red configurada en el dispositivo que contiene la ruta predeterminada.
    104: El enlace automatizado solo funcionará cuando haya exactamente 2 interfaces pares, se encontraron más de 2.
    105: La interfaz ya forma parte de un enlace

### Sistema operativo

    200: SO no compatible
    201: El directorio de copia de seguridad ya existe
    202: Red Hat Network Manager habilitado
    203: El paquete Debian ifenslave no está instalado o no se puede ubicar
    204: Las interfaces que comienzan con __tmp existen, lo que indica que las interfaces de red están mal configuradas

**Errores**
----

Enviar errores, solicitudes de características, etc. como [Problemas][1]

**Contribuyendo**
------------

1. Haz un fork
2. Crea una rama
3. Haz un commit
4. Pushea
5. Haz una solicitud de pull

[1]: https://github.com/sivel/bonding/issues

