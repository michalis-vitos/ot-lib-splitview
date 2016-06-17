# ot-lib-splitview
Let a user resize a pair of adjacent views

## main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<com.fsck.splitview.SplitView 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:splitview="http://schemas.android.com/apk/res/com.fsck.example.splitview"
    android:id="@+id/split_view"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    splitview:handle="@+id/handle"
    splitview:primaryContent="@+id/primary"
    splitview:secondaryContent="@+id/secondary"
    >

    <LinearLayout
        android:id="@+id/primary"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
    android:orientation="vertical">
    <Button android:id="@+id/maximize_secondary" android:text="maximize secondary"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
        />
    <Button android:id="@+id/maximize_primary" android:text="minimize secondary" 
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
        />
    <Button android:id="@+id/halves" android:text="resize"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
        />
    <TextView  
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
    android:text="Hello World, ACTIVITY_ENTRY_NAME"
    />
</LinearLayout>
    <ImageView 
        android:id="@+id/handle"
        android:layout_width="fill_parent" 
        android:layout_height="20dip"
        android:background="@drawable/shade_handlebar"
    />
<com.fsck.splitview.SplitView 
    android:id="@+id/secondary"
        android:orientation="horizontal"
    android:layout_width="fill_parent"
    android:layout_height="0dip"
    android:layout_weight="1"
    splitview:handle="@+id/inner_handle"
    splitview:primaryContent="@+id/inner_primary"
    splitview:secondaryContent="@+id/inner_secondary"
    >
    <TextView
        android:id="@+id/inner_primary"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_weight="1" 
    android:text="Hello World, ACTIVITY_ENTRY_NAME"/>
    
    <ImageView 
        android:id="@+id/inner_handle"
        android:layout_height="fill_parent" 
        android:layout_width="20dip"
        android:background="@drawable/shade_handlebar_vertical"/>
    <TextView
    android:id="@+id/inner_secondary"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" 
    android:layout_weight="1"
    android:text="Hello World, ACTIVITY_ENTRY_NAME"
    />
    </com.fsck.splitview.SplitView>
</com.fsck.splitview.SplitView>
```

## Activity
``` java
public class Home extends Activity
{
    private Button mHalves;
    private Button mMaximizePrimaryContent;
    private Button mMaximizeSecondaryContent;

    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);

        mMaximizePrimaryContent = (Button)findViewById(R.id.maximize_primary);  
        mMaximizePrimaryContent.setOnClickListener( new OnClickListener() {
            @Override public void onClick(View v) {
                ((SplitView)findViewById(R.id.split_view)).maximizePrimaryContent();
            }

        });

        mMaximizeSecondaryContent = (Button)findViewById(R.id.maximize_secondary);  
        mMaximizeSecondaryContent.setOnClickListener( new OnClickListener() {
            @Override public void onClick(View v) {
                ((SplitView)findViewById(R.id.split_view)).maximizeSecondaryContent();
            }

        });

        mHalves = (Button)findViewById(R.id.halves);
        mHalves.setOnClickListener( new OnClickListener() {
            @Override public void onClick(View v) {
                ((SplitView)findViewById(R.id.split_view)).setPrimaryContentSize(200);
            }

        });


    }
}

```


