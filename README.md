# knowlegde-base
Best Practices &amp; RND content


MPPM SWAGGER API DOCS

https://www-ca-1.pmgr.messagepoint.com/api/v1/doc/index.html#/

----------------------------------------------------------------------------------------

API Headers

Authorization : PINC 1b8b9ff9-905a-46a3-97fa-a1a04c346413:&YI2YEr3&rK[ofMY}PkfBoBhR}E+zB

pinc-company-id : 7b0f2093-9f89-9429-4a2b-dadcb690be48

----------------------------------------------------------------------------------------

API Calls

POST - Upload Driver File with pinc-file-name (252595E01.xml) & pinc-file-environment (test/production) & content-type (application/xml)
https://mp.ccpdev.shared.banksvcs.net/api/v1/files

Extract Driver Id from response : "id": "ffa763e2-93f7-47ad-9790-24665df32d93",

----------------------------------------------------------------------------------------

GET - MPPM Application by Touchpoint Name
https://mp.ccpdev.shared.banksvcs.net/api/v1/applications?metadata.mpdc.touchpoint.name=ZZ_AMT-Test

Extract application Id & company Id from response :  
	"id": "75a10c5d-3f5e-4743-a365-7af2ad88602e"
	"companyId": "7b0f2093-9f89-9429-4a2b-dadcb690be48"
	
----------------------------------------------------------------------------------------

GET - MPPM Application Versions using the application Id from above request https://mp.ccpdev.shared.banksvcs.net/api/v1/applications/75a10c5d-3f5e-4743-a365-7af2ad88602e/versions

Extract application version Id i.e. Topmost entry from the response :
	"id": "a6c32019-3f83-43e3-ac6a-9f6f84251b85"

----------------------------------------------------------------------------------------

POST - Create MPPM Job by passing payload 
https://mp.ccpdev.shared.banksvcs.net/api/v1/jobs

{
   "applicationId": "75a10c5d-3f5e-4743-a365-7af2ad88602e",
   "companyId": "7b0f2093-9f89-9429-4a2b-dadcb690be48",   
   "applicationVersionId": "a6c32019-3f83-43e3-ac6a-9f6f84251b85",
   "name": "ZZ_AMT-Test-job", # job-name
   "driverFileIds": [
      "ffa763e2-93f7-47ad-9790-24665df32d93"
    ]
}

Extract MPPM Job Id from response : 
	"id": "31e6f106-d995-4b05-8d7a-7096a076cf69"
	
----------------------------------------------------------------------------------------

GET - Get Job Id details
https://mp.ccpdev.shared.banksvcs.net/api/v1/jobs/31e6f106-d995-4b05-8d7a-7096a076cf69
	
Extract the 3rd result file Id from resultFileIds array:
	 "resultFileIds": [
	        "5fa0931d-fb58-43ad-b2c9-ee6692f1a6b3",
	        "f1e03cc6-ae4b-4245-8187-8f6fabcccc49",
	        "bb2ddac9-477f-40d3-a306-ba9303b88669"
	    ]
	
----------------------------------------------------------------------------------------

GET - Download Result File i.e. PDF
https://mp.ccpdev.shared.banksvcs.net/api/v1/files/bb2ddac9-477f-40d3-a306-ba9303b88669![image](https://github.com/user-attachments/assets/eba15004-2e2d-4b8f-93b7-33120bd2fbd9)
