PORTAL DE SOCIOS - FONDO HUMANITARIO PARA COLOMBIA - OCHA 2

index.html reconoce las contraseñas de socios, supervisores por clúster y equipos
PEAS y AAP. Abre automáticamente la vista del acceso, sin elegir un perfil.
peas.html y aap.html conservan los enlaces existentes de los equipos; sus claves
funcionan también en index.html. No necesitan servidor Python, npm ni una API.
El acceso se abre con la contraseña del socio; los datos están cifrados dentro
del HTML y la contraseña se utiliza solo en el navegador. No se envía a GitHub.

PUBLICAR ESTE REPOSITORIO EN GITHUB PAGES
1. Subir los archivos de ESTA carpeta al repositorio en la rama main.
2. En GitHub: Settings > Pages > Build and deployment > Source: GitHub Actions.
3. Ejecutar el workflow o hacer push a main. El workflow publica exclusivamente
   index.html, peas.html, aap.html y .nojekyll. El enlace queda disponible en Pages y en Actions.

ACTUALIZAR DATOS
Los dos scripts de conexión actualizan los tres HTML después de exportar sus CSV.
También se puede ejecutar en la raíz del proyecto OCHA2:
conda run -n DesarrolloVisu python 2_Scripts/generar_portal_socios_ocha2.py
Después hay que subir los tres HTML actualizados (commit y push) para que GitHub
Pages muestre la nueva exportación. La actualización local no hace push.

Las contraseñas están en contrasenas_socios_ocha2.csv, en la raíz del proyecto,
FUERA de esta carpeta publicable. Conservarlas y compartir cada una únicamente
con su socio. No subir el archivo de contraseñas, el .env ni las exportaciones
de Kobo al repositorio del sitio.
Las claves equipo_peas y equipo_aap están en contrasenas_equipos_ocha2.csv,
también en la raíz del proyecto y fuera del sitio publicable. Cada vista de
equipo contiene solo su componente y permite filtrar todos los socios. Las
respuestas individuales de encuestas se mantienen fuera de estos HTML.
Las nuevas claves de supervisión están en contrasenas_supervisores_clusters_ocha2.csv,
en la raíz del proyecto. Los cuatro alcances siguen los sectores operativos del
formulario: Protección de la niñez y acción contra minas, WASH, Salud y nutrición,
y Derechos Humanos. Cada clave solo abre su sector y sus socios. La vista muestra
el consolidado y permite seleccionar un socio, departamento o municipio.
Las claves de socios y equipos existentes se conservan al actualizar.

FECHAS IMPORTANTES
El botón de calendario de la portada permite consultarlo sin contraseña.
Después de ingresar está disponible en Fechas importantes y en el resumen
de próximas fechas de Panorama, para todos los tipos de acceso.
Las ocho ventanas de cargue, cierres y entregas se leen automáticamente de
0_Planeación/0_fechas_claves/Fechas_informes_OneGMS.xlsx al regenerar.
Los textos cualitativos usan la fecha del cierre de datos, según el acuerdo del
taller, y se resaltan en verde azulado. Una fecha pasada no indica si se entregó
o no el reporte. El informe de cierre queda pendiente hasta definir su fecha.

Las contraseñas permanecen al regenerar. Para cambiar una:
conda run -n DesarrolloVisu python 2_Scripts/generar_portal_socios_ocha2.py --rotar-clave CODIGO
Publicar después los tres HTML. Las copias anteriores de un sitio estático
no pueden revocarse remotamente; una contraseña antigua puede abrir una copia
antigua. El portal no sustituye un sistema de usuarios con control en servidor.

METAS Y ALCANCE
Las metas asignadas se leen de Metas por indicador.xlsx, por socio e indicador
y municipio. No se distribuyen por mes. Personas únicas usa las filas R=Sí de
planeación: suma municipal por clúster y máximo independiente de las ocho celdas
IDP/Host y sexo/grupo; Buenos Aires suma clústeres por excepción autorizada.
La cifra de cada socio se recalcula dentro de su alcance; no sumar esas cifras
para obtener el total del proyecto. El acumulado se recalcula hasta el corte.
Es una estimación agregada. Las edades siguen los rangos disponibles del Kobo
(15-18 y desde 19); no se reasignan personas de 18 años sin información individual.
Las variantes de indicadores se agrupan con las equivalencias de OCHA 2.
PERSONAS NO NUEVAS tiene una sección propia en el portal y en Power BI.
El No del formulario core solicita solo personas_no_nuevas_atendidas, sin
desagregaciones. conexion_kobo.py conserva el registro en la base general y
exporta además la hoja Atenciones_no_nuevas y atenciones_no_nuevas_ocha2.csv.
Estas cantidades son atenciones por visita: no se suman a personas nuevas ni
al alcance único. La pestaña respeta filtros, alertas y el escenario elegido.
PEAS/AAP muestra resultados agregados, sin división por entrada/salida y sin metas de muestra. No se
publican respuestas individuales PEAS, datos del personal ni tokens de Kobo.
Los registros sospechosos se resaltan: una coincidencia no confirma duplicidad.
El escenario que cuenta una vez es preliminar; conserva visibles los registros.

Fuentes técnicas:
https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/deriveKey
https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
