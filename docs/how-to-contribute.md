# How to contribute

We welcome contributions, The following components can be worked on:

- Tasks:

  - All new tasks are to be added in the tasks directory.
  - Use the example-pr-checks.yaml for any new tests to be added for pull request checks
  - Any other tasks are welcome too.
  - Make sure to add new resource required for the tasks in the resource.yaml

- Pipeline:

  - New pipeline are to be added in the pipeline directory.

- Events:

  - Please create new events for eventlistener, along with the triggertemplate and triggerbindings.

# Want to step up an instance

- Setup Tekton Pipeline and Tekton Trigger in cluster.

```
oc new-project tekton-pipelines
oc adm policy add-scc-to-user anyuid -z tekton-pipelines-controller
oc apply --filename https://storage.googleapis.com/tekton-releases/pipeline/previous/v0.11.3/release.notags.yaml
oc apply --filename https://storage.googleapis.com/tekton-releases/triggers/previous/v0.4.0/release.yaml
oc apply --filename https://github.com/tektoncd/dashboard/releases/download/v0.6.1.5/tekton-dashboard-release.yaml
oc expose svc/tekton-dashboard
```

- If behind the VPN, one time setup components:

  - Ultrahook: ultrahook passes the public internet request to services behind VPN

    - ultrahook secret and deployment with destination as aicoe-ci listener

Create the application with `kustomize build . | oc --namespace ... -f -`

_NOTE_: components can be searched/deleted by label app.<br>
`--selector 'app=aicoe-ci'`
