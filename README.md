# Whats is this?
This is a sample configuration and startup script for a [Windows feature called Sandbox](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-sandbox/)

## What is that?
it is a very fast, very small footprint, isolated, epemeral instance of your copy of windows running in a window. 
It's kinda like a Virtual Machine but not, Nothing you save on this thing will persist so don't "restart" it unless you are done done with everything, the fact nothing is saved is a feature.

## Why do I care?
Well do you ever wish you could access your personal private resources on a computer? Say maybe, a work computer where you have permissoins to enable a Windows Feature? Lets say you do or if this is your own computer and you want some additional privacy or hell say you want to open a file that your not entirely sure to wether or not its a virius but still really want to open it, the usecases are limitless.

## Getting Started
If the feature is installed on your computer all you need to do is clone this repo (its only really two files) Update the ExampleSandbox.wsb with the absolute paths by replacing [MAKE YOUR OWN PATH] with the path to the scripts folder on your pc along with the path to a dropbox folder of your choice.
Thats it, double click the ExampleSandbox.wsb, profit.

```XML
<Configuration>
    <ProtectedClient>false</ProtectedClient>
    <MappedFolders>
        <MappedFolder>
            <HostFolder>[MAKE YOUR OWN PATH]</HostFolder>
            <SandboxFolder>C:\Dropbox</SandboxFolder>
            <ReadOnly>true</ReadOnly>
        </MappedFolder>
        <MappedFolder>
            <HostFolder>[MAKE YOUR OWN PATH]</HostFolder>
            <SandboxFolder>C:\Scripts</SandboxFolder>
            <ReadOnly>true</ReadOnly>
        </MappedFolder>
    </MappedFolders>
    <LogonCommand>
        <Command>C:\Scripts\InstallApps.bat</Command>
    </LogonCommand>
</Configuration>
```

### Theres more isn't there?
I have included a startup script, that will download a copy of Signal along with VisualStudioCode you can modify it to what ever you want.

If you indend to use this to open a virus you should look into the disabling the Networking Interface in the config along with adjusting the ProtectedClient feature flag.

An advance sencnario would be using [Desired State Configuration](https://docs.microsoft.com/en-us/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=dsc-2.0) to further configure your ephemeral instance.

### Further Reading
[Window Sandbox Configuration Documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-sandbox/windows-sandbox-configure-using-wsb-file)