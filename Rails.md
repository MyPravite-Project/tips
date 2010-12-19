# Ruby on Rails

## UTF-8 strings

    "þ".mb_chars.capitalize.to_s #=> Þ
	
## Ruby 1.9 file's encoding

Add one of the following to the top of the file

    # encoding: UTF-8

    # coding: UTF-8

    # -*- coding: UTF-8 -*-