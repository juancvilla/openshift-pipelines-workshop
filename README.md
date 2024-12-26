Pasos para generar el workshop

```git clone https://github.com/redhat-developer-demos/openshift-pipelines-workshop```

```cd openshift-pipelines-workshop```

```oc login --token=sha256~...5N0 --server=https://api.sandbox-m3.1530.p1.openshiftapps.com:6443```

```oc apply -f qotd-pipeline.yaml```

 ```oc create -f workspace.yaml```

```oc create -f apply_manifest_task.yaml```

Si no esta instalado tekton, instala con el comando:

```brew install tektoncd-cli```

```tkn pipeline start qotd-build-and-deploy -w name=shared-workspace,claimName=source-pvc -p git-url=https://github.com/redhat-developer-demos/qotd.git -p IMAGE=image-registry.openshift-image-registry.svc:5000/nombreDeTuProyecto-dev/qotd:latest```

Para ver como va el avance de los pasos de la canalización (pipeline), ejecutar:

```tkn pipelinerun logs qotd-build-and-deploy-run-... -f -n nombreDeTuProyecto-dev```

