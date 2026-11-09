# Modelo Relacional de Bases de Datos 14



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos para una plataforma de cocina y recetas comunitarias, enfocado en el control de miembros, recetas, pasos de preparación, ingredientes, relaciones ingrediente-receta y reseñas.

---

## Estructura de Tablas y Atributos



### 1. Miembro



* **PK (Clave Primaria):** `id_Miembro`


* **Atributos:**
* `nombre`


* `tipo_perfil`


* `fecha_registro`


* `correo_electronico`





### 2. Receta



* **PK (Clave Primaria):** `id_codigo_receta`


* **Atributos:**
* `porciones`


* `titulo`


* `descripción`


* `tiempo_preparación`


* `dificultad`




* **FK (Claves Foráneas):**
* `id_Miembro` (asociado a la tabla Miembro)





### 3. Paso



* **PK (Clave Primaria):** `id_paso`


* **Atributos:**
* `imagen`


* `tiempo_estimado`


* `numero_paso`


* `descripcion_detallada`




* **FK (Claves Foráneas):**
* `id_codigo_receta` (asociado a la tabla Receta)





### 4. Ingrediente



* **PK (Clave Primaria):** `id_codigo_ingrediente`


* **Atributos:**
* `nombre`


* `unidad_medida`


* `descripción`


* `categoria`





### 5. Receta_ingrediente



* **FK (Claves Foráneas):**
* `id_codigo_receta` (asociado a la tabla Receta)


* `id_codigo_ingrediente` (asociado a la tabla Ingrediente)




* **Atributos:**
* `cantidad`





### 6. Reseña



* **PK (Clave Primaria):** `id_reseñas`


* **Atributos:**
* `fecha_publicacion`


* `comentario`


* `puntuación`




* **FK (Claves Foráneas):**
* `id_codigo_receta` (asociado a la tabla Receta)


* `id_Miembro` (asociado a la tabla Miembro)





---

## Relaciones Principales



* **Miembro y Receta:** Un miembro de la comunidad puede publicar múltiples recetas, vinculándose a través de `id_Miembro`.


* **Receta y Paso:** Una receta se compone de varios pasos explicativos estructurados de forma secuencial mediante `id_codigo_receta`.


* **Receta e Ingrediente (Receta_ingrediente):** La relación de muchos a muchos entre recetas e ingredientes se gestiona mediante la tabla intermedia `Receta_ingrediente`, especificando la cantidad requerida para cada uno.


* **Receta, Miembro y Reseña:** Las valoraciones y comentarios de las recetas son registrados por los miembros en la tabla `Reseña`, asociando `id_codigo_receta` e `id_Miembro`.
