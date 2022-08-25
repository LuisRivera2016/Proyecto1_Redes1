# Redes 1: Proyecto 1 
|Grupo 2| Carnet | Nombre |
| --- | --- | --- |
| Coordinador | 201602813 | Luis Enrique Rivera Najera |
| Compañero 2 | 201602880 | Bryan Alexander Portillo Alvarado  |
| Compañero 3 | 201709073 | Walter Alexander Guerra Duque |
| Compañero 4 | 201403793 | Kevin Nicolas Garcia Martinez |

# Manual Tecnico 

## Comandos

- **_config t_** : este comando permite acceder al modo configuración global desde el modo privilegiado.

- **_int f#/#_** : este comando permite seleccionar algun puerto de un switch para aplicarle alguna configuración.

- **_vtp domain_** : este comando permite asignar un dominio a un switch. Los switches que se encuentren en el mismo dominio de VTP comparten su información de VLAN entre sí, y un switch puede participar en solo un dominio de administración de VTP.

- **_vtp password_** : este comando protege las actualizaciones de VTP estableciendo una contraseña segura.

- **_vtp mode client_** : este comando hace que el switch este en modo cliente, este modo no permite a un switch cambiar su configuración de VLAN. Eso significa que un switch cliente VTP no puede crear ni eliminar VLAN. Sin embargo, las actualizaciones de VTP recibidas se procesan y reenvían.

- **_vtp mode server_** : este comando permite que un switch anuncie sus configuraciones de VLAN a otros switches en el mismo dominio VTP y sincronizar sus configuraciones de VLAN con otros switches en función de los anuncios recibidos a través de enlaces troncales. Estos switches si pueden crear y eliminar VLANs.

- **_vtp mode transparent_** : este comando permite que un switch no sincronice la configuracion de las VLAN con otros switches aunque, puede enviar la informacion de las VLAN. Estos switches si pueden crear y eliminar VLANs pero solo locales no del VTP server.

- **_switchport mode access_** : este comando establece el puerto en modo acceso.

- **_switchport mode trunk_** : este comando pone la interfaz en modo de enlace troncal permanente y negocia para convertir el enlace vecino en un enlace troncal.

- **_switchport trunk allowed vlan_** : este comando se usa para especificar la lista de VLAN que están permitidas en un puerto troncal.

- **_spanning-tree vlan [VLAN] root primary_** : este comando se utiliza para asignar el valor con menor prioridad.

## Topologías 

### Topologia 1

![](https://github.com/LuisRivera2016/Proyecto1_Redes1/blob/main/img/topologia1.png)

**---------------------------------------------- Configuración ESW1 ----------------------------------------------**

```sh
config t
vtp domain GRUPO2
vtp password grupo2
vtp mode client
```

Configuración modo trunk para fa1/0, fa1/1 y fa1/2
```sh
int f1/0
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

```sh
int f1/1
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

```sh
int f1/2
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

**---------------------------------------------- Configuración ESW2 ----------------------------------------------**
```sh
config t
vtp domain GRUPO2
vtp password grupo2
vtp mode client
```

Configuración modo acces/trunk para fa1/0, fa1/1, fa1/2 fa1/3 y fa1/4 
```sh
int f1/0
switchport mode access
switchport access vlan 10
```

```sh
int f1/1
switchport mode access
switchport access vlan 30
```

```sh
int f1/2
switchport mode access
switchport access vlan 10
```

```sh
int f1/3
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

```sh
int f1/4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

**---------------------------------------------- Configuración ESW3 ----------------------------------------------**
```sh
config t
vtp domain GRUPO3
vtp password grupo3
vtp mode client
```

Configuración modo access/trunk para fa1/0, fa1/1, fa1/2 fa1/3 y fa1/4 
```sh
int f1/0
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```

```sh
int f1/1
switchport mode access
switchport access vlan 30
```

```sh
int f1/2
switchport mode access
switchport access vlan 40
```

```sh
int f1/3
switchport mode access
switchport access vlan 20
```

```sh
int f1/4
switchport mode trunk
switchport trunk allowed vlan 1,10,20,30,40,1002-1005
```



Se utiliza el siguiente comando para switches

```sh
sh vtp st
```

![](https://github.com/LuisRivera2016/Proyecto1_Redes1/blob/main/img/vtp_esw1_topologia1.png)


Se utiliza el comando: 
```sh
sh vlan-sw 
```
para ver las configuaraciones aplicadas 

![](https://github.com/LuisRivera2016/Proyecto1_Redes1/blob/main/img/esw1_topologia1.png)

**RRHH_1**

```sh
ip 192.168.31.10/24 192.168.31.1
```

**Conta_1**

```sh
ip 192.168.33.10/24 192.168.33.1
```

**RRHH_2**

```sh
ip 192.168.31.20/24 192.168.31.1
```

**Conta_2**

```sh
ip 192.168.33.20/24 192.168.33.1
```

**Informatica_1**

```sh
ip 192.168.32.10/24 192.168.32.1
```

Configuración para: CLOUD1

```sh
Local:4001
Remoto:4002
```

![](https://github.com/LuisRivera2016/Proyecto1_Redes1/blob/main/img/CLOUD1_TOPO1.png)

### Topologia 2

### Topologia 3

