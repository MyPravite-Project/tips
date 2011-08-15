# .Gemrc

See http://www.justinball.com/2011/07/18/ruby-1-9-2-rvm-and-a-nasty-error-when-installing-rubygems-couldnt-parse-yaml-at-line-2-column-10-psychsyntaxerror/

Old file:

    echo -e '---
    :benchmark: false
    gem: --no-ri --no-rdoc
    :update_sources: true
    :bulk_threshold: 1000
    :verbose: true
    :sources:
    - http://rubygems.org
    - http://gems.github.com
    :backtrace: false' > ~/.gemrc
