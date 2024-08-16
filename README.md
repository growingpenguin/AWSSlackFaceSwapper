# AWSSlackFaceSwapper
Learned how to lauch FaceSwapper Canvas Application in AWS Universe Day <br/>
![Workflow1](https://github.com/user-attachments/assets/547585f5-dd79-4ba5-8b0b-cf9469204a7c) <br/>
**1.User Uploads Image via Canva (Frontend)** <br/>
The user interacts with Canva, which is the frontend of your application <br/>
The user uploads an image through Canva <br/>
**2.Canva Requests a Pre-signed URL** <br/>
Canva (the frontend) sends a request to an AWS Lambda function asking for a pre-signed URL <br/>
This URL allows the image to be securely uploaded to an S3 bucket without needing direct access to S3 <br/>
**3.Canva Uploads the Image to S3** <br/>
Canva receives the pre-signed URL from the Lambda function and uses it to upload the user's image directly to the S3 bucket <br/>
**4.S3 Triggers a Lambda Function** <br/>
Once the image is successfully uploaded to S3, this triggers another Lambda function (using S3 event notifications) <br/>
**5.Lambda Processes the Image Using the AI Model** <br/>
The triggered Lambda function retrieves the uploaded image from S3 and sends it to an AI model running on an EC2 instance (or within the Lambda function if it’s small enough) to perform tasks like face detection, face swapping, or any other AI-based processing <br/>
**6.Processed Image is Saved Back to S3** <br/>
The AI model processes the image and the resulting processed image is saved back to the S3 bucket <br/>
**7.Lambda Generates a Pre-signed URL for the Processed Image** <br/>
After saving the processed image, Lambda generates another pre-signed URL for the processed image and sends this URL back to Canva.
**8.User Views the Processed Image on Canva** <br/>
Canva receives the pre-signed URL for the processed image and displays the image to the user, allowing them to see the result of the AI processing <br/>


https://kinocoder.tistory.com/13 <br/>
