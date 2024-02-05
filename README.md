# What is this?
This is a sample configuration and startup script for a [Windows feature called Sandbox](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview)

## What is that?
It is a very fast, very small footprint, isolated, ephemeral instance of your copy of windows running in a special RDP Window. 
It's like a Virtual Machine but not like you're probably used to. Nothing you save on this thing will persist, so don't "restart" it unless you are done done with everything. 
The fact that nothing is saved is a feature.

## Why do I care?
Well, do you ever wish you could access your personal private resources on a computer? Say maybe, a work computer where you have permissions to enable a Windows Feature? Let us say you do, or if this is your own computer and you want some additional privacy, or hell, say you want to open a file that you're not entirely sure whether or not it's a virus but still really want to open it, the use cases are limitless.

## Getting Started
If the feature is installed on your computer, all you need to do is clone this repo (it's only really two files) update the ExampleSandbox.wsb with the absolute paths by replacing [MAKE YOUR OWN PATH] with the path to the scripts folder on your pc along with the path to a dropbox folder of your choice.
That's it, Double click the ExampleSandbox.wsb, profit.

```XML
<Configuration>
    ...
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
    ...
</Configuration>
```

### There's more, isn't there?
I have included a startup script that will download a copy of Signal along with VisualStudioCode you can modify it to whatever you want.

If you intend to use this to open a virus, you should look into disabling the Networking Interface in the config and adjusting the ProtectedClient feature flag.

An advanced scenario would be using [Desired State Configuration](https://docs.microsoft.com/en-us/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=dsc-2.0) to further configure your ephemeral instance.

### Further Reading
[Window Sandbox Configuration Documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-sandbox/windows-sandbox-configure-using-wsb-file)
