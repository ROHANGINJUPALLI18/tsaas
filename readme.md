Terra-Sight project Documentation 

The complete plan of the application is to :-

Map Your Land Draw your land boundary on an interactive map. Takes under 2 minutes(user should also select the daily / weekly / monthly frequency). 
We Capture It Our system pulls satellite images of your parcel on your chosen frequency — daily or weekly. 
AI Analyzes Machine learning models detect any changes — construction, encroachment, vegetation loss. (This is future)
You Get Alerted Instant push notification and email alert with before/after image comparison and a PDF report. (This is future)

For now phase let’s keep the application simple working condition like creating polygon , creating subscription(via webhook or anything related…..) , fetching images from satellite and storing in aws s3 bucket , and working UI 


Frontend :- React
Backend :- Nestjs
DataBase :- postgres
Image storage :- Aws s3 bucket 
Auth :- Google OAuth



Step by step Required  External api’s flow :- (we need to take api’s so, that images should contain good resolution and should satisfy satisfy the subscription frequency (daily , weekly and monthly  ) api by the webhooks (preferably ) that is chosen by the user )



Phase 1 — Account & API access
Do this first, takes ~30 min

1.1Sign up at planet.complanet.com/login▼
1.2Get your API keySettings → API Key▼
1.3Purchase imagery quota (self-service)planet.com/pricing▼
1.4Verify coverage over India with Explorerplanet.com/explorer▼


Phase 2 — Infrastructure setup
AWS S3 + webhook endpoint, before writing any subscription code

2.1Create a dedicated S3 bucketAWS Console▼
2.2Expose your webhook endpoint publiclyngrok for dev▼
2.3Test the Data API with your polygonquick-search▼


Phase 3 — Create your first subscription
Wire Planet → S3 → webhook

3.1Create a test subscription via curlSubscriptions API▼
3.2Check subscription statusGET /subscriptions/v1/:id▼
3.3Simulate a webhook to test NestJS handlercurl POST▼





Phase 4 — Scaling to commercial use
Required before launching paying users
4.1Contact Planet sales for reseller / SaaS agreementRequired for SaaS▼
4.2Apply for Education & Research Program (optional, for MVP testing)Free — 3,000 km²/mo▼
4.3Monitor quota usage & set subscription limitsReports API



Means if the user chooses the weekly frequency then we need to show images taken by the satellite every week , so to automate this process we need to setup the webhook_base_url , so that will connect it to the satellite , so when the satellite takes the new image (after a week ) then it should notify the base_url and as well user to know that there is a new image taken by the satellite and that should be automatically shown in the UI and stored in the s3 bucket and imageUrl in the database 





Endpoints that are required for building the backend :-

Land Parcel
1.1 Create parcel and select the plan 
1.2 Create a subscription for the daily , weekly and monthly update 

Fetch the images from the satellite
Store the image in the s3 bucket and image urls in the database
Get all the fields of the user 
Get particular satellite data by clicking on the field 






Some more routes modules to be added here :-

Auth Module
	
User Module

Parcel Module

Subscription Module

Imagery Module

Webhook Module

Notification Module

Billing Module (later) 


