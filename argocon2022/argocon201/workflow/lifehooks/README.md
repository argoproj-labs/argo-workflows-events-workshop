##LifeHook 

Create workflow 

```
argo submit https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/lifehooks/wf-exit-hook.yaml --watch
```

Output
```
Name:                lifecycle-hook-zp2v8
Namespace:           argo
ServiceAccount:      unset (will run with the default ServiceAccount)
Status:              Running
Conditions:          
 PodRunning          False
Created:             Wed Sep 14 21:07:36 -0700 (3 seconds ago)
Started:             Wed Sep 14 21:07:36 -0700 (3 seconds ago)
Duration:            3 seconds
Progress:            0/2

STEP                            TEMPLATE  PODNAME                                DURATION  MESSAGE
 ⚠ lifecycle-hook-zp2v8         main                                                       template http not found  
 └───◷ step1                    heads     lifecycle-hook-zp2v8-heads-3796436756  3s        PodInitializing          
                                                                                                                             
 ◷ lifecycle-hook-zp2v8.onExit  heads     lifecycle-hook-zp2v8-heads-3995051931  2s        PodInitializing          


```

    
