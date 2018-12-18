---
title: UpdateManifestForBrowserApplication Task | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7e86f07d0806f6ce5873cd91b68b4b32d58f4e6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220700"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Updatemanifestforbrowserapplication — zadanie
<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, aby dodać  **\<hostInBrowser / >** elementu w manifeście aplikacji (*\<nazwa_projektu >. exe.manifest*) podczas [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] Projekt został skompilowany.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationManifest`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, które chcesz dodać `<hostInBrowser />` elementu.|  
|`HostInBrowser`|Wymagane **logiczna** parametru.<br /><br /> Określa, czy należy zmodyfikować manifest aplikacji, aby uwzględnić  **\<hostInBrowser / >** elementu. Jeśli **true**, nowy  **\<hostInBrowser / >** element znajduje się w  **\<punktu wejścia / >** elementu. Włączenie elementu jest zbiorcza: Jeśli  **\<hostInBrowser / >** element już istnieje, nie jest usunięte, lub zastąpione. Zamiast tego dodatkowe  **\<hostInBrowser / >** zostanie utworzony element. Jeśli **false**, manifestu aplikacji nie jest modyfikowana.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] są uruchamiane przy użyciu [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] wdrażania, dlatego należy je opublikować z pomocniczymi manifesty wdrażania i aplikacji. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] używa [generateapplicationmanifest —](generateapplicationmanifest-task.md) zadania, aby wygenerować manifest aplikacji.  
  
 Następnie, aby skonfigurować aplikacje hostowane w przeglądarce, dodatkowy  **\<hostInBrowser / >** element musi zostać dodany do manifestu aplikacji, jak pokazano w poniższym przykładzie:  
  
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
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, gdy [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] projekt został skompilowany w celu dodania `<hostInBrowser />` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak i upewnij się, że `<hostInBrowser />` element znajduje się w pliku manifestu aplikacji.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Omówienie aplikacji przeglądarki XAML w WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)