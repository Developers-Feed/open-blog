---
title: "Creating A Virtual Machine Using CLI in Azure"
datePublished: Sun Aug 20 2023 14:18:41 GMT+0000 (Coordinated Universal Time)
cuid: clljpbdcb00mk2rnv62th7pay
slug: creating-a-virtual-machine-using-cli-in-azure
canonical: https://dev.to/jetsumz/creating-a-virtual-machine-using-cli-in-azure-gap
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692551251134/4b117a1a-c983-4b3b-87b1-04652b85151e.png

---

**1.** The first step would be logging into your Azure portal account.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551239031/a10c16e5-8fbe-44a1-b082-cd4dee09ecff.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--d1A7Zd5l--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1n71rloqufv8yglqps0g.png)

**2.** The second step would be opening the opening the command line interface on the portal.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551240108/f4a063d3-60d0-481e-80f5-5a3547b839ff.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--U6l34h1Z--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yzkwux9ba95iq5n2u3hj.png)

**3.** For the purpose of this particular session, we will be using Powershell instead of Bash. Use the dropdown button to switch to Powershell.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551241323/751095a4-a312-47db-9351-982bfde98081.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--wiJLgUgg--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/34leg0xdew80ah3nblsx.png)

**4.** After switching to Powershell, it should look like similar to the image below.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551242272/e780ea56-2432-4005-b81c-eda78ff1da03.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--N9LnS-01--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/12y8h0daqwxu55fmh5sj.png)

**5.** Create a Resource Group using the syntax below.  
`New-AzResourceGroup -Name 'myCoolerRg' -Location 'EastUS'`  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551243343/792bea15-dc3b-4d42-b159-1e82ae302bfc.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--AGCIpy1k--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cdnfnk2r6epfjfxq0yri.png)

**6.** Create the virtual machine using the syntax below.  

    New-AzVm `
    -ResourceGroupName "myCoolerRg" `
    -Name "myVMps" `
    -Location "WEST US" `
    -VirtualNetworkName "myVnetPS" `
    -SUbnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    
    

Enter fullscreen mode Exit fullscreen mode

[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551244383/17fd8ed3-d71a-4234-a858-697aa85a1377.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--9Hf7yyck--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/nr6m7q63r0p6jqja8cip.png)

**7.** Notice that the code snippet specified above is a multi-line code. This is achieved with the use of the backtick symbol  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551245473/db3d6a45-93e8-46af-b3a0-78186f9c9cb4.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--SqUTdmJU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jf7piju0jmewfq80fiul.png)

**8.** After running the code, you will be prompted to enter the username and password that will later be used to access the virtual machine.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551246482/c92b5607-9bda-499b-902f-8b0bb28d5352.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--aP0Bnz_P--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jpu9k62ic7k3terjz9r1.png)

**9.** Ensure that the password created follows the guidelines specified below otherwise it may not work.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551247789/69a9845e-3215-4011-b21d-fe39f0904dfd.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--1xnN4U0X--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6opmkhcwp9vl347twijo.png)

**10.** After inputting the username and password, you should get the prompt below signifying that the Virtual Machine is being created.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551248865/cde28b50-ec08-4242-8825-2d810ef9db1e.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--gKBW6vQd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lfr7u6ms1u7vh5jugpef.png)

**11.** Once successfully created, you will see a message indicating the creation of the Virtual Machine and the attributes that you had earlier specified.  
[![Image description](https://cdn.hashnode.com/res/hashnode/image/upload/v1692551249942/7e15f08a-6ce3-4f3a-935b-828aec80e52d.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--o6s3WF-U--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3i8ix1jx94x0kyzfp3hm.png)