# Vagrantfile
Vagrantfile の設定方法を勉強していく過程です


１．config.vm  

設定キー| 内容  |例  
--|---|--  
config.vm.box | HashiCorpのVagrant Cloudのボックスの略称  | "ubuntu/cosmic64"
  config.vm.box_check_update |   |  
  config.vm.box_download_checksum |   |  
  config.vm.box_download_checksum_type |   |  
  config.vm.box_download_client_cert |   |  
  config.vm.box_download_ca_cert |   |  
  config.vm.box_download_ca_path |   |  
  config.vm.box_download_insecure |   |  
  config.vm.box_download_location_trusted |   |  
  config.vm.box_url |   |  
  config.vm.box_version |   |  
  config.vm.communicator |   |  
  config.vm.graceful_halt_timeout |   |  
  config.vm.guest |   |  
  config.vm.hostname |   |  
  config.vm.ignore_box_vagrantfile |   |  
  config.vm.post_up_message |   |  
  config.vm.provider |   |  
  config.vm.provision |   |  
  config.vm.synced_folder |   |  
  config.vm.usable_port_range |   |  

２．config.ssh  

設定キー|内容|例  
-|-|-  
config.ssh.username  |   |   
config.ssh.host  |   |  
config.ssh.port  |   |  
config.ssh.guest_port  |   |  
config.ssh.private_key_path  |   |  
config.ssh.keys_only  |   |  
config.ssh.paranoid  |   |  
config.ssh.forward_agent  |   |  
config.ssh.forward_x11  |   |  
config.ssh.forward_env  |   |  
config.ssh.insert_key  |   |  
config.ssh.proxy_command  |   |  
config.ssh.pty  |   |  
config.ssh.keep_alive  |   |  
config.ssh.shell  |   |  
config.ssh.export_command_template  |   |  
config.ssh.sudo_command  |   |  
config.ssh.compression  |   |  
config.ssh.dsa_authentication  |   |  
config.ssh.extra_args  |   |  
