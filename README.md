# windows_iis
Windows Module to Manage IIS , tested with windows 2012 evaluation 180 days version, 
hence you might find few things that are not needed in normal setup , 
but my system needed those for this module to execute completely

#Pre-requisites 
If running with masterless setup for development purposes do read - https://docs.puppetlabs.com/windows/troubleshooting.html 
and install certs else you cannnot download the required forge modules as in next steps; if you have puppet master ignore this link
and continue with dependencies 

Should have 'puppet/windowsfeature' module installed from forge ; 'puppet module install puppet/windowsfeature'

Should have 'puppet/iis' module installed from forge ; 'puppet module install puppet/iis'

:puppet module list
:C:/ProgramData/PuppetLabs/code/environments/production/modules
:├── coders-windows_iis (v0.0.1)
:├── puppet-iis (v2.0.0)
:├── puppet-windowsfeature (v1.1.0)
:├── puppetlabs-powershell (v1.0.6)
:└── puppetlabs-stdlib (v4.11.0)

#Usage
To Install this module from geppetto to target system use below commands and 
you can also use --git in case you need to download from git

From Geppetto - > Right Click on module -> Export -> Export Modules to file system




# References
1) https://docs.puppetlabs.com/puppet/latest/reference/lang_defined_types.html
2) http://docs.puppetlabs.com/puppet/4.3/reference/services_agent_windows.html
3) https://docs.puppetlabs.com/windows/troubleshooting.html
4) https://puppetlabs.com/blog/managing-permissions-windows-access-control-lists

Helpful commands 
REM puppet config print modulepath

echo un-installing puppet module 
puppet module uninstall coders-windows_iis

echo installing puppet module 
puppet module install coders-windows_iis-0.0.1.tar.gz --ignore-dependencies

Suggestions of update in puppet-iis:
1) in puppet-iis update the dependency tree with inclusion of puppet/windowsfeature , which will be needed 
2) Create-my_application_pool]/returns: Import-Module : The specified module 'WebAdministration' was not loaded


