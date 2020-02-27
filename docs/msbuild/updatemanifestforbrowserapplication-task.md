---
title: UpdateManifestForBrowserApplication Task | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631331"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication —, zadanie

Zadanie <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> jest uruchamiane w celu dodania elementu **\<HostInBrowser/>** do manifestu aplikacji ( *\<ProjectName >. exe. manifest*) w przypadku skompilowania projektu aplikacji przeglądarki XAML (XBAP).

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, do którego ma zostać dodany element `<hostInBrowser />`.|
|`HostInBrowser`|Wymagany parametr **logiczny** .<br /><br /> Określa, czy należy zmodyfikować manifest aplikacji w taki sposób, aby zawierał **\<HostInBrowser/>** . W przypadku **wartości true**nowy element **\<HostInBrowser/>** jest zawarty w elemencie **\<EntryPoint/>** . Dołączenie elementu jest skumulowane: Jeśli element **\<HostInBrowser/>** już istnieje, nie zostanie on usunięty ani nadpisany. Zamiast tego tworzony jest dodatkowy **\<element HostInBrowser/>** . W przypadku **wartości false**manifest aplikacji nie jest modyfikowany.|

## <a name="remarks"></a>Uwagi

 Aplikacje XBAP są uruchamiane przy użyciu wdrażania ClickOnce, dlatego należy je opublikować z obsługą manifestu wdrażania i aplikacji. Program MSBuild używa zadania [GenerateApplicationManifest —](generateapplicationmanifest-task.md) do wygenerowania manifestu aplikacji.

 Następnie w celu skonfigurowania aplikacji do hostowania z poziomu przeglądarki należy dodać do manifestu aplikacji dodatkowy **\<element HostInBrowser/>** , jak pokazano w następującym przykładzie:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 Zadanie <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> jest uruchamiane, gdy projekt XBAP zostanie skompilowany w celu dodania elementu `<hostInBrowser />`.

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak upewnić się, że element `<hostInBrowser />` jest zawarty w pliku manifestu aplikacji.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)