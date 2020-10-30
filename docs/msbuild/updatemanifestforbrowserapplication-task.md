---
title: UpdateManifestForBrowserApplication — — Zadanie | Microsoft Docs
description: Dowiedz się, jak MSBuild uruchamia zadanie UpdateManifestForBrowserApplication —, aby dodać element hostInBrowser do manifestu aplikacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 43e8fc7b9b09af51ea3be73409e2dcde9a718cee
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046809"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication, zadanie

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Zadanie jest uruchamiane w celu dodania **\<hostInBrowser />** elementu do manifestu aplikacji ( *\<projectname> . exe. manifest* ) w przypadku skompilowania projektu aplikacji przeglądarki XAML (XBAP).

## <a name="task-parameters"></a>Parametry zadania

|Parametr|Opis|
|---------------|-----------------|
|`ApplicationManifest`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, do którego chcesz dodać `<hostInBrowser />` element.|
|`HostInBrowser`|Wymagany parametr **logiczny** .<br /><br /> Określa, czy należy zmodyfikować manifest aplikacji w celu uwzględnienia **\<hostInBrowser />** elementu. W przypadku **wartości true** **\<hostInBrowser />** w elemencie znajduje się nowy element **\<entryPoint />** . Dołączenie elementu jest skumulowane: Jeśli **\<hostInBrowser />** element już istnieje, nie zostanie usunięty ani nadpisany. Zamiast tego **\<hostInBrowser />** zostanie utworzony dodatkowy element. W przypadku **wartości false** manifest aplikacji nie jest modyfikowany.|

## <a name="remarks"></a>Uwagi

 Aplikacje XBAP są uruchamiane przy użyciu wdrażania ClickOnce, dlatego należy je opublikować z obsługą manifestu wdrażania i aplikacji. Program MSBuild używa zadania [GenerateApplicationManifest —](generateapplicationmanifest-task.md) do wygenerowania manifestu aplikacji.

 Następnie w celu skonfigurowania aplikacji do obsługi z poziomu przeglądarki **\<hostInBrowser />** należy dodać do manifestu aplikacji dodatkowy element, jak pokazano w następującym przykładzie:

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

 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Zadanie jest uruchamiane, gdy projekt XBAP zostanie skompilowany w celu dodania `<hostInBrowser />` elementu.

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak upewnić się, że `<hostInBrowser />` element jest zawarty w pliku manifestu aplikacji.

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
- [Dokumentacja zadań](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)