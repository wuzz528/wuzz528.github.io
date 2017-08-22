## List supported script engines  
{% highlight java linenos=table %}
ScriptEngineManager manager = new ScriptEngineManager();
for(ScriptEngineFactory factory : manager.getEngineFactories()){
    System.out.printf("Name: %s%n" +
                    "\tVersion: %s%n" +
                    "\tLanguage name: %s%n" +
                    "\tLanguage version: %s%n" +
                    "\tExtensions: %s%n" +
                    "\tMime types: %s%n" +
                    "\tNames: %s%n",
            factory.getEngineName(),
            factory.getEngineVersion(),
            factory.getLanguageName(),
            factory.getLanguageVersion(),
            factory.getExtensions(),
            factory.getMimeTypes(),
            factory.getNames());
}
{% endhighlight %}  
## Invoke script functions  
{% highlight java linenos=table %}
ScriptEngine jsEngine = manager.getEngineByExtension("js");
// put binding context
jsEngine.put("url", "username=a&category=a book");
try{
    Object result = jsEngine.eval("encodeURI(url)");
    System.out.println(result);
}catch (ScriptException e){
    e.printStackTrace();
}
{% endhighlight %}
