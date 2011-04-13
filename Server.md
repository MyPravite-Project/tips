# Use logrotate

From http://www.trottercashion.com/2010/04/21/logrotate-for-rails.html

Create /etc/logrotate.d/our_app
    
    /srv/our_app/current/log/*.log {
      daily          # rotate daily
      rotate 12      # keep twelve copies
      compress       # gzip the old files
      missingok      # don't barf if there is no log
      copytruncate
    }
