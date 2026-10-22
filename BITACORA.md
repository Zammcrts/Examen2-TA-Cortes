# Bitácora del examen

**Nombre:** Edna Samantha Cortes Carrisoza
**Repositorio:** https://github.com/Zammcrts/Examen2-TA-Cortes.git

Copia el bloque de abajo una vez por cada falla que encuentres. Llénalo en el momento, no al final.

---

## Falla N (Parte 1 / Ticket N / F1 / F2 / Extra)

### parte 1

**Síntoma:** error al hacer las migraciones, asi mismo al relacionar su disciplina con su nombre. Error de que deberia de ser unico, y no se podian crear por ser duplicados

**Causa raíz:** el problema de las migraciones se encontraba en las settings.py, ya que no se declaraba en INSTALLED_APPS la base de datos, posteriormente, al momento de cargar los datos, se tenia como create la disciplina, lo que hacia que no se pudieran mandar las tuplas

**Corrección:** settings.py: se agrego la DB, */'gimnasio',/*, y en cargar_datos, se cambio a get_or_create, para evitar el problema de los duplicados, asi mismo se agregaron modifico el parametro para recibir las tuplas, y se agrego *.strip()*. *disciplina, _ = Disciplina.objects.get_or_create(nombre=fila["disciplina"].strip())*

**Verificación:** se pudieron generar las migraciones marcando OK, y se agregaron los datos, enviando el mensaje de creados

**Commit:** actualizacion: no se declaraba la base de datos en INSTALLED APP por lo que no se podia migrar
actualizaion de la clase Disciplina y de la carga de datos para que el nombre de la disciplina sea unico y se pueda crear correctamente asi  como del archivo cargar_datos.py para que se cree la disciplina si no existe y se asigne a la clase correspondiente

---

## Declaración de uso de IA

Marca una opción.

- [ ] No usé asistentes de IA en este examen.
- [ ] Sí usé asistentes de IA. Para cada uso: herramienta, qué le pedí, qué usé de su respuesta y qué revisé o cambié yo.
