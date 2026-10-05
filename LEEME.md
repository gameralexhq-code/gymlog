# GymLog — registro de entrenamiento (Android)

App nativa en Kotlin + Jetpack Compose. Datos 100% en el teléfono (SQLite), sin cuentas ni internet.

## Qué trae

- **Entreno**: registro por día (flechas o toca la fecha), series con peso/reps/RPE/nota, cardio con distancia/tiempo/ritmo. Toca una serie para editarla o borrarla. Muestra "Última vez" y marca 🏆 los récords.
- **Timer de descanso**: arranca solo al guardar una serie (tiempo configurable por ejercicio), ±15 s, vibra y suena al terminar.
- **Rutinas**: rutinas → días → ejercicios con series y rango de reps (ej. 4×6-8). "Iniciar rutina" carga el día y te da una **sugerencia de progresión**: si completaste todas las series en el tope del rango, te propone subir el peso (+2,5 kg configurable).
- **Progreso**: series por grupo muscular (7 días vs promedio), volumen y sesiones de 12 semanas, récords recientes. Por ejercicio: gráficos de 1RM estimado, peso máx, volumen, reps; mejor peso por repeticiones (1RM…12RM) e historial.
- **Cuerpo**: peso, % grasa y cintura con gráfico y cambio en 30 días.
- **Más**: gestionar ejercicios, **importar CSV de FitNotes o Excel (.xlsx/.csv)**, exportar CSV, respaldo/restauración completa (.db).

### Importar tus datos
- **FitNotes**: Ajustes → *Spreadsheet Export* → pasa el CSV al teléfono → GymLog → Más → Importar.
- **Excel propio**: necesita una fila de encabezados con al menos **Fecha** y **Ejercicio**, más **Peso** y **Reps** (o Distancia/Tiempo). También reconoce *Categoría/Grupo, Series, Unidad, Nota, RPE*. Lee todas las hojas del archivo. Si la fecha o el ejercicio están en blanco (celdas combinadas), usa el de la fila anterior. Una columna "Series" = 3 crea 3 series iguales. Importar dos veces el mismo archivo no duplica.

## Cómo compilar e instalar

### Opción A — Android Studio (recomendada)
1. Instala Android Studio (developer.android.com/studio).
2. *File → Open* → elige esta carpeta `GymLog`. Espera que termine el "Gradle sync" (la primera vez descarga cosas, tarda unos minutos).
3. Conecta tu teléfono por USB con *Depuración USB* activada (Ajustes → Acerca del teléfono → toca 7 veces "Número de compilación" → Opciones de desarrollador → Depuración USB).
4. Presiona ▶ Run. La app queda instalada.
   - Para sacar un APK suelto: *Build → Build App Bundle(s) / APK(s) → Build APK(s)*. Queda en `app/build/outputs/apk/debug/app-debug.apk`.

Si Android Studio ofrece actualizar el "Android Gradle Plugin", puedes aceptar.

### Opción B — sin instalar nada (GitHub)
1. Crea un repositorio en GitHub y sube esta carpeta.
2. Ve a la pestaña *Actions*: el flujo "Build APK" compila solo.
3. Descarga el artefacto `GymLog-apk`, pásalo al teléfono e instálalo (permite "instalar apps de origen desconocido").

## Estructura
```
app/src/main/java/cl/alex/gymlog/
  data/Db.kt            base de datos y consultas
  data/Stats.kt         1RM, progresión, formatos
  data/ImportExport.kt  importar CSV/XLSX, exportar, respaldo
  ui/                   pantallas (Compose)
```
