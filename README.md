# dynamic-dependencies-sample

## How to use this
This sample is configured to automatically replace a nuget package dependency by its source code if it is available locally in the Dependencies directory by using the MSBuild Choose statement in the .csproj file. The steps below demonstrate how this functionaly works correctly in Visual Studio version 17.1.7, but fails in 17.2.1.

### Use nuget package reference.
By default, after cloning this repository, the project DynamicDependencies restores an external nuget package reference, in this case Swashbuckle.AspNetCore.Swagger (but any nuget package will do). Opening the Visual Studio solution will prompt a warning that not all projects could be loaded. This behaviour is expected and is not a problem. The project that can't be loaded is a reference to the source code of the dependency which is not required when using the nuget package reference.

### Use project reference from source code.
Now, we want to include the source code of the dependency:
1. Close Visual Studio.
2. Clone the Swashbuckle.AspNetCore source code from the git repository (https://github.com/domaindrivendev/Swashbuckle.AspNetCore/blob/master/README.md) into the directory **Dependencies**.
3. Start Visual Studio and load the solution.
4. In Visual Studio 17.1.7 the Swashbuckle dependency of the DynamicDependencies project has automatically switched to the local project reference and is correctly loaded.
4. In Visual Studio 17.2.1 the Swashbuckle dependency of the DynamicDependencies project still references the nuget package.
