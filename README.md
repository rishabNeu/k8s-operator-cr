# k8s-operator

This will help you understand how to write `Operators` using `Kubebuilder` SDK which will help create a Custom Resource Definition, Custom Resource, Controllers and Reconciliation logic.
Basically, Reconcile the `current` state to the `desired` state

## :mechanical_arm: Operator

- S/w that runs within k8s
- eventual consistency which it will get in the desired state what was expected
- Any changes you do in type.go file run the `make manifests` command

```bash
# any changes to types file run the below command
make manifests

```

## :brain: Kubebuilder

- After bootstrapping, you will notice a set of generated directories and files. Each has its specific purpose:

  `Dockerfile`: A Dockerfile used for building a containerized version of the operator.

  `Makefile`: A Makefile containing targets for building, testing, and deploying the operator.

  `PROJECT`: A YAML file containing project metadata.

  `api/`: A directory that will contain the API definitions for our CRDs.

  `internal/controllers/`: A directory that will contain the controller implementations.

  `config/`: A directory that contains different configuration on how your operator would be deployed and interact with k8s cluster

  `cmd/main.go`: The entrypoint of our operator.

## :microbe: CR and CRD

- Think of `CRDs` as the definition of our **custom Objects**, while `CRs` are **instances** of them.

## :seedling: Sample which the Kubebuilder provides

- sample is a folder which provides a sample custom resource i.e an object ( YAML file)
- This can be used to edit it as per the req to work with in cluster

## :jigsaw: Schema

- `TypeMeta` (which describes API version and Kind), and also contains `ObjectMeta`, which holds things like name, namespace, and labels.

## :traffic_light: Controller

- Each controller implements a control loop that watches the cluster's shared state via the API server and makes changes needed, consistently bringing it back to the desired state.
- Operators’ controllers run in the worker nodes.

## :yo_yo: Reconciler

- In every controller, the reconciler is the logic that’s triggered by cluster events. The reconcile function takes the name of an object and returns whether or not the state matches the desired state.
- Need to implement the logic in the internal/controller/operator_controller.go file in the function `Reconcile()`

> Note: make install will install our custom resource in the k8s cluster
> make run will connect to the k8s cluster

## :dart: Validation & Markers

- markers, such as `+kubebuilder:validation:Minimum=1`
- These markers help in defining validations and criteria, ensuring that data provided by users — when they create or edit a Custom Resource for the **XYZ Kind** is properly validated.

```bash
+kubebuilder:validation:Minimum=1
+kubebuilder:validation:Maximum=3

```

## :ninja: Author

[Rishab Agarwal](mailto:agarwal.risha@northeastern.edu)
