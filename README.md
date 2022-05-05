# SI_Final_Project





ITIS-6177 System Integration

Final Project Documentation




INDEX:
1.Introduction
2.Text Extraction (OCR) Endpoint
3.Analyze Image Endpoint





Introduction:
	
	This project employs an API endpoint, which is designed to make calls to the Microsoft Azure computer vision API for the user, so that it would provide a privilege to the user does not require to login with azure, get subscription and use the API. The Computer Vision API provides state-of-the-art algorithms to process images and return information.

This API would serve the purpose of the user. When user makes a call to the API endpoint with URL, the API would invoke Azure API and returns the response to the user. API will employ HTTP protocol with use of axios and developed in Expess.js. All the dependencies used are express, async, fs, https, path, dotenv.


In this two endpoints where called and tested, one is understanding the image, where the url will be given and the respected detail or what the image will be specified through making a call. Next is the OCR where the url to will be given and all the details of the image including the text, angles, bounding box and other details will be displayed.








Security:

In this I used the .dotenv module in order to hide my key and even the endpoint, the environment variables, I created a file on the vscode and executing and got response from both the ends i.e the server and the azure and in order to maintain security I did not expose them on github.



test.env


<img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958104-ea29503d-a2bf-494c-878e-434890c6d381.png">


 





Text Extraction (OCR)  Endpoint:

OCR: Optical Character Recognition (OCR) is used to detect text in an image and extracts the recognized characters into a machine-usable character stream. Upon success, the OCR results will be returned.
Upon failure, the error code together with an error message will be returned. The error code can Internal Server error, Image URL error, Not supported Image, Not supported language.



API RESPONSE

URL-    http://159.203.181.219:3000/ComputerVisionOcr

Request body: 
{
    "url":"https://images.unsplash.com/photo-1610878180933-123728745d22?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Y2FuYWRhJTIwbmF0dXJlfGVufDB8fDB8fA%3D%3D&w=1000&q=80"
}


RESPONSE-

{
    "response": [
        "Recognized text:",
        "Nutrition Facts Amount Per Serving",
        "Serving size: 1 bar (40g)",
        "Serving Per Package: 4",
        "Total Fat 13g",
        "Saturated Fat 1.5g",
        "Amount Per Serving",
        "Trans Fat 0g",
        "alories 190",
        "Cholesterol Omg",
        "ories from Fat 110",
        "Sodium 20mg",
        "nt Daily Values are based on",
        "Vitamin A 50%",
        "calorie diet"
    ]
}




<img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958200-8fb3a7bb-9771-469f-9dc1-2e269cca7704.png">

 
http://localhost:3000/ComputerVisionOcr

<img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958250-840f30ed-b37e-4ace-ab7d-a6c66e9790ac.png">


 http://159.203.181.219:3000/ComputerVisionOcr




Analyze Endpoint:

Understanding the image API endpoint gets the image details and will provide the content of the image. It will give a privilege specifying image URL from web to understand and let us know what is the image. To leverage the maximum features of the API, query parameters with details would require to use, which are optional yet very useful parameters for this API endpoint.


API RESPONSE

URL- http://159.203.181.219:3000/ComputerVisionAnalyze




Request body: 
{
    "url" : "https://media.npr.org/assets/img/2021/08/11/gettyimages-1279899488_wide-f3860ceb0ef19643c335cb34df3fa1de166e2761-s1100-c50.jpg"
}


RESPONSE:

{
    "response": "Tags: cat (0.99), small to medium-sized cats (0.99), domestic cat (0.99), animal (0.99), mammal (0.98), indoor (0.97), felidae (0.97), whiskers (0.96), cat furniture (0.92), domestic short-haired cat (0.91), furniture (0.89), malayan cat (0.88), chair (0.81), wall (0.77), white (0.73), black (0.65)"
}


 <img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958321-b0c1f99f-0a81-429d-89ac-8ca189bf3c79.png">

 

http://localhost:3000/ComputerVisionAnalyze


<img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958364-b7c15083-ff3d-4f86-b9cc-0604d55d8811.png">

 
http://159.203.181.219:3000/ComputerVisionAnalyze


Status Codes:

1.	200: Success
2.	400: Invalid arguments, Invalid Request
Ex: application/json

{
    "error": {
        "code": "InvalidRequest",
        "message": "Input data is not a valid image.",
        "innererror": {
            "code": "InvalidImageFormat",
            "message": "Input data is not a valid image."
        }
    }
}

  3.  415: Unsupported media type error

  Ex: application/json

   {
      "code": "BadArgument",
      "message": "Invalid Media Type"
    }

   4. 500: Internal Service Error
         
      Ex: application/json
       
       {
      "error": {
       "code": "InternalServerError",
         "message": "Internal server error"
                 }
       }

      5. 503: Service Unavailable

        Ex: application/json
 
        {
          "error": {
            "code": "ServiceUnavailable",
                   "message": "The service is temporarily unavailable.",
                     "innererror": {
                      "code": "ServiceUnavailable",
                       "message": "The service is temporarily unavailable."
                     }
                }
            }




URL to access API Endpoints:

http://159.203.181.219:3000/


<img width="468" alt="image" src="https://user-images.githubusercontent.com/97813292/166958413-caac78ee-6b22-4d51-a306-456bc3a510e9.png">

 

