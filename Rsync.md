# Local directory to remote SSH server

    rsync -avPe ssh [/local/directory] [user]@[domain]:[/directory]
    
# Remote SSH server directory to local server

    rsync -avPe ssh [user]@[domain/ip]:[/path/to/directory/] .