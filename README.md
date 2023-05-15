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

4. Name the Helm Deployment as: final-project-wp-scalefocus.
5. Deploy the helm chart using the Jenkins pipeline.
6. Load the home page of the WordPress to see the final result.


7. Explain the project directly in a README.md file in your project repo
