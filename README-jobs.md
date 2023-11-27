
A Job creates one or more Pods and will continue to retry execution of the Pods until a specified number of them successfully terminate

As pods successfully complete, the Job tracks the successful completions

Deleting a Job will clean up the Pods it created. Suspending a Job will delete its active Pods until the Job is resumed again.


# 1. Create a JOB using the examples file

    cd examples
    kubectl apply -f job1.yaml
    kubectl logs jobs/pi

    kubectl apply -f job2.yaml
    kubectl logs jobs/countdown

# 2. Kubernetes CronJob Example  

A CronJob is useful for performing periodic, scheduled tasks like generating backups and reports. It is important to configure each task, so it recurs indefinitely. 

    cd  examples
    kubectl apply -f job3.yaml
    kubectl get CronJob

The .spec.schedule field is required. The value of that field follows the Cron syntax:

    # ┌───────────── minute (0 - 59)
    # │ ┌───────────── hour (0 - 23)
    # │ │ ┌───────────── day of the month (1 - 31)
    # │ │ │ ┌───────────── month (1 - 12)
    # │ │ │ │ ┌───────────── day of the week (0 - 6) (Sunday to Saturday;
    # │ │ │ │ │                                   7 is also Sunday on some systems)
    # │ │ │ │ │                                   OR sun, mon, tue, wed, thu, fri, sat
    # │ │ │ │ │
    # * * * * *

For example, 0 0 13 * 5 states that the task must be started every Friday at midnight, as well as on the 13th of each month at midnight.

# 3. Kubernetes Parallel Jobs Example 

    cd  examples
    kubectl apply -f job4.yaml

Parallelism: Notice the new configuration item, parallelism. The previous job executed pods one after another. However, we can configure a job to run pods in parallel using this new configuration.