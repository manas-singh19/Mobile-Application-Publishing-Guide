# Mobile-Application-Publishing-Guide


Mobile Application Publishing Guide
Google Play Store — Complete Step-by-Step Reference

Part 1: Setup Your Application
Before releasing your app, you must complete all required setup steps in the Google Play Console. Navigate to your app dashboard and click "Setup Your App" to begin.

Step 1 — Privacy Policy
You will need live website URLs for the following policy pages:
Privacy Policy
Refund Policy
Terms of Service / About Terms

💡 Tip: Make sure all URLs are publicly accessible and hosted on a live domain before proceeding.


Step 2 — App Access
Choose one of the two options below based on how your app handles user access:

Option A — No Access Restrictions
Select "All functionality in my app is available without any access restrictions" if your app is completely free to use and does not require users to log in.

Option B — Restricted Access (Login Required)
Select "All or some functionality in my app is restricted" if your app requires users to log in. Then follow these sub-steps:

Click on "Instructions" and provide a username and password for the Google reviewer to use for testing.
Enter a meaningful name for the test account.
In the text area below, enter clear instructions explaining how to access and use the provided demo credentials.
Check the box: "No other information is required to access my app."
Click "Add" and then "Save."

Step 3 — Ads
If your app does not display any ads, select: "No, my app does not contain ads."
If your app does display ads, select the appropriate option and carefully follow the additional steps presented.

Step 4 — Content Rating
Content rating is divided into three sub-sections:

4A — Category
Enter an email address that will be used to contact you regarding your content rating. Note that this email may be shared with rating authorities and IARC.
Select your app category — if your app is not a game and not a social or communication application, choose: "All Other App Types."

4B — Questionnaire
Fill in the questionnaire with details specific to your application's content and functionality.

4C — Summary
Review all the details you have entered. This section displays a summary of your content rating selections.

Step 5 — Target Audience
This section contains multiple sub-sections. The required fields will vary depending on the target age groups you select.

5A: Target Age Groups — Select all applicable age ranges.
5B: App Details — Provide additional context about your application.
5C: Ads — Specify ad details relevant to your target audience.
5D: Store Presence — Define how your app appears in the store.
5E: Summary — Review all selections before saving.

Step 6 — Data Safety
Data Safety is one of the most important sections. It contains multiple sub-sections that must be completed according to your specific application's requirements.

💡 Tip: In the Data Collection section, read every option carefully before making a selection.


💡 Tip: In the OAuth checkbox section, provide a URL where users can request account deletion — a Google Form URL is acceptable for this purpose.


💡 Tip: In the Data Safety section, clearly specify every type of data you collect from users.


⚠️ Important: After completing the data clarification fields, you will only see a "Discard" button — do NOT click it. Instead, click the three-dot menu (⋮) next to that button, and from the pop-up, select "Save." Once saved, navigate back using the dashboard's back button.


Step 7 — Government Apps
Select "No" if your application is not a government application.

Step 8 — Financial Features
If your app provides financial features, select the appropriate option. Otherwise, scroll down and select "My app doesn't provide any financial feature," then click the "Next" button.

⚠️ Important: After completing this section, do NOT click "Discard." Click the three-dot menu (⋮) next to that button and choose "Save" from the pop-up. Then navigate back using the dashboard's back button. Once you return, a new section will open automatically requiring additional details such as Advertising ID and Health Apps settings. These options vary based on your previous selections.


💡 Tip: In the Advertising ID section, ensure that every available option is checked.


Step 9 — Health
If your app provides any health-related features or activities, select the relevant options. Otherwise, scroll down and select "My app does not have any health features."

Once all steps are completed, the back arrow button will be hidden. Click "All Apps" and re-select your application from the list.

Final Setup — Store Configuration
After completing all setup steps, the following sections will become available on your dashboard:

App Organization
Under "Manage How Your App Is Organized and Presented," select the appropriate category for your app. In the "Tags" section, choose relevant tags that best describe your application.

Store Settings
Enter your store listing contact details:
Email Address (this will be publicly visible on your Play Store listing)
Phone Number
Website URL

💡 Tip: Ensure the "External Marketing" checkbox is checked in your Store Settings.


Store Listing
Complete your full store listing with the following details:
App Name
Short Description
Long Description
App Icon — must be exactly 512 × 512 pixels
Feature Graphic — must be exactly 1,024 × 500 pixels
Promo Video — optionally add a YouTube video link
Phone Screenshots — upload a minimum of 6 to 8 screenshots of your application



Part 2: Release Your App

💡 Tip: Do not click "Test Your App" unless you specifically need to conduct beta testing with a large group of users.


Step 1 — Create and Publish a Release

1A — Select Countries and Regions
Click "Select Countries and Regions," add all desired countries and regions, then click the "Create New Release" button in the top-right corner.

1B — Upload Your AAB File
Upload your signed Android App Bundle (.aab) file.

1C — Release Name
The release name will be automatically populated once your AAB file has been successfully uploaded.

1D — Release Notes
Describe the new features and changes included in this release.

