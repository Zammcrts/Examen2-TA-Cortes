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


### parte 2
#### ticket 1

**Síntoma:** pantalla amarilla al momento de arrancar la app

**Causa raíz:** las urls no coincidian con clase_lista.html y la pantilla de urls

**Corrección:** se cambio *td><a href="{% url 'detalle_clase' clase.pk %}">{{ clase.codigo }}</a></td>* por *<td><a href="{% url 'clase_detalle' clase.pk %}">{{ clase.codigo }}</a></td>*

**Verificación:** ya no se muestra la pantalla amarilla

**Commit:** actualizacion: se arreglo el primer ticket poniendo la referencia de forma correcta a las urls


#### ticket 2

**Síntoma:** La página principal dice que hay 20 clases con lugares disponibles, y no puede ser: Spinning del lunes a las 7:00 (SPN-01) está llena, 20 de 20, y Box del viernes (BOX-03) se canceló. Las dos salen en ?con_lugar=1." Una clase tiene lugar si está activa y tiene menos inscritos que su cupo. Con los datos de recepción deben ser 16.

**Causa raíz:** el filtrado en el models.py *return self.annotate(num_inscritos=Count("inscritos")).filter(num_inscritos__lte=F("cupo")* ya que el parametro es LTE por lo que hasta los que estan llenos pasan a ser contabilizados

**Corrección:** se cambio *num_inscritos__lt=F("cupo")* cambiando LTE a LT, posteriormente se arreglo el *estado=Clase.Estado.ACTIVA*, para solo contabilizar los que esten con estado activo y no llenos

**Verificación:** se muestran ahora 16 clases

**Commit:** acualizacion: se cambio el rango de verificacion para mostrar las clases, pasando de LTE a LT

#### ticket 3

**Síntoma:** En el buscador (/clases/buscar/) escribo 'yoga' y salen 39 resultados. Solo tenemos 4 clases de yoga.

**Causa raíz:** se mostraban datos repetidos el problema *.select_related("disciplina")*

**Corrección:** se anadio *.distinct().select_related("disciplina")*

**Verificación:** se muestran ahora 4 clases correspondientes a yoga

**Commit:** actualizacion> se arreglo la que en la busqueda se mostraran repetidos, de forma que ahora se muestran filtrados

#### ticket 4

**Síntoma:** "La app de recepción intenta crear una clase nueva por la API y el servidor responde error 500." La app envía esto, y la respuesta debe ser 201:

**Causa raíz:** la url que se esta consultando no esta 

**Corrección:** -

**Verificación:** -

**Commit:** -

## Declaración de uso de IA

Marca una opción.

- [ ] No usé asistentes de IA en este examen.
- [ ] Sí usé asistentes de IA. Para cada uso: herramienta, qué le pedí, qué usé de su respuesta y qué revisé o cambié yo.
se empleo chatgpt ya que el intentar arreglar la primera parte relacionado con la integridad de datos, termine cambiando mas de lo que deberia, generando errores que no conocia. Se me apoyo corrigiendo esos errores para regresarle su integridad


## se revisaron los archivos de clases pasas para contrastar la logica
