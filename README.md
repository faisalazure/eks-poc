> **The app is live at :**
>
> I have used secrets in the deployment and cicd. Also used the
> declarative approach with HELM inside kubernetes.
>
> **CICD Approach**

> The CICD approach here we are using is quote simple but according to
> best practice. Below is the breakdown of whole cicd system
>
> 1 and 2 - developer pushes the code from his system to a specific
> branch in github. After qa the branch merges to master\
> 3 - Github actions trigger on the master branch and run the ci
> process.
>
> 4 - Github actions dockerizes the application and uses github secrets
> for any secrets/password/keys that are required to dockerize the app.
>
> 5 - Image pushed to docker repo, in our case it is ECR\
> 6 - once pushed to repo AWS EKS gets the new version of the app and
> deploys it accordingly.
>
> **2a.** - There are multiple choices for the CICD of kubernetes
> application depending upon where we are hosting our source code and
> where the target deployment. For example we can use Github Actions if
> we are hosting code repo in github. AWS CICD services (codepipeline,
> codecommit, codedeploy) are also good candidates for CICD.
>
> We don\'t need to provide access to devs for the deployment process,
> it will be totally automated and without any human intervention. Dev
> can simply push the code and after merging that to master (or any
> other desired branch) the CICD will run. It will dockerize the app,
> push that into a docker repo and deploy the application to kubernetes,
> all automatically. Each CICD service that mentioned above provides
> alerts and notifications on the status of the CICD process, in this
> way we can be assured that the process is working fine or not. Also we
> can use open source monitoring tools on top of the cluster to make
> sure everything is working fine after the\
> deployment. Some of the tools are LENS, Grafana, NewRelic etc.
>
> **i -** To manage secrets inside the CICD process and in kubernetes
> application we have various choices. We can use github secrets during
> CICD, or in AWS we can use AWS Secrets Manager. Also we can use
> Kubernetes Secrets as well for storing application related secrets.
>
> **Ii -** The above part already answers this question. As we can use
> github secrets for CICD or AWS Secrets Manager / Kubernetes Secrets
> for storing application related secrets.
>
> **2b. -** Addons are used to extend the functionality of K8s. We can
> use either HELM charts or Kubernetes Channels to install and manage
> these addons. This thread shows a way to use channels in K8s to manage
> addons\
> Also here is an office doc list of addons (not all)\
> . This doc discusses about various addons installation options and
> management.
