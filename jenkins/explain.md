# **Declarative** and **Scripted Pipelines** 

<br><br>

## What is a Jenkins Pipeline?

A **pipeline** is a set of steps Jenkins follows to:

1. Get code
2. Build it
3. Test it
4. Deploy it

Think of it like a **recipe** Jenkins follows.

---

## Declarative Pipeline (Simple & Structured)

### In lemon language 🍋

Declarative pipeline is like:

> “Follow these rules. Don’t think too much.”

You **tell Jenkins what you want**, and Jenkins decides **how** to do it.

---

### Key ideas

* Easy to read
* Fixed structure
* Less flexible, but safer
* Best for beginners

---

### Example

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }
}
```

### What this means

* `pipeline` → start of pipeline
* `agent any` → run on any machine
* `stages` → steps of the recipe
* `steps` → what to do

👉 Jenkins **forces rules**, so you make fewer mistakes.

---

## Scripted Pipeline (Powerful & Flexible)

### In lemon language 🍋

Scripted pipeline is like:

> “Do whatever you want, however you want.”

You **write full logic** using Groovy code.

---

### Key ideas

* Very flexible
* More powerful
* Harder to read
* Easy to make mistakes
* Best for advanced users

---

### Example

```groovy
node {
    stage('Build') {
        echo 'Building...'
    }

    stage('Test') {
        echo 'Testing...'
    }
}
```

### What this means

* `node` → pick a machine
* You control everything
* You can use loops, conditions, variables freely

---

## Main Difference (Super Simple Table 🍋)

| Feature       | Declarative | Scripted |
| ------------- | ----------- | -------- |
| Easy to learn | ✅ Yes       | ❌ No     |
| Strict rules  | ✅ Yes       | ❌ No     |
| Flexible      | ❌ Limited   | ✅ Very   |
| Error chances | Low         | High     |
| Best for      | Beginners   | Experts  |

---

## When to use what?

### Use **Declarative Pipeline** when:

* You are new to Jenkins
* Pipeline is simple
* You want clean and safe code

### Use **Scripted Pipeline** when:

* You need complex logic
* You need loops, conditions, dynamic behavior
* You are comfortable with Groovy

---

## One-line Summary 🍋

* **Declarative** = “Simple rules, less thinking”
* **Scripted** = “Full freedom, more responsibility”


<br><br>

# **Explanation** of **Upstream** and **Downstream jobs in Jenkins**


## First: What is a Jenkins Job?

A **job** is a task Jenkins runs, like:

* Build code
* Run tests
* Deploy app

Think of each job as a **worker**.

---

## Upstream Job 🍋

### In lemon language

**Upstream job** is:

> “The job that runs FIRST and triggers another job.”

It is **before** another job.

---

### Example

* Job A builds the code
* After Job A finishes, Job B runs tests

👉 **Job A = Upstream job**
👉 **Job B = Downstream job**

---

### Simple sentence

🟢 **Upstream = Parent job**

---

## Downstream Job 🍋

### In lemon language

**Downstream job** is:

> “The job that runs AFTER another job.”

It depends on another job to start.

---

### Example

* Build → Test → Deploy

| Order | Job    | Role       |
| ----- | ------ | ---------- |
| 1     | Build  | Upstream   |
| 2     | Test   | Downstream |
| 3     | Deploy | Downstream |

---

### Simple sentence

🔵 **Downstream = Child job**

---

## Real-Life Example 🍋

Imagine making lemonade:

1. **Buy lemons** 🍋 → (Upstream)
2. **Make juice** 🥤 → (Downstream)
3. **Serve drink** 😄 → (Downstream)

You can’t make juice unless you buy lemons first.

---

## How Jenkins Connects Them

### Method 1: “Build other projects”

* In Job A settings:

  * Configure → Build Triggers
  * Select **Build other projects**
  * Add Job B

👉 Job A becomes **Upstream**, Job B becomes **Downstream**

---

### Method 2: Pipeline trigger

```groovy
build job: 'Test-Job'
```

* Current job = Upstream
* Triggered job = Downstream

---

## Key Points 🍋

* Upstream job **starts the flow**
* Downstream job **depends on upstream**
* One job can have:

  * Multiple downstream jobs
  * Multiple upstream jobs

---

## One-Line Summary 🍋

* **Upstream** → “I run first”
* **Downstream** → “I run after someone else”
