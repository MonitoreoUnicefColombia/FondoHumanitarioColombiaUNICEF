PORTAL DE SOCIOS - FONDO HUMANITARIO PARA COLOMBIA - OCHA 2

index.html es el acceso de socios; peas.html y aap.html son los accesos separados
de los equipos PEAS y AAP. No necesitan servidor Python, npm ni una API.
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

Las contraseñas permanecen al regenerar. Para cambiar una:
conda run -n DesarrolloVisu python 2_Scripts/generar_portal_socios_ocha2.py --rotar-clave CODIGO
Publicar después los tres HTML. Las copias anteriores de un sitio estático
no pueden revocarse remotamente; una contraseña antigua puede abrir una copia
antigua. El portal no sustituye un sistema de usuarios con control en servidor.

METAS Y ALCANCE
Las metas asignadas se leen de Metas por indicador.xlsx, por socio e indicador
y municipio. No se distribuyen por mes y no se suman como personas únicas.
Las variantes de indicadores se agrupan con las equivalencias de OCHA 2.
PEAS/AAP muestra resultados agregados y no tiene metas de muestra. No se
publican respuestas individuales PEAS, datos del personal ni tokens de Kobo.
Los registros sospechosos se resaltan: una coincidencia no confirma duplicidad.
El escenario que cuenta una vez es preliminar; conserva visibles los registros.

Fuentes técnicas:
https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/deriveKey
https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
