# Delayed Job

Source http://stackoverflow.com/questions/3638250/how-to-cancel-scheduled-job-with-delayed-job-in-rails

## List jobs

    Delayed::Job.all

## Delete a job

    job = Delayed::Job.find(params[:id])
    job.delete

## Custom job

    class MyJob < Struct.new(:some_value);
        def perform
            # ...
        end
    end

    my_job = MyJob.new('xyz')
    job = Delayed::Job.enqueue(my_job, {:priority => 0, :run_at => 1.hour.from_now})
    job.name
    # => "MyJob"
    job.handler
    
## Custom job name

    class MyJob < Struct.new(:user_id);
        def perform
            # ...
        end

        def display_name
            return "MyJob-User-#{user_id}"
        end 
    end

## Init.d script

Create /etc/init.d/delayed_job
Remember to change [app] to your app name and your deploy user

    #! /bin/sh
    set_path="cd /u/[app]/current"
    deploy_user="deploy"

    case "$1" in
        start)
        echo -n "Starting delayed_job: "
        su - $deploy_user -c "$set_path; RAILS_ENV=production script/delayed_job start" >> /var/log/delayed_job.log 2>&1
        echo "done."
        ;;
        stop)
        echo -n "Stopping delayed_job: "
        su - $deploy_user -c "$set_path; RAILS_ENV=production script/delayed_job stop" >> /var/log/delayed_job.log 2>&1
        echo "done."
        ;;
        *)
        echo "Usage: $N {start|stop}" >&2
        exit 1
        ;;
    esac

    exit 0

Then chmod it

    sudo chmod +x /etc/init.d/delayed_job
    
## Monit

From http://www.funonrails.com/2011/03/monitor-delayedjob-in-rails.html

Create delayed_job.monitrc under /etc/monit/conf.d (Be sure that /etc/monit/monitrc has include /etc/monit/conf.d at the bottom)

    check process delayed_job with pidfile /u/[app]/shared/pids/delayed_job.pid
        stop program = "/etc/init.d/delayed_job stop"
        start program = "/etc/init.d/delayed_job start"
        if totalmem > 100.0 MB for 3 cycles then restart
        if cpu usage > 95% for 3 cycles then restart
