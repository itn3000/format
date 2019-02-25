﻿## dotnet-format

[![Nuget)](https://img.shields.io/nuget/vpre/dotnet-format.svg)](https://www.nuget.org/packages/dotnet-format)

[![MyGet](https://img.shields.io/dotnet.myget/format/v/dotnet-format.svg?label=myget)](https://dotnet.myget.org/feed/format/package/nuget/dotnet-format)


|Branch| Windows (Debug)| Windows (Release)| Linux (Debug) | Linux (Release)
|---|:--:|:--:|:--:|:--:|
[master](https://github.com/dotnet/format/tree/master)|[![Build Status](https://dev.azure.com/dnceng/public/_apis/build/status/dotnet/format/dotnet.format?branchName=master&jobName=Windows&configuration=debug&label=build)](https://dev.azure.com/dnceng/public/_build/latest?definitionId=347&branchName=master)|[![Build Status](https://dev.azure.com/dnceng/public/_apis/build/status/dotnet/format/dotnet.format?branchName=master&jobName=Windows&configuration=release&label=build)](https://dev.azure.com/dnceng/public/_build/latest?definitionId=347&branchName=master)|[![Build Status](https://dev.azure.com/dnceng/public/_apis/build/status/dotnet/format/dotnet.format?branchName=master&jobName=Linux&configuration=debug&label=build)](https://dev.azure.com/dnceng/public/_build/latest?definitionId=347&branchName=master)|[![Build Status](https://dev.azure.com/dnceng/public/_apis/build/status/dotnet/format/dotnet.format?branchName=master&jobName=Linux&configuration=release&label=build)](https://dev.azure.com/dnceng/public/_build/latest?definitionId=347&branchName=master)


`dotnet-format` is a code formatter for `dotnet` that applies style preferences to a project or solution. Preferences will be read from an `.editorconfig` file, if present, otherwise a default set of preferences will be used.

### How To Install

The `dotnet-format` nuget package is currently in beta and published to nuget.org. You can visit the [dotnet-format nuget page](https://www.nuget.org/packages/dotnet-format/) to get the latest version number.

You can install the tool using the following command.

```console
dotnet tool install -g dotnet-format --version 3.0.0-beta4-19105-10
```

#### Installing Development Builds

Development builds of `dotnet-format` are being hosted on myget. You can visit the [dotnet-format myget page](https://dotnet.myget.org/feed/format/package/nuget/dotnet-format) to get the latest version number.

You can install the tool using the following command.

```console
dotnet tool install -g dotnet-format --version 3.0.0-prerelease.19119.4 --add-source https://dotnet.myget.org/F/format/api/v3/index.json
```

### How To Use

By default `dotnet-format` will look in the current directory for a project or solution file and use that as the workspace to format. If more than one project or solution file is present in the current directory you will need to specify the workspace to format using the `-w` option. You can control how verbose the output will be by using the `-v` option.

```
Usage:
  dotnet-format [options]

Options:
  -w, --workspace    The solution or project file to operate on. If a file is not specified, the command will search
                     the current directory for one.
  -v, --verbosity    Set the verbosity level. Allowed values are q[uiet], m[inimal], n[ormal], d[etailed], and
                     diag[nostic]
  --version          Display version information
```

Add `format` after `dotnet` and before the command arguments that you want to run:

| Examples                                                 |
| -------------------------------------------------------- |
| dotnet **format**                                        |
| dotnet **format** -w &lt;workspace&gt;                   |
| dotnet **format** -v diag                                |
| dotnet **format** -w &lt;workspace&gt; -v diag           |

### How To Uninstall

You can uninstall the tool using the following command.

```console
dotnet tool uninstall -g dotnet-format
```

### How To Build From Source

You can build and package the tool using the following commands. The instructions assume that you are in the root of the repository.

```console
build -pack
# The final line from the build will read something like
# Successfully created package '..\artifacts\packages\Debug\Shipping\dotnet-format.3.0.0-dev.nupkg'.
# Use the value that is in the form `3.0.0-dev` as the version in the next command.
dotnet tool install --add-source .\artifacts\packages\Debug\Shipping -g dotnet-format --version <version>
dotnet format
```

> Note: On macOS and Linux, `.\artifacts` will need be switched to `./artifacts` to accommodate for the different slash directions.
