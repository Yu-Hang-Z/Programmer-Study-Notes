
# Quartz 快速上手示例

## 1. 简介

Quartz 是一个开源的作业调度框架，可以用来调度作业执行。它可以与 J2EE 和 J2SE 应用程序一起使用。Quartz 可以与 JTA 事务一起使用，也可以与 JMS 一起使用。

## 2. Quartz 的基本概念

### 2.1 作业（Job）

作业是 Quartz 中的基本执行单元。它是一个实现了 Job 接口的类，其中定义了要执行的任务。

### 2.2 触发器（Trigger）

触发器是用来触发作业执行的。它定义了作业执行的时间规则。

### 2.3 调度器（Scheduler）

调度器是 Quartz 的核心组件，它用来调度作业的执行。调度器可以启动、暂停、恢复和停止作业的执行。

## 3. Quartz 的使用

### 3.1 添加 Quartz 依赖

在 Maven 项目中，可以通过添加以下依赖来使用 Quartz：

<dependency>

    <groupId>org.quartz-scheduler</groupId>

    <artifactId>quartz</artifactId>

    <version>2.3.2</version>

</dependency>

  

### 3.2 编写作业类

在 Quartz 中，需要编写一个实现了 Job 接口的类来定义要执行的任务。例如：

public class MyJob implements Job {

    public void execute(JobExecutionContext context) throws JobExecutionException {

        System.out.println("Hello Quartz!");

    }

}

  

### 3.3 编写触发器类

在 Quartz 中，需要编写一个触发器类来定义作业执行的时间规则。例如：

public class MyTrigger {

    public Trigger getTrigger() {

        return TriggerBuilder.newTrigger()

                .withIdentity("myTrigger", "group1")

                .withSchedule(CronScheduleBuilder.cronSchedule("0/5 * * * * ?"))

                .build();
