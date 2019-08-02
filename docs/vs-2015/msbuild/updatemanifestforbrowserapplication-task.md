---
title: UpdateManifestForBrowserApplication Task | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740220"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadanie jest uruchamiane w celu [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]  **\<dodania elementu HostInBrowser/>** do manifestu aplikacji (ProjectName. exe. manifest) podczas kompilowania projektu. <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationManifest`|Wymagany parametr **ITaskItem []** .<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, do którego chcesz dodać `<hostInBrowser />` element.|  
|`HostInBrowser`|Wymagany parametr **logiczny** .<br /><br /> Określa, czy należy zmodyfikować manifest aplikacji tak, aby zawierał  **\<element HostInBrowser/>** . Jeśli **wartość**jest równa `<`true, nowy element **HostInBrowser/>** jest zawarty w  **\<elemencie EntryPoint/>** . Należy zauważyć, że dołączenie elementu jest kumulatywne: Jeśli  **\<element HostInBrowser/>** już istnieje, nie zostanie usunięty ani nadpisany. Zamiast tego jest tworzony dodatkowy  **\<element HostInBrowser/>** . W przypadku **wartości false**manifest aplikacji nie jest modyfikowany.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)]są uruchamiane przy użyciu [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] wdrożenia i, dlatego, muszą być opublikowane z obsługą manifestu wdrażania i aplikacji. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)]używa zadania [GenerateApplicationManifest —](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) do wygenerowania manifestu aplikacji.  
  
 Następnie w celu skonfigurowania aplikacji do obsługi z poziomu przeglądarki należy dodać do manifestu aplikacji dodatkowy element  **\<HostInBrowser/>** , jak pokazano w następującym przykładzie:  
  
```  
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
  
 Zadanie jest uruchamiane [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] po skompilowaniu projektu `<hostInBrowser />` w celu dodania elementu. <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak upewnić się, `<hostInBrowser />` że element jest zawarty w pliku manifestu aplikacji.  
  
```  
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
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Aplikacje przeglądarek WPF XAML — omówienie](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
