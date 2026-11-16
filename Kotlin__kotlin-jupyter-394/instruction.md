# Issue

**Title:** mybinder: Update to Java 11

## Description

The Kotlin kernel currently fails when this repo is launched on mybinder.org:
```
...
Listening for transport dt_socket at address: 1044
Exception in thread "main" java.lang.UnsupportedClassVersionError: ch/qos/logback/classic/spi/LogbackServiceProvider has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:756)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:473)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:74)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:369)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:363)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:362)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:418)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:352)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:351)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:348)
	at java.util.ServiceLoader$LazyIterator.nextService(ServiceLoader.java:370)
	at java.util.ServiceLoader$LazyIterator.next(ServiceLoader.java:404)
	at java.util.ServiceLoader$1.next(ServiceLoader.java:480)
	at org.slf4j.LoggerFactory.safelyInstantiate(LoggerFactory.java:134)
	at org.slf4j.LoggerFactory.findServiceProviders(LoggerFactory.java:115)
	at org.slf4j.LoggerFactory.bind(LoggerFactory.java:178)
	at org.slf4j.LoggerFactory.performInitialization(LoggerFactory.java:170)
	at org.slf4j.LoggerFactory.getProvider(LoggerFactory.java:453)
	at org.slf4j.LoggerFactory.getILoggerFactory(LoggerFactory.java:439)
	at org.slf4j.LoggerFactory.getLogger(LoggerFactory.java:388)
	at org.jetbrains.kotlinx.jupyter.config.LoggingKt.getLogger(logging.kt:9)
	at org.jetbrains.kotlinx.jupyter.config.LoggingKt.getLogger$default(logging.kt:9)
	at org.jetbrains.kotlinx.jupyter.ConfigKt$log$2.invoke(config.kt:16)
	at org.jetbrains.kotlinx.jupyter.ConfigKt$log$2.invoke(config.kt:16)
	at kotlin.SynchronizedLazyImpl.getValue(LazyJVM.kt:74)
	at org.jetbrains.kotlinx.jupyter.ConfigKt.getLog(config.kt:16)
	at org.jetbrains.kotlinx.jupyter.IkotlinKt.main(ikotlin.kt:70)
[I 22:17:27.776 NotebookApp] KernelRestarter: restarting kernel (1/5), new random ports
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc11c663744e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.