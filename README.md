ABC Retail - Cloud-Based Order Management Portal
Project Description

This project is a modern, cloud-native web application built for ABC Retail to replace their aging on-premises order processing system. The application leverages the power and scalability of Microsoft Azure to handle customer data, product imagery, order processing, and system logging efficiently.

The portal provides a user-friendly interface for managing key retail operations, demonstrating a practical implementation of various Azure Storage services within a single .NET Core web application.

Features

Customer Management: Create and store customer profiles using Azure Table Storage, a NoSQL key-value store perfect for structured data.

Product Image Hosting: Upload and manage product images using Azure Blob Storage, designed for storing large amounts of unstructured data like images and videos.

Decoupled Order Processing: Place order messages into a reliable queue using Azure Queue Storage, ensuring that orders are processed asynchronously without overwhelming the system during peak times.

System Logging: Log important system activities (like new customers or image uploads) to text files stored in Azure Files Storage, a fully managed cloud file share.

Modern User Interface: A responsive and visually appealing user interface built with Bootstrap and custom CSS, providing a professional experience for users.

Technology Stack

Backend: C#, ASP.NET Core MVC (.NET 6.0+)

Cloud Platform: Microsoft Azure

Web Hosting: Azure App Service

Storage Services:

Azure Table Storage

Azure Blob Storage

Azure Queue Storage

Azure Files Storage

Frontend: HTML5, CSS3, Bootstrap 5

Development Environment: Visual Studio 2022

Prerequisites

Before you begin, ensure you have the following installed:

.NET 6.0 SDK or later.

Visual Studio 2022 with the ASP.NET and web development workload.

An active Microsoft Azure subscription.

Setup and Configuration

Follow these steps to get the application running locally.

1. Azure Storage Setup

Create an Azure Storage Account:

Log in to the Azure Portal.

Create a new Storage Account. A general-purpose v2 account is recommended.

Place it in a new Resource Group (e.g., ABC-Retail-RG).

Configure Storage Services:

Inside your new storage account, navigate to the Data storage section in the left menu.

Tables: Create a new table named CustomerProfiles.

Blobs: Create a new blob container named productimages. Set the public access level to "Blob".

Queues: Create a new queue named orderprocessing.

File Shares: Create a new file share named logfiles.

Get Connection String:

Navigate to Security + networking > Access keys in your storage account.

Copy one of the connection strings. You will need this for the next step.

2. Local Application Setup

Clone the Repository:

git clone <your-repository-url>
cd ABC.Retail.Web

Configure Connection String:

Open the project in Visual Studio.

Find and open the appsettings.json file.

Paste your Azure Storage connection string into the ConnectionString field:

{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "AzureStorageConfig": {
    "ConnectionString": "DefaultEndpointsProtocol=https;AccountName=abcretailstorageaccounts;AccountKey=rmrQOxcaz6v/DaCr9abZPiDqyDGeA/Cc99bLPvG98OWCV+CGArVjPM5V5zIeNxK94euq0U+9i0cj+AStfNYVIA==;EndpointSuffix=core.windows.net"
  }
}

Install Dependencies:

The NuGet packages should restore automatically when you open the project. If not, right-click the solution in Solution Explorer and select "Restore NuGet Packages".

How to Run the Application

Ensure all the setup steps are complete.

Open the project in Visual Studio.

Press F5 or click the "Start Debugging" button (with the green play icon) to build and run the application.

Your default web browser will open, and you will see the ABC Retail Portal home page.

Deployment to Azure

This application is designed to be deployed to Azure App Service.

Publish from Visual Studio:

In Solution Explorer, right-click the ABC.Retail.Web project and select Publish.

Choose Azure as the target and select Azure App Service (Windows).

Create a new App Service instance or select an existing one. It's recommended to use the same Resource Group you created for the storage account.

The name you give the App Service will determine its URL (https://st10161873-dvcyayf6dpg9buhe.canadacentral-01.azurewebsites.net/).

Click Publish. Visual Studio will handle the deployment process.

Test Deployed App:

Once publishing is complete, your browser will open the live URL. Test all functionalities (creating a customer, uploading an image, etc.) to ensure they work correctly in the cloud environment.
