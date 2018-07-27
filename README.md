Idea Plugin Simulate Key Pressing
=================================

Two way to simulate key pressing:

1. when `x` is pressed, it will be ignored and simulated `s` will be sent 5 times, using `Toolkit.getDefaultToolkit().systemEventQueue.postEvent(createKeyEvent(event))`
2. when `y` is pressed, it will be ignored and simulated `c` will be sent 10 times(it should be `5`), using `Robot.keyPressing`

The 2nd way has issues, can't fix it now.

Update:

The issue of 2 is (almost) fixed. The reason if when you press a key, it actually triggered 3 events:

1. `KEY_PRESSED`
2. `KEY_TYPED`
3. `KEY_RELEASED`

So if we use `Robot.keyPress/keyRelease` for each event, it will trigger more than expected.

But, why it's 10 times, not 15? Figure it next time.

Run plugin in IDEA
------------------

```
./gradlew runIde
```

Create any file, and type something into it, including char `x` and `y`, you will see something strange.

Build the plugin to a zip
-------------------------

```
./gradlew buildPlugin
```

It will generate the plugin file in `./build/distributions`

Notice
-------

- Use `version 'IC-2018.1.5'` every time to reduce download. (about 500M)
- Don't forget to change `id` and `name` in `resources/META-INF/plugin.xml` to current project