Click "Save" — a pop-up will appear asking: "Go to Publishing Overview?" Click "Go to Overview." After the progress check completes, click the "Send [X] Changes for Review" button in the top-right corner.



Part 3: Generating a Keystore File & Signed AAB

⚠️ Important: The keystore file is mandatory for generating a signed APK or AAB. Store this file securely — once your app is published to Google Play using a specific keystore, you must use the same file for every future update. Using a different keystore will permanently prevent you from updating your application.


Method 1 — Via Android Studio GUI (Recommended)

Step 1: Open Your Project
Open your React Native project's android folder in Android Studio.

Step 2: Navigate to Generate Signed Bundle
Go to: Build → Generate Signed Bundle / APK

Step 3: Select AAB Format
Select "Android App Bundle" and click "Next."

Step 4: Create a New Keystore
Click the "Create new..." button next to the "Key store path" field.

Step 5: Fill in Keystore Details
Complete all fields in the form as shown below:

Key store path:        /your-project/android/app/my-upload-key.keystore
Password:              your_strong_password
Confirm Password:      your_strong_password

── Key Section ──────────────────────────────────
Alias:                 my-key-alias
Password:              your_key_password
Confirm Password:      your_key_password
Validity (years):      25

── Certificate Section ──────────────────────────
First & Last Name:     John Doe
Organizational Unit:   Engineering
Organization:          Your Company Name
City:                  New York
State / Province:      NY
Country Code (XX):     US


Click OK → Next → Finish to generate your keystore and signed AAB file.



Method 2 — Via Terminal

Required File 1: Keystore File
If you do not already have a keystore, generate one using the following command:

keytool -genkey -v -keystore my-upload-key.keystore \
  -alias my-key-alias \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000


Place the generated file at:  android/app/my-upload-key.keystore

⚠️ Important: Never commit your keystore file to Git. Add it to your .gitignore file immediately.


Required File 2: gradle.properties — Add Signing Config
File location: android/gradle.properties

MYAPP_UPLOAD_STORE_FILE=my-upload-key.keystore
MYAPP_UPLOAD_KEY_ALIAS=my-key-alias
MYAPP_UPLOAD_STORE_PASSWORD=your_store_password
MYAPP_UPLOAD_KEY_PASSWORD=your_key_password


Required File 3: build.gradle — Reference the Signing Config
File location: android/app/build.gradle

android {
    ...
    signingConfigs {
        release {
            if (project.hasProperty('MYAPP_UPLOAD_STORE_FILE')) {
                storeFile file(MYAPP_UPLOAD_STORE_FILE)
                storePassword MYAPP_UPLOAD_STORE_PASSWORD
                keyAlias MYAPP_UPLOAD_KEY_ALIAS
                keyPassword MYAPP_UPLOAD_KEY_PASSWORD
            }
        }
    }
    buildTypes {
        release {
            signingConfig signingConfigs.release
            minifyEnabled enableProguardInReleaseBuilds
            proguardFiles getDefaultProguardFile("proguard-android.txt"),
                         "proguard-rules.pro"
        }
    }
}


Required File 4: google-services.json (Firebase only)
If your app uses Firebase, place the configuration file at: android/app/google-services.json
Download this file from your Firebase project console.

Generate the AAB File

cd android
./gradlew bundleRelease


Output location:
android/app/build/outputs/bundle/release/app-release.aab




Version Management
In android/app/build.gradle, increment the following values before each new release:

defaultConfig {
    applicationId  "com.yourapp"
    versionCode    2          // Increment by 1 for each release
    versionName    "1.1.0"    // Semantic version shown to users
}




Pre-Upload Checklist
Verify all items below before uploading your release to Google Play:

✓
Item
File / Location
☐
Keystore file
android/app/*.keystore
☐
Signing config
android/gradle.properties
☐
App version updated (versionCode & versionName)
android/app/build.gradle
☐
App icons (all required sizes)
android/app/src/main/res/
☐
App name set
android/app/src/main/res/values/strings.xml
☐
Permissions declared
AndroidManifest.xml
☐
google-services.json (Firebase only)
android/app/




Common Errors & Fixes

Error
Fix
Upload certificate mismatch
Use the same keystore file as previous releases.
versionCode already used
Increment the versionCode in build.gradle before rebuilding.
APK not signed
Verify the signingConfigs block in build.gradle is correct.
Missing permissions
Check and update AndroidManifest.xml with the required permissions.




Android Folder Structure

android/
├── app/
│   ├── build.gradle            ← signing configuration
│   ├── my-upload-key.keystore  ← your keystore file
│   ├── google-services.json    ← Firebase config (if applicable)
│   └── src/main/
│       ├── AndroidManifest.xml
│       └── res/                ← app icons & resources
└── gradle.properties           ← keystore credentials


⚠️ Important: The most common reason uploads fail is a missing or misconfigured keystore. Ensure that the credentials in gradle.properties exactly match what you used when generating the .keystore file, then rebuild your AAB using: ./gradlew bundleRelease


