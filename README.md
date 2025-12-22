# Azure-virtual-wan

User asking how could they manage vHub in different region under the same vWan environment, the method is quite simple.

Just create a vHub under the different RG with the vWan's resources, and assigned IAM for region admin on the specific RG can do the job.

