# For Users

- **Project** A project can have multiple applications, and a project can be associated with a git repository. To a certain extent, the project is equal to the git repository.
- **Image** A Container image, It's built from the git repository, can be used for the application deployment
- **Application** A server application, can be deploy to multiple environments
- **Deployment** A deployment for every application, support multiple deploy modes, contains Rolling, BlueGreen and Canary 
- **Event** All K8S events related to the application. It's from loki, not from the APIServer of Kubernetes
- **Log** The stdout and stderr logs from pods of the Application
- **Config** The configuration files can be mounted on the Application pods base on the Kubernetes ConfigMap and Secret
- **Environment** Environment variables that can be used by applications
- **Entrypoint** The entrypoint can be visit for the application
- **Route** The route can be setting ratelimit, CORS, MOCK and other for the application
- **Dependent** Middleware or other applications that will be called by the application
- **AccessRule** Rules that control how the application is called by other applications

## For Operators

- **GitProvider** Provide Git repository integrated configuration, provide users with oauth2 way to authorize their own code repository
- **ImageRegistry** Image repository configuration is provided for the built image storage. Support Dockerhub, Github Registry, Google Registry or other self-built image repositories
- **ImageBuilder** CNB image builder. Platform administrators can build image builders supported by their own platforms. For more information, please see CNB
- **Open Application Model(OAM)** brings modular, extensible, and portable design for modeling application deployment with higher level yet consistent API.
- **KubeVela Application** A concrete implementation of OAM, which can contain a set of Components, and each Component can contain multiple Traits. This is a Custom Resource Definition (CRD).
- **KubeVela Component** A Component defines the delivery artifact (binary, Docker image, Helm Chart...) or cloud service included in one application. 
- **KubeVela Trait** Traits are management requirements of an artifact that can be declared with each Component. For example: scale and rollout strategy, persistent storage claim, gateway endpoint and so on.
- **KubeVela Addon** A KubeVela addon is a collection that can contains the defintions of the components and traits. From kubevela's point of view, Kiae is an Addon.
- **Istio Gateway** We use a istio gateway to manage inbound and outbound traffic for your mesh, letting you specify which traffic you want to enter or leave the mesh.
- **Istio VirtualService** A virtual service lets you configure how requests are routed to a service within an Istio service mesh, building on the basic connectivity and discovery provided by Istio and your platform
- **Cloud Native Buildpacks(CNB)** transform your application source code into images that can run on any cloud.
- **Kpack Stacks** A stack resource is the specification for a cloud native buildpacks stack used during build and in the resulting app image. This is a Custom Resource Definition (CRD).
- **Kpack Stores** A store resource is a repository of buildpacks packaged in buildpackages that can be used by kpack to build OCI images. This is a Custom Resource Definition (CRD).
