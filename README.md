# ActivityStack    
这个项目有什么用呢？其实没什么用，但其实也很有用。主要是一些跟具体项目无关的工具类。

## BlockUtils
一个通过Looper.setMessageLogging来监听HandlerMessage消息实现的监控主线程是否出现卡顿的工具
<pre><code>BlockUtils.getInstance().install();</code></pre>

## ReflectUtils
一个反射工具类，可以类似写脚本一样反射java属性和方法。
<pre><code>ReflectUtils.reflect(application, "mLoadedApk.mActivityThread.mActivities");</code></pre>
<pre><code>ReflectUtils.reflect(application, "mModel.getName().toString()");</code></pre>
<pre><code>ReflectUtils.reflect(application, "mModel.setName(%1)", new Object[]{"new_name"});</code></pre>
<pre><code>ReflectUtils.reflect(null, "android.app.ActivityThread#currentApplication()");</code></pre>

## ApplicationUtils
用ReflectUtils反射获取当前App的所有处于Activity栈中的Activity的引用。
<pre><code>ApplicationUtils.getTopActivity();</code></pre>
<pre><code>ApplicationUtils.getActivities();</code></pre>

## LifecycleUtils
打印Activity和Fragment生命周期的工具，利用了系统Api，对Activity和Fragment是0侵入。如果项目非常大了，一些界面很可能不是自己维护的，要找到某个界面对应的类，看源码可能效率不是很高，可以用这个类非常简单快速的定位界面对应的类。
<pre><code>new LifecycleUtils(this).register();</code></pre>

## ShakeManager
这个是从Facebook的ReactNative中偷过来的。ReactNative里可以通过摇一摇手机然后弹一个弹窗辅助开发。比如某个界面需要手动输入的东西非常多。这时候可以写一个自动填充的代码，然后通过摇一摇弹出菜单，点击调用代码。
<pre><code>new ShakeManager(this).registerShakeDetector();</code></pre>
