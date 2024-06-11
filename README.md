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
