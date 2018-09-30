# 修复android.os.NetworkOnMainThreadException？
[How do I fix android.os.NetworkOnMainThreadException?](https://stackoverflow.com/questions/6343166/how-do-i-fix-android-os-networkonmainthreadexception)

```
URL url = new URL(urlToRssFeed);
SAXParserFactory factory = SAXParserFactory.newInstance();
SAXParser parser = factory.newSAXParser();
XMLReader xmlreader = parser.getXMLReader();
RssHandler theRSSHandler = new RssHandler();
xmlreader.setContentHandler(theRSSHandler);
InputSource is = new InputSource(url.openStream());
xmlreader.parse(is);
return theRSSHandler.getFeed();
```

会有一个错误

```java
android.os.NetworkOnMainThreadException
```

___



> 1

这个Exception会在APP试图在主线程做一个网络操作的时候报出来，你需要使用[`AsyncTask`](http://developer.android.com/reference/android/os/AsyncTask.html)来异步执行你的代码

```java
class RetrieveFeedTask extends AsyncTask<String, Void, RSSFeed> {

    private Exception exception;

    protected RSSFeed doInBackground(String... urls) {
        try {
            URL url = new URL(urls[0]);
            SAXParserFactory factory = SAXParserFactory.newInstance();
            SAXParser parser = factory.newSAXParser();
            XMLReader xmlreader = parser.getXMLReader();
            RssHandler theRSSHandler = new RssHandler();
            xmlreader.setContentHandler(theRSSHandler);
            InputSource is = new InputSource(url.openStream());
            xmlreader.parse(is);

            return theRSSHandler.getFeed();
        } catch (Exception e) {
            this.exception = e;

            return null;
        } finally {
            is.close();
        }
    }

    protected void onPostExecute(RSSFeed feed) {
        // TODO: check this.exception
        // TODO: do something with the feed
    }
}
```

这样执行任务:

```java
new RetrieveFeedTask().execute(urlToRssFeed);
```

不要忘了在AndroidManifest.xml文件里添加

```java
<uses-permission android:name="android.permission.INTERNET"/>
```

> 2

使用一个新的Thread:

```java
Thread thread = new Thread(new Runnable() {

    @Override
    public void run() {
        try  {
            //Your code goes here
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
});

thread.start(); 
```