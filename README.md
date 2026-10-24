# 🚗 CarsWash – Sistema de Gestión de Carwash en Python

Sistema de gestión para un carwash desarrollado en **Python** aplicando **Programación Orientada a Objetos (POO)**. Permite registrar clientes y sus vehículos, contratar un servicio de lavado, pagar con distintos medios y hacer seguimiento del estado de cada auto en una fila de espera.

Incluye dos interfaces: una por **consola** y una **interfaz gráfica** simple hecha con `tkinter`.

---

## ✨ Características

- Registro de clientes (nombre y RUT) y de su vehículo (patente, marca, modelo, puertas).
- Dos tipos de servicio:
  - **Lavado Básico** – $8.000 – 20 min.
  - **Lavado Premium** (incluye encerado) – $15.000 + IVA (19%) – 40 min.
- Dos medios de pago: **efectivo** y **tarjeta**.
- Un único puesto de lavado: los autos esperan en **cola** y pasan a lavarse automáticamente.
- Cálculo del tiempo estimado de espera para cada auto.
- Simulación del paso del tiempo para ver cómo avanza la fila.
- Ciclo de vida del auto: `Registrado, sin servicio → En espera → En proceso de lavado → Finalizado`.

---

## 🖥️ Interfaces

### Interfaz gráfica (tkinter)

```bash
python interfaz_gui.py
```

Tres pestañas que siguen el flujo del sistema:

1. **Registro:** alta de cliente y de su auto.
2. **Servicio y pago:** selección de servicio y medio de pago, con confirmación del total.
3. **Estado:** estado del puesto, tabla de clientes/autos y avance del tiempo de simulación.

### Consola

```bash
python main.py
```

Menú interactivo con las opciones: registrar cliente, registrar auto, contratar servicio y pagar, ver estado, avanzar tiempo y salir.

---

## ⚙️ Requisitos

- Python 3.9 o superior.
- `tkinter` (solo para la interfaz gráfica). Viene incluido con Python en Windows y macOS. En Linux:

  ```bash
  sudo apt install python3-tk
  ```

No se necesitan librerías externas.

---

## 🚀 Cómo ejecutar

```bash
git clone https://github.com/<tu-usuario>/<tu-repositorio>.git
cd <tu-repositorio>

# Interfaz gráfica
python interfaz_gui.py

# o interfaz por consola
python main.py
```

---

## 🗂️ Estructura del proyecto

| Archivo | Descripción |
|---|---|
| `main.py` | Punto de entrada de la versión por consola. |
| `interfaz_gui.py` | Interfaz gráfica con tkinter. |
| `menu_console.py` | Menú e interacción por consola. |
| `carwash_controller.py` | Controlador que orquesta la atención y el cobro. |
| `cola_lavado.py` | Administra la fila de autos y el paso del tiempo. |
| `cliente.py` | Clase `Cliente` (dueño de un vehículo). |
| `vehiculo.py` | Clase base `Vehiculo` con su estado de servicio. |
| `auto.py` | Clase `Auto`, hereda de `Vehiculo`. |
| `servicio.py` | Clase abstracta `Servicio`. |
| `lavado_basico.py` / `lavado_premium.py` | Servicios concretos. |
| `pagable.py` | Interfaz `Pagable` (contrato de pago). |
| `pago_efectivo.py` / `pago_tarjeta.py` | Medios de pago concretos. |
| `estado_servicio.py` | Enumeración `EstadoServicio`. |

---

## 🧠 Conceptos de POO aplicados

- **Clases y objetos, abstracción:** `Cliente`, `Vehiculo`, `Servicio`, etc.
- **Encapsulamiento:** atributos "privados" con `_` y acceso mediante `@property`.
- **Herencia:** `Auto` hereda de `Vehiculo`; `LavadoBasico` y `LavadoPremium` heredan de `Servicio`.
- **Clases abstractas:** `Servicio` define el método abstracto `calcular_precio()`.
- **Interfaces:** `Pagable` define el contrato `pagar()`, implementado por `PagoEfectivo` y `PagoTarjeta`.
- **Polimorfismo:** el controlador cobra y calcula precios sin saber qué servicio o medio de pago concreto recibe.
- **Composición:** un `Cliente` *tiene un* `Vehiculo`; el menú *tiene un* controlador y una cola.
- **Enumerados:** `EstadoServicio` limita los estados posibles del vehículo.
- **Estructuras de datos y control:** listas, diccionarios, condicionales y ciclos.

---

## 🔄 Flujo de uso

1. Registrar al **cliente**.
2. Registrar el **auto** del cliente.
3. Elegir el **servicio** y el **medio de pago**.
4. Si el pago es exitoso, el auto entra a la fila (o pasa directo al lavado si el puesto está libre).
5. Consultar el **estado** y **avanzar el tiempo** para ver cómo se completan los lavados.

---

## 🔮 Posibles mejoras

- Persistencia de datos (archivo o base de datos).
- Nuevos tipos de vehículo (camioneta, moto) y nuevos servicios.
- Nuevos medios de pago, sin modificar el resto del sistema gracias a la interfaz `Pagable`.
- Validación de RUT y de número de tarjeta.
- Pruebas unitarias.

---

## 📄 Licencia

Proyecto académico / de uso libre. Agrega aquí la licencia que prefieras (por ejemplo, MIT).
