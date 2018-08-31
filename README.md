# download-problem
I am attempting to isolate a [problem](https://github.com/michel-kraemer/gradle-download-task/issues/120) with the Gradle
download plugin. In a larger project I ran into a NoSuchFieldError with the stack trace below. This project does not
exhibit the same problem, yet.

```
Caused by: java.lang.NoSuchFieldError: INSTANCE
        at org.apache.http.conn.ssl.SSLConnectionSocketFactory.<clinit>(SSLConnectionSocketFactory.java:146)
        at org.apache.http.impl.client.HttpClientBuilder.build(HttpClientBuilder.java:964)
        at de.undercouch.gradle.tasks.download.internal.DefaultHttpClientFactory.createHttpClient(DefaultHttpClientFactory.java:86)
        at de.undercouch.gradle.tasks.download.internal.CachingHttpClientFactory.createHttpClient(CachingHttpClientFactory.java:43)
        at de.undercouch.gradle.tasks.download.DownloadAction.executeHttpProtocol(DownloadAction.java:247)
        at de.undercouch.gradle.tasks.download.DownloadAction.execute(DownloadAction.java:205)
        at de.undercouch.gradle.tasks.download.DownloadAction.execute(DownloadAction.java:157)
        at de.undercouch.gradle.tasks.download.Download.download(Download.java:90)
        at org.gradle.internal.reflect.JavaMethod.invoke(JavaMethod.java:73)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.doExecute(StandardTaskAction.java:46)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:39)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:26)
        at org.gradle.api.internal.AbstractTask$TaskActionWrapper.execute(AbstractTask.java:801)
        at org.gradle.api.internal.AbstractTask$TaskActionWrapper.execute(AbstractTask.java:768)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$1.run(ExecuteActionsTaskExecuter.java:131)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:300)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:292)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:174)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:90)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.run(DelegatingBuildOperationExecutor.java:31)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeAction(ExecuteActionsTaskExecuter.java:120)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeActions(ExecuteActionsTaskExecuter.java:99)
        ... 31 more
```
