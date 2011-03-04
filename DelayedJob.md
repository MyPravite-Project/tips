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