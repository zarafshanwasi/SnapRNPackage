# zmckit-library

`zmckit-library` is a React Native library that simplifies the integration of camera functionalities in your applications. This library seamlessly works with Snap Camera for capturing images and handling lens changes.

## Installation

You can install `zmckit-library` using Yarn or npm:

```sh
# Using Yarn
yarn add https://github.com/idealinktr/zmkit-hybrid

# Using npm
npm add https://github.com/idealinktr/zmkit-hybrid
```

## Permissions

### Android

Add the following permissions to your `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-feature android:name="android.hardware.camera" />
```

### iOS

Add the following key to your `Info.plist`:

```xml
<key>NSCameraUsageDescription</key>
<string>We need access to your camera to capture images.</string>
```

## Usage

### Import Components

Ensure you import the required components from `react-native-zmckit-library`:

```tsx
import {
  SingleProductView,
  GroupProductView,
} from "react-native-zmckit-library";
```

### Using `SingleProductView`

```tsx
<SingleProductView
  apiToken="YOUR_API_TOKEN"
  lensId="YOUR_LENS_ID"
  groupId="YOUR_GROUP_ID"
  onImageCaptured={(imageUri) => console.log("Image captured:", imageUri)}
/>
```

#### Props for `SingleProductView`

| Prop              | Type     | Required | Default | Description                   |
| ----------------- | -------- | -------- | ------- | ----------------------------- |
| `apiToken`        | string   | Yes      | -       | API authentication token      |
| `lensId`          | string   | Yes      | -       | Lens ID for single product    |
| `groupId`         | string   | Yes      | -       | Group ID for single product   |
| `showFrontCamera` | boolean  | No       | `false` | Enable front camera           |
| `showPreview`     | boolean  | No       | `true`  | Show preview before capturing |
| `onImageCaptured` | function | Yes      | -       | Callback for image capture    |

### Using `GroupProductView`

```tsx
<GroupProductView
  apiToken="YOUR_API_TOKEN"
  groupId="YOUR_GROUP_ID"
  onImageCaptured={(imageUri) => console.log("Image captured:", imageUri)}
  onLensChange={(lensId) => console.log("Lens changed to:", lensId)}
/>
```

#### Props for `GroupProductView`

| Prop              | Type     | Required | Default | Description                   |
| ----------------- | -------- | -------- | ------- | ----------------------------- |
| `apiToken`        | string   | Yes      | -       | API authentication token      |
| `groupId`         | string   | Yes      | -       | Group ID for group products   |
| `showFrontCamera` | boolean  | No       | `false` | Enable front camera           |
| `showPreview`     | boolean  | No       | `true`  | Show preview before capturing |
| `onImageCaptured` | function | Yes      | -       | Callback for image capture    |
| `onLensChange`    | function | No       | -       | Callback for lens change      |

## Additional Resources & Features

### React Native Sample App

You can find a sample app demonstrating the integration at the following link:  
[React Native Sample App](https://drive.google.com/drive/folders/10qr4T16XDY64S_Hzmhae06-SLLf0fCx-?usp=sharing)

### Android Share Feature

The share feature is available under preview. To enable it for Android, please add the following configuration to your `AndroidManifest.xml`:

```xml
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="${applicationId}.provider"
    android:exported="false"
    android:grantUriPermissions="true">
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/file_paths" />
</provider>
```

And include this `file_paths.xml` under `res/xml/`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <cache-path name="cache" path="." />
</paths>
```

## License

This library is licensed under the [MIT License](LICENSE).
