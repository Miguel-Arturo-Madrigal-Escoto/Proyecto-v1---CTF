<h1>PROYECTO</h1>
<h6>Oswaldo Gael Cervantes Castoño</h6>
<h6>Kevin Arturo Fernández Román</h6>
<h6>Aide Sarahí Flores Ontiveros</h6>
<h6>Miguel Arturo Madrigal Escoto</h6>
<h6>José Ulises Vallejo Sierra</h6>

<h4>GitHub</h4>	
<ol>
  <li><strong>Clonar</strong> el repositorio</li>
</ol>

<h4>Docker</h4>	
<ol>
  <li>Elaborar los Dockerfile de cada microservicio (api-auth, api-events, frontend) (si es que no se tienen los dockerfiles)</li>
  <li>Subirlos a DockerHub</li>
  <li>Crear un docker-compose.yaml con los 3 microservicios, donde la imagen es para cada microservicio la de Dockerhub.</li>
  <li>Para probar que funcionen los 3 microservicios en sus respectivos contenedores, en la raiz del proyecto se escribe el comando: docker-compose up</li>
  <li>Una vez probado y ver que funcione, se puede detener con: docker-compose down.</li>
</ol>

<h4>Kubernetes</h4>	
<ol>
  <li><strong>minikube</strong> start</li>
  <li><strong>kompose</strong> convert (si no se tienen los yaml de los microservicios)</li>
  <li><strong>kubectl</strong> apply -f .\auth-api-deployment.yaml,.\auth-api-service.yaml,.\events-api-deployment.yaml,.\events-api-service.yaml,.\webmvc-deployment.yaml,.\webmvc-service.yaml</li>
  <li><strong>kubectl</strong> get pods</li>
  <li><strong>kubectl</strong> get services</li>
  <li><strong>kubectl</strong> port-forward svc/webmvc 3000:3000</li>
  <li><strong>kubectl</strong> port-forward svc/events-api 4001:4001</li>
  <li><strong>kubectl</strong> port-forward svc/auth-api 4000:4000</li>
  <li><strong>minikube</strong> dashboard</li>
  <li><strong>minikube</strong> dashboard --url</li>
</ol>

<h4>Istio</h4>	
<ol>
  <li>Si no se tiene istio, instalar istioctl.</li>
  <li><strong>kubectl</strong> apply -f .\auth-api-deployment.yaml,.\auth-api-service.yaml,.\events-api-deployment.yaml,.\events-api-service.yaml,.\webmvc-deployment.yaml,.\webmvc-service.yaml</li>
  <li>Comando injected: <strong>kubectl</strong> label namespace default istio-injection=enabled</li>
  <li>Observar herramientas de monitoreo y analisis, en especial la ubicacion de Kiali: <strong>kubectl</strong> get svc -n istio-system</li>
  <li>Redigir el trafico al puerto de Kiali (20001): <strong>kubectl</strong> port-forward svc/kiali -n istio-system 20001</li>
  <li>Acceder en el navegador a localhost:20001</li>
</ol>

<h4>OpenShift</h4>	
<ol>
  <li>Crear por separado un repositorio para cada microservicio.</li>
  <li>Subir en cada repositorio el microservicio.</li>
  <li>Crear una cuenta de OpenShift (si no se tiene).</li>
  <li>En el apartado de "ADD", crear una aplicación importando desde GitHub.</li>
  <li>Completar el formulario con el url del repositorio de GitHub y en "import strategy" seleccionar node.js</li>
  <li>Dar en la opción "crear"</li>
  <li>(Esto es para cada microservicio)</li>
  <li>Esperar a que build termine de cada microservicio para acceder en la URL.</li>
  <li>Crear el build de la aplicacion de react con: <strong>npm</strong> run build</li>
  <li>Crear un servidor con el framework node.js y usar el middleware app.use(express.static('./public)), en la carpeta public debera ir el build de la aplicacion de React.</li>
  <li>Guardar los cambios en github</li>
  <li>En el microservicio del frontend volver a hacer el build del mismo para cargar los cambios del repositorio de github</li>
  <li>Acceder en la URL a la aplicación conectada con las 2 RESTFul APIs.</li>
</ol>
