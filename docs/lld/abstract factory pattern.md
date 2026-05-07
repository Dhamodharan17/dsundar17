# Abstract Factory Example - Cloud Provider System

## Problem

We support multiple cloud providers.

Each provider needs its own:

- Storage
- Queue
- Logger

But client code should remain provider-independent.

---

# Product Interfaces

```java
interface Storage {
    void upload();
}

interface Queue {
    void send();
}

interface Logger {
    void log();
}


---

AWS Implementations

class S3Storage implements Storage {
    public void upload() {
        System.out.println("Uploading to S3");
    }
}

class SQSQueue implements Queue {
    public void send() {
        System.out.println("Sending via SQS");
    }
}

class CloudWatchLogger implements Logger {
    public void log() {
        System.out.println("Logging to CloudWatch");
    }
}


---

GCP Implementations

class GCSStorage implements Storage {
    public void upload() {
        System.out.println("Uploading to GCS");
    }
}

class PubSubQueue implements Queue {
    public void send() {
        System.out.println("Sending via PubSub");
    }
}

class StackDriverLogger implements Logger {
    public void log() {
        System.out.println("Logging to StackDriver");
    }
}


---

Abstract Factory

interface CloudFactory {
    Storage createStorage();
    Queue createQueue();
    Logger createLogger();
}


---

AWS Factory

class AWSFactory implements CloudFactory {

    public Storage createStorage() {
        return new S3Storage();
    }

    public Queue createQueue() {
        return new SQSQueue();
    }

    public Logger createLogger() {
        return new CloudWatchLogger();
    }
}


---

GCP Factory

class GCPFactory implements CloudFactory {

    public Storage createStorage() {
        return new GCSStorage();
    }

    public Queue createQueue() {
        return new PubSubQueue();
    }

    public Logger createLogger() {
        return new StackDriverLogger();
    }
}


---

Client Code

class Application {

    private Storage storage;
    private Queue queue;
    private Logger logger;

    public Application(CloudFactory factory) {
        storage = factory.createStorage();
        queue = factory.createQueue();
        logger = factory.createLogger();
    }

    public void run() {
        storage.upload();
        queue.send();
        logger.log();
    }
}


---

Usage

CloudFactory factory = new AWSFactory();

Application app = new Application(factory);

app.run();


---

Why Abstract Factory Here?

All providers create same product categories:

Storage

Queue

Logger


But implementations belong to different ecosystems:

AWS	GCP

S3Storage	GCSStorage
SQSQueue	PubSubQueue
CloudWatchLogger	StackDriverLogger


This keeps provider families consistent and client code clean.