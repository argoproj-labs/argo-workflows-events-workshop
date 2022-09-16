## HTTP Template
### Submit the Workflow
```sh
argo submit https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/http/http-template.yaml --watch
```

Output:
```sh
Name:                http-template-wbcz6
Namespace:           argo
ServiceAccount:      unset (will run with the default ServiceAccount)
Status:              Succeeded
Conditions:          
 PodRunning          False
 Completed           True
Created:             Thu Sep 15 21:44:09 -0700 (36 seconds ago)
Started:             Thu Sep 15 21:44:09 -0700 (36 seconds ago)
Finished:            Thu Sep 15 21:44:45 -0700 (now)
Duration:            36 seconds
Progress:            12/16

STEP                    TEMPLATE    PODNAME  DURATION  MESSAGE
 ✔ http-template-wbcz6  main                                                                
 └─┬─✔ four             http-steps                                                          
   │ └─┬─✖ bad          http                           received non-2xx response code: 404  
   │   ├─✔ good         http                                                                
   │   ├─✔ good-1       http                                                                
   │   └─✔ good-2       http                                                                
   ├─✔ one              http-steps                                                          
   │ └─┬─✖ bad          http                           received non-2xx response code: 404  
   │   ├─✔ good         http                                                                
   │   ├─✔ good-1       http                                                                
   │   └─✔ good-2       http                                                                
   ├─✔ three            http-steps                                                          
   │ └─┬─✖ bad          http                           received non-2xx response code: 404  
   │   ├─✔ good         http                                                                
   │   ├─✔ good-1       http                                                                
   │   └─✔ good-2       http                                                                
   └─✔ two              http-steps                                                          
     └─┬─✖ bad          http                           received non-2xx response code: 404  
       ├─✔ good         http                                                                
       ├─✔ good-1       http                                                                
       └─✔ good-2       http                                                      
```


### Check the Agent POD

![image](https://user-images.githubusercontent.com/33908564/190455443-ef265cfb-dc0d-4b04-b00f-5dc0e6534ad4.png)

