# Local directory to remote SSH server

    rsync -avPe ssh [/local/directory] [user]@[domain]:[/directory]
    
# Remote SSH server directory to local server

    rsync -avPE ssh [user]@[domain/ip]:[/path/to/directory/] .