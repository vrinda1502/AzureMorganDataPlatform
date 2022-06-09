# AzureMorganDataPlatform

Multiple Internal Applications sends the huge data in csv format on daily basis in cloud storage. There are couple of schema validation needs to be performed on incoming data. Once everything passed data to be persisted as delta table in databricks for downstream system.

Following steps are implemented:
1) Internal Application sends the csv file in ADLS(As we are taking 3 files in input folder in ADLS for validation check ->files loaded manually).
![image](https://user-images.githubusercontent.com/44741582/172779594-0ec9b2e2-fce7-455d-bf73-dbe9a8a9986c.png)
2) Validation needs to be applied as follows:
      1) Check for duplicate rows. If it contain duplicate rows file need to be rejected.
      2) Need to Validate the Date format for all the date fields Date column name and desired dateformat is stored in a Azure SQL Server. If validation fails file will be rejected

Dateformat is not in correct format 
![image](https://user-images.githubusercontent.com/44741582/172780078-8a1cc4d1-6c2b-494a-8227-a751455d47ad.png)
Dateformat is in correct format

![image](https://user-images.githubusercontent.com/44741582/172780226-027d80c2-50ff-4433-b694-ec03c1848317.png)

3) Move all the rejected files to Rejected folder.

![image](https://user-images.githubusercontent.com/44741582/172780988-c18eb1eb-2107-4c15-ba43-362062e1fbc9.png)

5) Move all the passed files to staging folder.

![image](https://user-images.githubusercontent.com/44741582/172781129-4c35e50f-2490-4968-b3f8-9cc05dfc3cfa.png)

7) Write all the passed files as the delta table in databricks using storage event trigger.

![image](https://user-images.githubusercontent.com/44741582/172785773-cdc4e1dd-3ef9-46d2-88eb-6715f17e3c07.png)

 
 


