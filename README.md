# iac-and-gitops
Notes from DevSecOps ch.10 IaC and GitOps for DevSecOps

IaC saves lots of time when scaling infrastructure
Also from a security aspect, it avoids misconfigurations that come with manual errors
Since infra is now code being run, this also provides an opportunity to run scans on this code to detect any potential security issues

1. Write terraform script 
<img width="1073" alt="Capture d’écran 2024-06-11 à 21 57 07" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/054bdc11-6c3c-4175-b5eb-92ca43a58f83">

2. Create terraform AWS user for running the script + create gitlab runner - add credentials to the tf vars
<img width="553" alt="Capture d’écran 2024-06-11 à 21 56 54" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/64212a03-6ec3-4de1-aa2b-956df7a8b628">

3. Run terraform init + terraform plan
<img width="610" alt="Capture d’écran 2024-06-11 à 22 12 12" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/edb2b028-f4fe-4c7b-aec5-a73d0c787448">

4. Run terraform apply
<img width="726" alt="Capture d’écran 2024-06-11 à 22 23 52" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/24ae372b-bff6-44cc-9232-c4bdcd16b8cf">

5. Run the pipeline with the provisioned infra

GitOps: git as single source of truth
Benefit from git versioning and collaborative flows (merge requests, commits etc)
can run tests on infra code, security scans
-> DevOps for infra

6. Create dedicated pipeline for infra
<img width="440" alt="Capture d’écran 2024-06-11 à 22 54 32" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/958f6597-b0c7-4317-aa5a-3f69bb5fc99c">

7. Configure remote terraform state and attach policy for S3 to the user
<img width="348" alt="Capture d’écran 2024-06-12 à 21 47 21" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/c6bd6322-22df-4efd-b4b9-834e86d14251">
<img width="1290" alt="Capture d’écran 2024-06-12 à 21 47 28" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/7991d7ae-b13a-453f-b5d8-3c2a4a0b7a17">
<img width="339" alt="Capture d’écran 2024-06-12 à 21 57 55" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/1a1b0526-4188-4819-bf8f-60eadd00c0d4">
<img width="825" alt="Capture d’écran 2024-06-12 à 22 04 40" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/8069d8b0-280a-4745-bb15-ebaa196b504f">
<img width="591" alt="Capture d’écran 2024-06-12 à 22 10 34" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/9e9046e8-7003-4231-90a1-86dd9f8aba9b">


8. Add code syntax test to infra pipeline
tf has native 'validate' cmd
<img width="237" alt="Capture d’écran 2024-06-12 à 22 10 50" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/29ae5fc2-3bf2-4a8b-a862-f681c810f419">

10. Add security scan to pipeline
Security scanner for tf: tfsec
<img width="745" alt="Capture d’écran 2024-06-12 à 22 24 13" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/0e5a002f-1993-4070-8f3b-5a986500f739">
<img width="727" alt="Capture d’écran 2024-06-12 à 22 25 52" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/98bb10de-e561-4b13-8763-dbd60d1f7502">
<img width="348" alt="Capture d’écran 2024-06-12 à 22 20 52" src="https://github.com/JulienAvezou/iac-and-gitops/assets/62488871/0bf03ffc-3056-4d68-9430-b42a0a512fac">


Concept cattle vs pets:
treat servers as interchangeable resources that can be created, destroyed and replaced on demand
