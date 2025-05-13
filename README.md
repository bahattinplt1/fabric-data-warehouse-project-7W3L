# Microsoft Fabric Sample Data Warehouse Project

This project demonstrates step-by-step instructions to create, query, and validate a sample data warehouse in Microsoft Fabric using SQL. It is based on the official Microsoft learning lab: [Query a data warehouse in Microsoft Fabric](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/06b-data-warehouse-query.html).

---

## 📚 Steps

### 1. Create a Workspace
- Navigate to [https://app.fabric.microsoft.com/](https://app.fabric.microsoft.com/).
- Sign in using your Microsoft Fabric credentials.
- In the left menu, select **Workspaces** and create a new workspace (e.g., `FabricDemo`).
- Make sure to select a license mode that includes Fabric capacity (Trial, Premium, or Fabric).

📷 _See `screenshots/step1_workspace_creation.png`_

---

### 2. Create a Sample Data Warehouse
- In the workspace, select **Create** from the sidebar.
- Under the **Data Warehouse** section, choose **Sample warehouse**.
- Name it `sample-dw`.
- Wait for about a minute for sample data to be loaded.

📷 _See `screenshots/step2_sample_warehouse.png`_

---

### 3. Query the Data Warehouse
- Open **New SQL Query**.
- Run the following queries one by one:

#### a. Total trips and revenue by month
```sql
SELECT 
 D.MonthName, 
 COUNT(*) AS TotalTrips, 
 SUM(T.TotalAmount) AS TotalRevenue 
FROM dbo.Trip AS T
JOIN dbo.[Date] AS D
 ON T.[DateID]=D.[DateID]
GROUP BY D.MonthName;
