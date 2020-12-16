# winningAPI

API Technical Test
==================
I have used Postman along with a newman tool to automate and run the solution for the given API Technical Test.


API Collection for download is available at:
=========================================== 
	GitHub: https://github.com/vkharge/winningAPI.git

	
The solution contains two files:
================================

	1. Postman API Collection: WinningAPITest.postman_collection.json

	   This file has the API Collection which contains 2 requests for case1 and case 2 mentioned in the API Test 

	2. Postman API Environment: WinningAPITestEnv.postman_environment.json

		This file has the environment variables which can be configured to run the tests.
		It contains below environment variables:
			Variable 			Value
			------------------------------------
			server			www.appliancesonline.com.au
			product_slug		samsung-55-inch-tu8000-crystal-uhd-4k-smart-led-tv-ua55tu8000wxxy/
			invalid_slug		invalid_slug		
			responseTime		1000


		server: Server name on which API service is running
		product_slug: Valid product name
		invalid_slug: Invalid product name

		responseTime: Response time threshold which is used for response time validation


API Tests:
=========
	
	Case 1: Get Valid Product Details 
		API EndPoint: GET https://www.appliancesonline.com.au/api/v2/product/slug/samsung-55-inch-tu8000-crystal-uhd-4k-smart-led-tv-ua55tu8000wxxy/

		Validation Performed:
			- Verify Response Code As 200
			- Verify Response Code As OK
			- Verify Response Body Content
			  {
    			"sku": "UA55TU8000WXXY",
    			"productId": 84933
			  }
			  *** The expected data is defined under pre-request script tab which can be modified to meet the validation needs
			- Verify Response Time Threshold


	Case 2: Invalid Product Slug
		API EndPoint: GET https://www.appliancesonline.com.au/api/v2/product/slug/invalid_slug

		Validation Performed:
			- Verify Response Code As 200
			- Verify Response Code As OK
			- Verify Response Time Threshold



Running the API Collection:
===========================
	
	1. Clone the git repo on your system [Assuming git is installed on the system]

	    # git clone https://github.com/vkharge/winningAPI.git

	    # cd winningAPI


	2. Running the API collection from Postman Collection Runner:

			Prerequisite:
				- Install Postman tool

			a. Open the Postman tool

			b. Import the below files in Postman
			   - WinningAPITest.postman_collection.json
			   - WinningAPITestEnv.postman_environment.json

			c. Once the collection is imported in the Postman, it will be shown in left panel

			d. Select on the imported collection, and then click on right arrow

			e. Click on the Run button, this will open Collection Runner

			f. Ensure the Environment is selected as 'WinningAPITestEnv'

			g. Click on RunWinningAPITest button

			h. This will run the API collection

			i. Execution report will be shown under Run Results


		OR

		Running the API collection from CLI using Newman:

			Prerequisite:

				- Install Node.js via package manager [https://nodejs.org/en/download/package-manager/]

				- Install Newman using npm [https://www.npmjs.com/package/newman#getting-started]
					# npm install -g newman

				- Newman HTML Reporter [https://www.npmjs.com/package/newman#external-reporters]
					# npm install -g newman-reporter-html


			a. CLI to run the collection from newman
				
				CLI Format: # newman run <postman_collection.json> -e <postman_environment.json> -r cli,html

				# newman run WinningAPITest.postman_collection.json -e WinningAPITestEnv.postman_environment.json -r cli,html


			b. Execution report is displayed on console and also a HTML report is created under newman directory in current working directory
