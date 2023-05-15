# Final-Project-Assessment-for-Scalefocus-Academy-
Final Project Assessment for Scalefocus Academy

Deploy a WordPress on Kubernetes (using Minicube) with Helm and automation with Jenkins.

Prerequisites:
1. Install the necessary tools: Minicube, Helm, and Jenkins.
  (For the needs of the academy and learning the material I downloaded Minicube, Helm, and Jenkins locally)
2. Separate repo in your GitHub Profile named: Final Project Assessment for Scalefocus Academy
   (I created the repository Final Project Assessment for Scalefocus Academy)


Requirement for the Project Assessment:
1. Download Helm chart for WordPress. ( Bitnami chart:
https://github.com/bitnami/charts/tree/main/bitnami/wordpress )
I downloaded this folder wordpress form this repo.To download only the repo I used https://download-directory.github.io/ an put the link:https://github.com/bitnami/charts/tree/main/bitnami/wordpress.

Also I install with this command helm install my-release oci://registry-1.docker.io/bitnamicharts/wordpress
and I got this output 

Pulled: registry-1.docker.io/bitnamicharts/wordpress:16.1.2
Digest: sha256:85dd56b733152b3465145ff5479bbe7f74456a61aaacafc183983002c71ca588
NAME: my-release
LAST DEPLOYED: Mon May 15 17:30:02 2023
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: wordpress
CHART VERSION: 16.1.2
APP VERSION: 6.2.0

** Please be patient while the chart is being deployed **

Your WordPress site can be accessed through the following DNS name from within your cluster:

    my-release-wordpress.default.svc.cluster.local (port 80)

To access your WordPress site from outside the cluster follow the steps below:

1. Get the WordPress URL by running these commands:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: 'kubectl get svc --namespace default -w my-release-wordpress'

   export SERVICE_IP=$(kubectl get svc --namespace default my-release-wordpress --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
   echo "WordPress URL: http://$SERVICE_IP/"
   echo "WordPress Admin URL: http://$SERVICE_IP/admin"

2. Open a browser and access WordPress using the obtained URL.

3. Login with the following credentials below to see your blog:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default my-release-wordpress -o jsonpath="{.data.wordpress-password}" | base64 -d)

with helm list I got this

NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART                   APP VERSION
my-release      default         1               2023-05-15 17:30:02.5524905 +0200 CEST  deployed        wordpress-16.1.2        6.2.0

I down

2. In values.yaml, you need to change line 543 from type: LoadBalancer to type: ClusterIP ( Hint: there
will be one more problem when deploying. Resolve it. )
In the values.yaml I changed type: LoadBalancer to type: ClusterIP.In my case it was line:534 

3. Create a Jenkins pipeline that checks if wp namespace exists, if it doesn’t then it creates one.
Checks if WordPress exists, if it doesn’t then it installs the chart.


4. Name the Helm Deployment as: final-project-wp-scalefocus.
5. Deploy the helm chart using the Jenkins pipeline.
6. Load the home page of the WordPress to see the final result.
7. Explain the project directly in a README.md file in your project repo. 
