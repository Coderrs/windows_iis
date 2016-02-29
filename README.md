# windows_iis
Windows Module to Setup and Manage IIS, tested with windows 2012 evaluation 180 days version, hence you might find few things that are not needed in normal setup, but my system needed those for this module to execute properly.

#Pre-requisites 

Latest Puppet windows agent is used for this setup and testing. 

If running with masterless setup for development purposes do read - https://docs.puppetlabs.com/windows/troubleshooting.html 
and install certs else you cannnot download the required forge modules as in next steps; if you have puppet master ignore this link
and continue with dependencies. 

Should have 'puppet/windowsfeature' module installed from forge ; 'puppet module install puppet/windowsfeature'

Should have 'puppet/iis' module installed from forge ; 'puppet module install puppet/iis'

puppet module list
C:/ProgramData/PuppetLabs/code/environments/production/modules

├── coders-windows_iis (v0.0.1)

├── puppet-iis (v2.0.0)

├── puppet-windowsfeature (v1.1.0)

├── puppetlabs-powershell (v1.0.6)

└── puppetlabs-stdlib (v4.11.0)

#Usage
To Install this module from geppetto to target system use below commands and 
you can also use --git in case you need to download from git

From Geppetto - > Right Click on module -> Export -> Export Modules to file system, which will o/p coders-windows_iis-0.0.1.tar.gz , copy the file to the windows Server and run below commands one by one in puppet shell (Run as Administrator)  

puppet module install puppet/windowsfeature
</br>
puppet module install puppet/iis
</br>
puppet module install coders-windows_iis-0.0.1.tar.gz --ignore-dependencies

# References
https://docs.puppetlabs.com/puppet/latest/reference/lang_defined_types.html
http://docs.puppetlabs.com/puppet/4.3/reference/services_agent_windows.html
https://docs.puppetlabs.com/windows/troubleshooting.html
https://puppetlabs.com/blog/managing-permissions-windows-access-control-lists

#Suggestions of update in puppet-iis:
In puppet-iis the dependency tree should have puppet/windowsfeature, which will perform required setup of iis and also manage sites
<br>
Services are not Managed in the puppet-iis module, and one needs a code to ensure service running instead of passing parameter's to puppet-iis module to manage service.
<br>
File / folder creation for site and permissions/Acl's for IIS security.
<br>
The puppet-iis module needs more documentation



