---
layout: post
title: Create a Web Deployment Package with Cake Build
category: Node.js
---

This is simple tip to help you create Web Deployment Packages with [Cake](http://cakebuild.net/).


<!--excerpt-->

If you have a ASP.NET project and you want to create a Web Deployment package using Cake, you just need to use the MSBUILD Command with the right arguments.

Feel free to copy the following command and paste it in a Task from your Cake file.

		MSBuild("PROJECT_NAME.csproj", settings =>
			settings.SetConfiguration(configuration)
			.UseToolVersion(MSBuildToolVersion.VS2015)
			.WithTarget("Package")
			.WithProperty("VisualStudioVersion", new string[]{"14.0"})
			.WithProperty("PackageLocation", new string[]{ packageDir.ToString()  })
			.WithProperty("PackageTempRootDir", new string[]{"root"})
			);

Here an example of a complete script (_build.cake_). 

	var target = Argument("target", "Default");
	var configuration = Argument("configuration", "Release");
	var packageDir = MakeAbsolute(Directory("./package"));

	Information("BUILD DIR:" + packageDir);

	Task("Default")
	.Does(() =>
	{
	
		MSBuild("PROJECT_NAME.csproj", settings =>
			settings.SetConfiguration(configuration)
			.UseToolVersion(MSBuildToolVersion.VS2015)
			.WithTarget("Package")
			.WithProperty("VisualStudioVersion", new string[]{"14.0"})
			.WithProperty("PackageLocation", new string[]{ packageDir.ToString()  })
			.WithProperty("PackageTempRootDir", new string[]{"root"})
			);


	});

	RunTarget(target);


Hope this helps.
