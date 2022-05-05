# SI_Final_Project





ITIS-6177 System Integration

Final Project Documentation




INDEX:
1.Introduction
2.Analyze Image Endpoint
3.Text Extraction (OCR) Endpoint





Introduction:
	
	This project employs an API endpoint, which is designed to make calls to the Microsoft Azure computer vision API for the user, so that it would provide a privilege to the user does not require to login with azure, get subscription and use the API. The Computer Vision API provides state-of-the-art algorithms to process images and return information.

This API would serve the purpose of the user. When user makes a call to the API endpoint with URL, the API would invoke Azure API and returns the response to the user. API will employ HTTP protocol with use of axios and developed in Expess.js. All the dependencies used are express, async, fs, https, path, dotenv.


In this two endpoints where called and tested, one is understanding the image, where the url will be given and the respected detail or what the image will be specified through making a call. Next is the OCR where the url to will be given and all the details of the image including the text, angles, bounding box and other details will be displayed.








Security:

In this I used the .dotenv module in order to hide my key and even the endpoint, the environment variables, I created a file on the vscode and executing and got response from both the ends i.e the server and the azure and in order to maintain security I did not expose them on github.



test.env




 





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





 
http://localhost:3000/ComputerVisionOcr



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


 

http://localhost:3000/ComputerVisionAnalyze



 
http://159.203.181.219:3000/ComputerVisionAnalyze



URL to access API Endpoints:

http://159.203.181.219:3000/



 
![image](https://user-images.githubusercontent.com/97813292/166957728-c4bb7446-cf16-4e18-bcd8-6f65c284b491.png)
