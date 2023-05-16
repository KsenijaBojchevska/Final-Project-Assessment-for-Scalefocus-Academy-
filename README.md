Final Project Assessment 

Deploy a WordPress on Kubernetes (using Minicube) with Helm and automation with Jenkins.


Prerequisites:
1. Install the necessary tools: Minicube, Helm and Jenkins.
   (For the needs of the academy and learning the material I downloaded Minicube, Helm, and Jenkins locally)
2. Separate repo in your GitHub Profile named: Final Project Assessment for Scalefocus Academy
   (I created the repository Final Project Assessment for Scalefocus Academy)
   
Requirement for the Project Assessment:
1. Download Helm chart for WordPress. ( Bitnami chart: https://github.com/bitnami/charts/tree/main/bitnami/wordpress )
   I downloaded this folder wordpress form this repo.To download only the repo I used https://download-directory.github.io/ an put the link:    https://github.com/bitnami/charts/tree/main/bitnami/wordpress. 
 
2. In values.yaml, you need to change line 543 from type: LoadBalancer to type: ClusterIP ( Hint: there
   will be one more problem when deploying. Resolve it. )
   In the values.yaml I changed type: LoadBalancer to type: ClusterIP.In my case it was line:534
   
3. Create a Jenkins pipeline that checks if wp namespace exists, if it doesn’t then it creates one.
   Checks if WordPress exists, if it doesn’t then it installs the chart.
   
   First I create New Item, and named ksenija.The project was created with Pipeline.In the Pipeline Definition I choose scripted pipeline so I connected
    my project with my github repo and in the GitHub repo I created Jenkinsfile. In the Jenkinsfile I put the code for the pipeline and it check if there
    is a namespace wp.
     And if there is not for now it print namespace not found.
     
     I have this console output
 
 
 Started by user Ksenija Bojchevska
Obtained Jenkinsfile from git https://github.com/KsenijaBojchevska/Final-Project-Assessment-for-Scalefocus-Academy-.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in C:\ProgramData\Jenkins\.jenkins\workspace\ksenija
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
 > git.exe rev-parse --resolve-git-dir C:\ProgramData\Jenkins\.jenkins\workspace\ksenija\.git # timeout=10
Fetching changes from the remote Git repository
 > git.exe config remote.origin.url https://github.com/KsenijaBojchevska/Final-Project-Assessment-for-Scalefocus-Academy-.git # timeout=10
Fetching upstream changes from https://github.com/KsenijaBojchevska/Final-Project-Assessment-for-Scalefocus-Academy-.git
 > git.exe --version # timeout=10
 > git --version # 'git version 2.40.0.windows.1'
 > git.exe fetch --tags --force --progress -- https://github.com/KsenijaBojchevska/Final-Project-Assessment-for-Scalefocus-Academy-.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git.exe rev-parse "refs/remotes/origin/master^{commit}" # timeout=10
Checking out Revision 2774f64bc917d0278a675c3a531dff0eeb411987 (refs/remotes/origin/master)
 > git.exe config core.sparsecheckout # timeout=10
 > git.exe checkout -f 2774f64bc917d0278a675c3a531dff0eeb411987 # timeout=10
Commit message: "Update Jenkinsfile"
 > git.exe rev-list --no-walk 2014f20be19eb307bb45af34bc8035e5e72980d2 # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (check wp)
[Pipeline] script
[Pipeline] {
[Pipeline] echo
namespace not found
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS.








4. Name the Helm Deployment as: final-project-wp-scalefocus.
5. Deploy the helm chart using the Jenkins pipeline.
6. Load the home page of the WordPress to see the final result.


7. Explain the project directly in a README.md file in your project repo
