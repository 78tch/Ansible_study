user00@TPX250:~/My_test$ vagrant up
Bringing machine 'web' up with 'virtualbox' provider...                        
==> web: Importing base box 'ubuntu/cosmic64'...                               
==> web: Matching MAC address for NAT networking...                            
==> web: Checking if box 'ubuntu/cosmic64' is up to date...                    
==> web: Setting the name of the VM: My_test_web_1542192556239_69701           
==> web: Clearing any previously set network interfaces...                     
==> web: Preparing network interfaces based on configuration...                
    web: Adapter 1: nat
    web: Adapter 2: hostonly
==> web: Forwarding ports...
    web: 22 (guest) => 2222 (host) (adapter 1)                                 
==> web: Running 'pre-boot' VM customizations...                               
==> web: Booting VM...
==> web: Waiting for machine to boot. This may take a few minutes...           
    web: SSH address: 127.0.0.1:2222
    web: SSH username: vagrant
    web: SSH auth method: private key
    web: Warning: Remote connection disconnect. Retrying...                    
    web:
    web: Vagrant insecure key detected. Vagrant will automatically replace     
    web: this with a newly generated keypair for better security.              
    web:
    web: Inserting generated public key within guest...                        
    web: Removing insecure key from the guest if it's present...               
    web: Key inserted! Disconnecting and reconnecting using new SSH key...     
==> web: Machine booted and ready!
==> web: Checking for guest additions in VM...                                 
==> web: Setting hostname...
==> web: Configuring and enabling network interfaces...                        
==> web: Mounting shared folders...
    web: /vagrant => /home/user00/My_test                                      