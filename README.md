# Azure-virtual-wan

User asking how could they manage vHub for the admin different region under the same vWan environment, and can only manage their region's, the method is quite simple.

Just create a vHub under the different RG with the vWan's resources, and assigned IAM for region admin on the specific RG can do the job.

