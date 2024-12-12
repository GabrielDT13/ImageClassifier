# Clasificador de Imágenes con PyTorch

Este proyecto implementa un clasificador de imágenes basado en una red neuronal convolucional (CNN) utilizando **PyTorch**. El modelo clasifica imágenes en diferentes categorías, tomando como referencia datasets personalizados. El código soporta tanto CPU como GPU para acelerar el entrenamiento.

---

## Características
- Entrenamiento de una red neuronal convolucional (CNN) personalizada.
- Uso automático de GPU si está disponible.
- Predicción inicial antes del entrenamiento y validación después del entrenamiento.

---

## Requisitos

### Software Necesario
- Python 3.8 o superior
- PyTorch (con soporte para CUDA si se usará GPU)
- Visual Studio (opcional, si usas este IDE)
- Google Colaboratory

### Bibliotecas de Python
Asegúrate de instalar las siguientes dependencias:

```bash
pip install torch torchvision matplotlib pillow
```

Si planeas descargar datasets desde Kaggle, también instala:

```bash
pip install kaggle kagglehub
```

---

## Estructura del Proyecto

El proyecto espera que el dataset descargado tenga la siguiente estructura:

```
┌── dataset/
│   ├── train/
│   │   ├── clase_1/
│   │   └── clase_2/
│   └── test/
│       ├── clase_1/
│       └── clase_2/
```

- **train/**: Imágenes para el entrenamiento del modelo.
- **test/**: Imágenes para la validación del modelo.

Cada subcarpeta dentro de `train` y `test` corresponde a una clase.

---

## Configuración

### 1. Configurar el Dataset
1. Descarga o prepara tu dataset.
2. Organiza las imágenes según la estructura descrita anteriormente.
3. Actualiza las rutas del dataset en el código:
   ```python
   train_dir = "ruta_a_tu_dataset/train"
   test_dir = "ruta_a_tu_dataset/test"
   ```

### 2. Verificar el Dispositivo
El código selecciona automáticamente el dispositivo (GPU o CPU):
```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
```

### 3. Configurar Visual Studio (opcional)
Si usas Visual Studio:
1. Configura el entorno Python que contiene PyTorch.
2. Asegúrate de que las dependencias estén instaladas en este entorno.
3. Ejecuta el proyecto desde Visual Studio.

---

## Ejecución del Proyecto

### Entrenamiento
Ejecuta el código para entrenar el modelo. Durante el entrenamiento:
1. El modelo procesa las imágenes del directorio `train`.
2. Evalúa la precisión en las imágenes del directorio `test` después de cada epoch.

### Predicción de una Nueva Imagen
Puedes probar el modelo con una imagen nueva después del entrenamiento:
1. Asegúrate de que la imagen tiene formato RGB.
2. Coloca la ruta de la imagen en el código:
   ```python
   new_image_path = "ruta_a_tu_imagen/nueva_imagen.jpg"
   ```
3. El modelo predecirá la clase de la imagen y mostrará el resultado.

---

## Resultados
Al finalizar el entrenamiento, el código muestra:
- La pérdida promedio por epoch.
- La precisión en el conjunto de validación.
- La predicción para una imagen.

---

## Problemas Comunes

### 1. `ModuleNotFoundError`
Si obtienes este error para alguna biblioteca, verifica que esté instalada en el entorno correcto:
```bash
pip install nombre_de_la_biblioteca
```

### 2. `CUDA Out of Memory`
Si estás usando GPU y se agota la memoria:
- Reduce el tamaño del batch (`batch_size`):
  ```python
  train_loader = DataLoader(train_dataset, batch_size=16, shuffle=True)
  ```

### 3. `List Index Out of Range`
Este error puede ocurrir si el dataset está mal configurado. Verifica que las carpetas `train` y `test` contengan subcarpetas con imágenes.

---

## Tecnologías Utilizadas
- **PyTorch**: Framework principal para construir y entrenar el modelo.
- **TorchVision**: Para transformaciones de imágenes y DataLoaders.
- **Matplotlib**: Para la visualización de resultados.
- **Pillow**: Para cargar y manipular imágenes.

---

## Futuras Mejoras
- Implementar aumento de datos para mejorar el rendimiento del modelo.
- Guardar y cargar modelos entrenados con `torch.save` y `torch.load`.
- Incorporar métricas adicionales como la matriz de confusión y la F1-Score.

---

## Autor
Este proyecto fue creado con el objetivo de aprender sobre clasificación de imágenes y el uso de PyTorch. Si tienes preguntas o sugerencias, no dudes en contactarme.

---

## Licencia
Este proyecto está bajo la licencia MIT. Puedes utilizarlo libremente para tus propios fines educativos y comerciales.

