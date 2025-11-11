# QR Code Generator (Spring Boot)

A simple Spring Boot service that generates QR codes on-the-fly and returns them as PNG images. It uses ZXing under the hood.

## Features
- HTTP endpoint to generate QR codes from text
- Returns PNG image directly in the response
- Adjustable width and height

## Prerequisites
- Java 17+
- Gradle (wrapper included)

## Getting Started

### Clone the repository
```
git clone <your-fork-or-clone-url>
cd qrCodeGenerator
```

### Build
```
./gradlew build
```

### Run
```
./gradlew bootRun
```
The application starts on http://localhost:8080 by default.

## API Usage

- Method: GET
- Path: /qr/generate
- Produces: image/png

Query parameters (all required):
- text: String content to encode into the QR code
- width: Integer width of the image in pixels (e.g., 300)
- height: Integer height of the image in pixels (e.g., 300)

### Example
Open in a browser:
```
http://localhost:8080/qr/generate?text=Hello%20World&width=300&height=300
```

Save to a file with curl:
```
curl -G \
  --data-urlencode "text=Hello World" \
  --data-urlencode "width=300" \
  --data-urlencode "height=300" \
  http://localhost:8080/qr/generate \
  --output qrcode.png
```

## Project Structure
- src/main/java/com/bryan/qrcodegenerator/QrCodeController.java: REST controller exposing the QR generation endpoint
- src/main/java/com/bryan/qrcodegenerator/QrCodeGeneratorApplication.java: Spring Boot application entry point
- build.gradle: Dependencies and build configuration

## Dependencies
- Spring Boot Web Starter
- ZXing core and javase
- JUnit + Spring Boot Test for testing

## Testing
```
./gradlew test
```

## Configuration
You can adjust the server port or other Spring properties in:
```
src/main/resources/application.properties
```
For example:
```
server.port=9090
```

## Notes & Tips
- Width and height should be positive integers. Common sizes: 256, 300, 512.
- Make sure to URL-encode the text parameter if calling from a browser or crafting URLs manually.

## License
This project is provided as-is. Add your preferred license text here.
