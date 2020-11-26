# Android-URL-Schemes
open android app from url and intent

## Requirements

###### Accept Application

1 - Add intent-filter to Manifest

```
<intent-filter
                android:autoVerify="true"
                android:label="@string/app_name">
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data
                    android:host="www.example.com"
                    android:scheme="http" />
                <data android:scheme="https" />
            </intent-filter>
```

2 - add Permissions to Manifest

```
<uses-permission android:name="android.permission.INTERNET" />

```

###### Use Intent Application

1 - add Permissions to Manifest

```
<uses-permission android:name="android.permission.INTERNET" />

```

## Usage

###### Accept Application

1. default
```
@Override
public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.main);

    Intent intent = getIntent();
    String action = intent.getAction();
    Uri data = intent.getData();
}
```
2. if accept application is your app.

```
        Intent intent=getIntent();
        if(intent!=null && intent.getData()!=null){

            String link=intent.getStringExtra("link");/// you get "www.facebook.com"
            String name=intent.getStringExtra("name");/// you get "My name is ..."

            Intent mainIntent = new Intent(MainActivity.this, UseGetIntentDataActivity.class);
            startActivity(mainIntent);
            finish();
        }else {
            
             Intent mainIntent = new Intent(MainActivity.this, OtherActivity.class);
             startActivity(mainIntent);
             finish();
           
        }
```


###### Use Intent Application

1. default

```
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https:\\www.example.com\sample"));
startActivity(intent);
```

2. if intent application is your app.

```
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https:\\www.example.com\sample"));
/// You can use as much putExtra as you need
intent.putExtra("link","www.facebook.com");
intent.putExtra("name","My name is ...");
startActivity(intent);
```

