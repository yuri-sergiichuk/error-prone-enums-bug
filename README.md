Error-prone compilation bug companion repo
----------

How to reproduce the bug.

1. Run `./gradlew clean build`.
2. The compilation fails with the following stacktrace:

```
error-prone-bug\src\main\java\com\acme\FloggerToStringFailure.java:10: error: An unhandled exception was thrown by the Error Prone static analysis plugin.
        logger.atInfo().log("This is formatted with toString() %s value", toString());
                           ^
     Please report this at https://github.com/google/error-prone/issues/new and include the following:
  
     error-prone version: 2.7.1
     BugPattern: FloggerArgumentToString
     Stack Trace:
     java.lang.NullPointerException
  	at java.base/java.util.Objects.requireNonNull(Objects.java:221)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString$Parameter.<init>(FloggerArgumentToString.java:113)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString$Parameter.<init>(FloggerArgumentToString.java:102)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString$Unwrapper$1.unwrap(FloggerArgumentToString.java:124)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString.unwrap(FloggerArgumentToString.java:349)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString.unwrapArguments(FloggerArgumentToString.java:322)
  	at com.google.errorprone.bugpatterns.flogger.FloggerArgumentToString.matchMethodInvocation(FloggerArgumentToString.java:291)
  	at com.google.errorprone.scanner.ErrorProneScanner.processMatchers(ErrorProneScanner.java:450)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitMethodInvocation(ErrorProneScanner.java:747)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitMethodInvocation(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCMethodInvocation.accept(JCTree.java:1650)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:82)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:74)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:48)
  	at jdk.compiler/com.sun.source.util.TreeScanner.visitExpressionStatement(TreeScanner.java:433)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitExpressionStatement(ErrorProneScanner.java:634)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitExpressionStatement(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCExpressionStatement.accept(JCTree.java:1460)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:82)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:74)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:48)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scan(TreeScanner.java:105)
  	at jdk.compiler/com.sun.source.util.TreeScanner.visitBlock(TreeScanner.java:248)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitBlock(ErrorProneScanner.java:521)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitBlock(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCBlock.accept(JCTree.java:1032)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:82)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:74)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:48)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scanAndReduce(TreeScanner.java:90)
  	at jdk.compiler/com.sun.source.util.TreeScanner.visitMethod(TreeScanner.java:206)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitMethod(ErrorProneScanner.java:741)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitMethod(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCMethodDecl.accept(JCTree.java:898)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:82)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:74)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:48)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scanAndReduce(TreeScanner.java:90)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scan(TreeScanner.java:105)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scanAndReduce(TreeScanner.java:113)
  	at jdk.compiler/com.sun.source.util.TreeScanner.visitClass(TreeScanner.java:187)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitClass(ErrorProneScanner.java:549)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitClass(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCClassDecl.accept(JCTree.java:808)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:82)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:74)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:48)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scan(TreeScanner.java:105)
  	at jdk.compiler/com.sun.source.util.TreeScanner.scanAndReduce(TreeScanner.java:113)
  	at jdk.compiler/com.sun.source.util.TreeScanner.visitCompilationUnit(TreeScanner.java:144)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitCompilationUnit(ErrorProneScanner.java:561)
  	at com.google.errorprone.scanner.ErrorProneScanner.visitCompilationUnit(ErrorProneScanner.java:151)
  	at jdk.compiler/com.sun.tools.javac.tree.JCTree$JCCompilationUnit.accept(JCTree.java:591)
  	at jdk.compiler/com.sun.source.util.TreePathScanner.scan(TreePathScanner.java:56)
  	at com.google.errorprone.scanner.Scanner.scan(Scanner.java:58)
  	at com.google.errorprone.scanner.ErrorProneScannerTransformer.apply(ErrorProneScannerTransformer.java:43)
  	at com.google.errorprone.ErrorProneAnalyzer.finished(ErrorProneAnalyzer.java:152)
  	at jdk.compiler/com.sun.tools.javac.api.MultiTaskListener.finished(MultiTaskListener.java:132)
  	at jdk.compiler/com.sun.tools.javac.main.JavaCompiler.flow(JavaCompiler.java:1418)
  	at jdk.compiler/com.sun.tools.javac.main.JavaCompiler.flow(JavaCompiler.java:1365)
  	at jdk.compiler/com.sun.tools.javac.main.JavaCompiler.compile(JavaCompiler.java:960)
  	at jdk.compiler/com.sun.tools.javac.api.JavacTaskImpl.lambda$doCall$0(JavacTaskImpl.java:104)
  	at jdk.compiler/com.sun.tools.javac.api.JavacTaskImpl.handleExceptions(JavacTaskImpl.java:147)
  	at jdk.compiler/com.sun.tools.javac.api.JavacTaskImpl.doCall(JavacTaskImpl.java:100)
  	at jdk.compiler/com.sun.tools.javac.api.JavacTaskImpl.call(JavacTaskImpl.java:94)
  	at org.gradle.internal.compiler.java.IncrementalCompileTask.call(IncrementalCompileTask.java:77)
  	at org.gradle.api.internal.tasks.compile.AnnotationProcessingCompileTask.call(AnnotationProcessingCompileTask.java:94)
  	at org.gradle.api.internal.tasks.compile.ResourceCleaningCompilationTask.call(ResourceCleaningCompilationTask.java:57)
  	at org.gradle.api.internal.tasks.compile.JdkJavaCompiler.execute(JdkJavaCompiler.java:55)
  	at org.gradle.api.internal.tasks.compile.JdkJavaCompiler.execute(JdkJavaCompiler.java:40)
  	at org.gradle.api.internal.tasks.compile.NormalizingJavaCompiler.delegateAndHandleErrors(NormalizingJavaCompiler.java:97)
  	at org.gradle.api.internal.tasks.compile.NormalizingJavaCompiler.execute(NormalizingJavaCompiler.java:51)
  	at org.gradle.api.internal.tasks.compile.NormalizingJavaCompiler.execute(NormalizingJavaCompiler.java:37)
  	at org.gradle.api.internal.tasks.compile.AnnotationProcessorDiscoveringCompiler.execute(AnnotationProcessorDiscoveringCompiler.java:51)
  	at org.gradle.api.internal.tasks.compile.AnnotationProcessorDiscoveringCompiler.execute(AnnotationProcessorDiscoveringCompiler.java:37)
  	at org.gradle.api.internal.tasks.compile.ModuleApplicationNameWritingCompiler.execute(ModuleApplicationNameWritingCompiler.java:46)
  	at org.gradle.api.internal.tasks.compile.ModuleApplicationNameWritingCompiler.execute(ModuleApplicationNameWritingCompiler.java:36)
  	at org.gradle.api.internal.tasks.compile.CleaningJavaCompiler.execute(CleaningJavaCompiler.java:53)
  	at org.gradle.api.internal.tasks.compile.incremental.IncrementalCompilerFactory.lambda$createRebuildAllCompiler$0(IncrementalCompilerFactory.java:98)
  	at org.gradle.api.internal.tasks.compile.incremental.IncrementalResultStoringCompiler.execute(IncrementalResultStoringCompiler.java:61)
  	at org.gradle.api.internal.tasks.compile.incremental.IncrementalResultStoringCompiler.execute(IncrementalResultStoringCompiler.java:45)
  	at org.gradle.api.internal.tasks.compile.CompileJavaBuildOperationReportingCompiler$2.call(CompileJavaBuildOperationReportingCompiler.java:59)
  	at org.gradle.api.internal.tasks.compile.CompileJavaBuildOperationReportingCompiler$2.call(CompileJavaBuildOperationReportingCompiler.java:51)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.api.internal.tasks.compile.CompileJavaBuildOperationReportingCompiler.execute(CompileJavaBuildOperationReportingCompiler.java:51)
  	at org.gradle.api.tasks.compile.JavaCompile.performCompilation(JavaCompile.java:345)
  	at org.gradle.api.tasks.compile.JavaCompile.performIncrementalCompilation(JavaCompile.java:239)
  	at org.gradle.api.tasks.compile.JavaCompile.compile(JavaCompile.java:211)
  	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
  	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
  	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
  	at java.base/java.lang.reflect.Method.invoke(Method.java:566)
  	at org.gradle.internal.reflect.JavaMethod.invoke(JavaMethod.java:104)
  	at org.gradle.api.internal.project.taskfactory.IncrementalInputsTaskAction.doExecute(IncrementalInputsTaskAction.java:32)
  	at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:51)
  	at org.gradle.api.internal.project.taskfactory.AbstractIncrementalTaskAction.execute(AbstractIncrementalTaskAction.java:25)
  	at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:29)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$2.run(ExecuteActionsTaskExecuter.java:494)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$1.execute(DefaultBuildOperationRunner.java:29)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$1.execute(DefaultBuildOperationRunner.java:26)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.run(DefaultBuildOperationRunner.java:56)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$run$1(DefaultBuildOperationExecutor.java:71)
  	at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.runWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:45)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:71)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeAction(ExecuteActionsTaskExecuter.java:479)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeActions(ExecuteActionsTaskExecuter.java:462)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.access$400(ExecuteActionsTaskExecuter.java:105)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.executeWithPreviousOutputFiles(ExecuteActionsTaskExecuter.java:273)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution.execute(ExecuteActionsTaskExecuter.java:251)
  	at org.gradle.internal.execution.steps.ExecuteStep.lambda$executeOperation$0(ExecuteStep.java:65)
  	at java.base/java.util.Optional.map(Optional.java:265)
  	at org.gradle.internal.execution.steps.ExecuteStep.executeOperation(ExecuteStep.java:65)
  	at org.gradle.internal.execution.steps.ExecuteStep.access$000(ExecuteStep.java:34)
  	at org.gradle.internal.execution.steps.ExecuteStep$1.call(ExecuteStep.java:47)
  	at org.gradle.internal.execution.steps.ExecuteStep$1.call(ExecuteStep.java:44)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:44)
  	at org.gradle.internal.execution.steps.ExecuteStep.execute(ExecuteStep.java:34)
  	at org.gradle.internal.execution.steps.RemovePreviousOutputsStep.execute(RemovePreviousOutputsStep.java:72)
  	at org.gradle.internal.execution.steps.RemovePreviousOutputsStep.execute(RemovePreviousOutputsStep.java:42)
  	at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:53)
  	at org.gradle.internal.execution.steps.ResolveInputChangesStep.execute(ResolveInputChangesStep.java:39)
  	at org.gradle.internal.execution.steps.CancelExecutionStep.execute(CancelExecutionStep.java:44)
  	at org.gradle.internal.execution.steps.TimeoutStep.executeWithoutTimeout(TimeoutStep.java:77)
  	at org.gradle.internal.execution.steps.TimeoutStep.execute(TimeoutStep.java:58)
  	at org.gradle.internal.execution.steps.CreateOutputsStep.execute(CreateOutputsStep.java:54)
  	at org.gradle.internal.execution.steps.CreateOutputsStep.execute(CreateOutputsStep.java:32)
  	at org.gradle.internal.execution.steps.CaptureStateAfterExecutionStep.execute(CaptureStateAfterExecutionStep.java:57)
  	at org.gradle.internal.execution.steps.CaptureStateAfterExecutionStep.execute(CaptureStateAfterExecutionStep.java:38)
  	at org.gradle.internal.execution.steps.BroadcastChangingOutputsStep.execute(BroadcastChangingOutputsStep.java:63)
  	at org.gradle.internal.execution.steps.BroadcastChangingOutputsStep.execute(BroadcastChangingOutputsStep.java:30)
  	at org.gradle.internal.execution.steps.BuildCacheStep.executeWithoutCache(BuildCacheStep.java:176)
  	at org.gradle.internal.execution.steps.BuildCacheStep.execute(BuildCacheStep.java:76)
  	at org.gradle.internal.execution.steps.BuildCacheStep.execute(BuildCacheStep.java:47)
  	at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:43)
  	at org.gradle.internal.execution.steps.StoreExecutionStateStep.execute(StoreExecutionStateStep.java:32)
  	at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:39)
  	at org.gradle.internal.execution.steps.RecordOutputsStep.execute(RecordOutputsStep.java:25)
  	at org.gradle.internal.execution.steps.SkipUpToDateStep.executeBecause(SkipUpToDateStep.java:102)
  	at org.gradle.internal.execution.steps.SkipUpToDateStep.lambda$execute$0(SkipUpToDateStep.java:95)
  	at java.base/java.util.Optional.map(Optional.java:265)
  	at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:55)
  	at org.gradle.internal.execution.steps.SkipUpToDateStep.execute(SkipUpToDateStep.java:39)
  	at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:83)
  	at org.gradle.internal.execution.steps.ResolveChangesStep.execute(ResolveChangesStep.java:44)
  	at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:37)
  	at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsFinishedStep.execute(MarkSnapshottingInputsFinishedStep.java:27)
  	at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:96)
  	at org.gradle.internal.execution.steps.ResolveCachingStateStep.execute(ResolveCachingStateStep.java:52)
  	at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:83)
  	at org.gradle.internal.execution.steps.CaptureStateBeforeExecutionStep.execute(CaptureStateBeforeExecutionStep.java:54)
  	at org.gradle.internal.execution.steps.ValidateStep.execute(ValidateStep.java:74)
  	at org.gradle.internal.execution.steps.SkipEmptyWorkStep.lambda$execute$2(SkipEmptyWorkStep.java:88)
  	at java.base/java.util.Optional.orElseGet(Optional.java:369)
  	at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:88)
  	at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:34)
  	at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsStartedStep.execute(MarkSnapshottingInputsStartedStep.java:38)
  	at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:46)
  	at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:34)
  	at org.gradle.internal.execution.steps.AssignWorkspaceStep.lambda$execute$0(AssignWorkspaceStep.java:43)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter$TaskExecution$3.withWorkspace(ExecuteActionsTaskExecuter.java:286)
  	at org.gradle.internal.execution.steps.AssignWorkspaceStep.execute(AssignWorkspaceStep.java:43)
  	at org.gradle.internal.execution.steps.AssignWorkspaceStep.execute(AssignWorkspaceStep.java:33)
  	at org.gradle.internal.execution.steps.IdentityCacheStep.execute(IdentityCacheStep.java:40)
  	at org.gradle.internal.execution.steps.IdentityCacheStep.execute(IdentityCacheStep.java:30)
  	at org.gradle.internal.execution.steps.IdentifyStep.execute(IdentifyStep.java:54)
  	at org.gradle.internal.execution.steps.IdentifyStep.execute(IdentifyStep.java:40)
  	at org.gradle.internal.execution.impl.DefaultExecutionEngine.execute(DefaultExecutionEngine.java:41)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.lambda$executeIfValid$1(ExecuteActionsTaskExecuter.java:183)
  	at java.base/java.util.Optional.orElseGet(Optional.java:369)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:183)
  	at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:173)
  	at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:109)
  	at org.gradle.api.internal.tasks.execution.FinalizePropertiesTaskExecuter.execute(FinalizePropertiesTaskExecuter.java:46)
  	at org.gradle.api.internal.tasks.execution.ResolveTaskExecutionModeExecuter.execute(ResolveTaskExecutionModeExecuter.java:62)
  	at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:57)
  	at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:56)
  	at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:36)
  	at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.executeTask(EventFiringTaskExecuter.java:77)
  	at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:55)
  	at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:52)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:200)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$CallableBuildOperationWorker.execute(DefaultBuildOperationRunner.java:195)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:75)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner$3.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:153)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.execute(DefaultBuildOperationRunner.java:68)
  	at org.gradle.internal.operations.DefaultBuildOperationRunner.call(DefaultBuildOperationRunner.java:62)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.lambda$call$2(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.internal.operations.UnmanagedBuildOperationWrapper.callWithUnmanagedSupport(UnmanagedBuildOperationWrapper.java:54)
  	at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:76)
  	at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter.execute(EventFiringTaskExecuter.java:52)
  	at org.gradle.execution.plan.LocalTaskNodeExecutor.execute(LocalTaskNodeExecutor.java:41)
  	at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:411)
  	at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:398)
  	at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:391)
  	at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:377)
  	at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.lambda$run$0(DefaultPlanExecutor.java:127)
  	at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.execute(DefaultPlanExecutor.java:191)
  	at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.executeNextNode(DefaultPlanExecutor.java:182)
  	at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.run(DefaultPlanExecutor.java:124)
  	at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
  	at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
  	at java.base/java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1128)
  	at java.base/java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
  	at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
```

## Env

JDK: 11-13
OS: any OS
