# RideCell Project

This repo containes a "main.yml" file under the workflow folder, which containes instruction to build and push the image to DockerHub, which
is later deployed to EKS cluster using "actiondeployment.yml" ! (CI)

It contains a Jenkins file as well which build the same dockerfile as above and pushes it to "AWS_ECR" and the deployed to "AWS_EKS" !(COMPLETE CI/CD)
