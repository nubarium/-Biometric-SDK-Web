# Biometric SDK for WEB
Nubarium Biometrics WEB SDK guides for developers.

## SDK compatibility

- Android - Chrome (Version 104 and above)
- Windows - Chrome (Version 56 and above) & Edge
- iOS -  Safari  (Version 14.8 and above)
- MacOS - Safari & Chrome (Version 56 and above)

## Components

The library includes 3 components,

- FaceCapture
- IdCapture
- VideoSelfie

## Installation

Install the Android SDK using Gradle.

### Prerequisites

- You must have your Nubarium credentials. 

### Library

**Step 1: Include the library and it dependencies**

```html
<!-- Third party dependency bundle -->
<script src="//cdn.nubarium.io/nubSdk/nubSdk@latest/nubSdk-third.min.js"></script>
<!-- Library -->
<script src="//cdn.nubarium.io/nubSdk/nubSdk@latest/nubSdk-biometrics.min.js"></script>
```

## Integrate

### Before you begin

- Get the Nubarium Key or API Credentials. It is required to successfully initialize the SDK.
- Implement the REST API call in your back-end to generate the [JWT token](https://github.com/nubarium/-Biometric-SDK-Web/blob/main/JWT.md). 
- All the steps in this document are mandatory unless stated otherwise.

## Initializing the SDK

### Face Capture

#### **Step 1: Initialize the SDK**

**HTML Element**

It is necessary to first declare the HTML Element where the component where the component will be drawn.

```html
<div id="face_component"></div>
```

Then you will need to declare the javascript code that calls the library

```javascript
// Class initialization with the Application Context
let faceCapture = new FaceCapture();

// Define your configuration
let config = {
  rootElement: 'face_component',   // DOM Element that will contains the HTML Component
  timeout: 180000,        // OPTIONAL - Time before expires the test (defaul)
  cameras: ['front', 'back']   // OPTIONAL - Cameras allowed to perform the test
};
// Initialize the component with your custom configuration
faceCapture.init(config);
// Set the JWT token
faceCapture.setToken('eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Im51Y.....'); // YOUR JWT TOKEN
```

#### Step 2: Load the component

Before to start the component you should load the component , in case of any error the event onError will be called.

```javascript
faceCapture.load(()=>{
  // Once that the component is loaded then it will execute the following
  // If you requires to start the component automatically after load its recommend it to start the component.
  faceCapture.start();
}); 
```

#### Step 3: Setting a event listener for results and load

To receive the images and result of component execution it is necessary to setting up a result listener.

```javascript
faceCapture.onSuccess((data) => {
  let id = data.id;
  let result = data.result;
  let face = data.face;
}).onFail((fail) => {
  let reason = fail.reason;
  let result = fail.result;
}).onError((error) => {
  let errorCode = error.code;
  let errorMsg = error.msg;
});
```

#### Step 4: Start component

We recommen to start the component right after the load,  but in case it is required to start the component after specific action you can execute the following command.

```javascript
faceCapture.start();
```

### IdCapture

#### **Step 1: Initialize the SDK**

**HTML Element**

It is necessary to first declare the HTML Element where the component where the component will be drawn.

```html
<div id="id_component"></div>
```

Then you will need to declare the javascript code that calls the library

```javascript
// Class initialization with the Application Context
let idCapture = new IdCapture();

// Define your configuration
let config = {
  rootElement: 'id_component',   // DOM Element that will contains the HTML Component
  timeouts: {
    front: 25000,
    back: 25000
  },       // OPTIONAL - Time before expires the test (defaul)
};
// Initialize the component with your custom configuration
idCapture.init(config);
// Set the JWT token
idCapture.setToken('eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Im51Y.....'); // YOUR JWT TOKEN
```

#### Step 2: Load the component

Before to start the component you should load the component , in case of any error the event onError will be called.

```javascript
idCapture.load(()=>{
  // Once that the component is loaded then it will execute the following
  // If you requires to start the component automatically after load its recommend it to start the component.
  idCapture.start();
}); 
```

#### Step 3: Setting a event listener for results and load

To receive the images and result of component execution it is necessary to setting up a result listener.

```javascript
idCapture.onSuccess((data) => {
  let id = data.id;
  let front = data.front;
  let back = data.back;  
  let result = data.result;
}).onFail((fail) => {
  let id = data.id;  
  let reason = fail.reason;
  let result = fail.result;
}).onError((error) => {
  let errorCode = error.code;
  let errorMsg = error.msg;
});
```

#### Step 4: Start component

We recommen to start the component right after the load,  but in case it is required to start the component after specific action you can execute the following command.

```javascript
idCapture.start();
```

### Video Selfie

#### **Step 1: Initialize the SDK**

**HTML Element**

It is necessary to first declare the HTML Element where the component where the component will be drawn.

```html
<div id="video_component"></div>
```

Then you will need to declare the javascript code that calls the library

```javascript
// Class initialization with the Application Context
let videoRecorder = new VideoRecorder();

// Define your configuration
let config = {
  rootElement: 'video_component',   // DOM Element that will contains the HTML Component
  textToPronounce: 'Yo Juan perez acepto la solicitud de credito',
  timeouts: {
    face: 12000,
    front: 15000,
    back: 13000
  },       // OPTIONAL - Time before the test expires (default)
  requestId: 'bv1234568.96543',  // OPTIONAL - In case you requires to set the text to speech in the backend
  store: false // OPTIONAL - In case you requires to store after 48 hours of recording.
};
// Initialize the component with your custom configuration
videoRecorder.init(config);
// Set the JWT token
videoRecorder.setToken('eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6Im51Y.....'); // YOUR JWT TOKEN
```

#### Step 2: Load the component

Before to start the component you should load the component , in case of any error the event onError will be called.

```javascript
videoRecord.load(()=>{
  // Once that the component is loaded then it will execute the following
  // If you requires to start the component automatically after load its recommend it to start the component.
  videoRecord.start();
}); 
```

#### Step 3: Setting a event listener for results and load

To receive the images and result of component execution it is necessary to setting up a result listener.

```javascript
videoRecord.onSuccess((data) => {
  let id = data.id;
  let result = data.result;
  let similarity = result.similarity;
  let difference = result.difference;
}).onFail((fail) => {
  let id = data.id;  
  let reason = fail.reason;
}).onError((error) => {
  let errorCode = error.code;
  let errorMsg = error.msg;
});
```

#### Step 4: Start component

We recommen to start the component right after the load,  but in case it is required to start the component after specific action you can execute the following command.

```javascript
videoRecord.start();
```


