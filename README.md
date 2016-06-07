##How to know Android home screen wiget size##

Take AppWidgetSizeUtils.java

Code works on JellyBean(v16) and higher. To support older versions read: http://stackoverflow.com/questions/17396045/how-to-catch-widget-size-changes-on-devices-where-onappwidgetoptionschanged-not or http://stackoverflow.com/questions/6984834/how-to-get-app-widget-size

##Using##

```java
public class AppWidgetSizeTest extends AppWidgetProvider {
    public void onUpdate(Context context, AppWidgetManager appWidgetManager, int[] appWidgetIds) {
        for (int id : appWidgetIds) {
            Point sizeInDIP    = AppWidgetSizeUtils.getSizeInDIP(appWidgetManager, id);
            Point sizeInPixels = AppWidgetSizeUtils.getSizeInPixels(appWidgetManager, id);
    
            Log.i("AppWidgetSizeTest", "onUpdate ID: " + id + " Size: " + sizeInDIP.x    + "x" + sizeInDIP.y    + " dip");
            Log.i("AppWidgetSizeTest", "onUpdate ID: " + id + " Size: " + sizeInPixels.x + "x" + sizeInPixels.y + " px");
        }
    }
    
    public void onAppWidgetOptionsChanged(Context context, AppWidgetManager appWidgetManager, int appWidgetId, Bundle newOptions) {
        Point sizeInDIP    = AppWidgetSizeUtils.getSizeInDIP(newOptions);
        Point sizeInPixels = AppWidgetSizeUtils.getSizeInPixels(newOptions);
    
        Log.i("AppWidgetSizeTest", "onAppWidgetOptionsChanged ID: " + appWidgetId + " Size: " + sizeInDIP.x    + "x" + sizeInDIP.y    + " dip");
        Log.i("AppWidgetSizeTest", "onAppWidgetOptionsChanged ID: " + appWidgetId + " Size: " + sizeInPixels.x + "x" + sizeInPixels.y + " px");
    }
}
```
