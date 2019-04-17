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
ms.openlocfilehash: 9b78668b0df966de45eb309f068f448809fed8e2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662858"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, aby dodać  **\<hostInBrowser / >** elementu w manifeście aplikacji (*projectname*. exe.manifest) podczas [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] projekt został skompilowany.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`ApplicationManifest`|Wymagane **[] ITaskItem** parametru.<br /><br /> Określa ścieżkę i nazwę pliku manifestu aplikacji, które chcesz dodać `<hostInBrowser />` elementu.|  
|`HostInBrowser`|Wymagane **logiczna** parametru.<br /><br /> Określa, czy należy zmodyfikować manifest aplikacji, aby uwzględnić  **\<hostInBrowser / >** elementu. Jeśli **true**, nowy `<` **hostInBrowser / >** element znajduje się w  **\<punktu wejścia / >** elementu. Należy pamiętać, że element jest włączenie: Jeśli  **\<hostInBrowser / >** element już istnieje, jest ono usuwane lub zastąpione. Zamiast tego dodatkowe  **\<hostInBrowser / >** zostanie utworzony element. Jeśli **false**, manifestu aplikacji nie jest modyfikowany.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] są uruchamiane przy użyciu [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] wdrożenia, a więc musi przez opublikowana z użyciem obsługi manifesty wdrażania i aplikacji. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] używa [generateapplicationmanifest —](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) zadania, aby wygenerować manifest aplikacji.  
  
 Następnie, aby skonfigurować aplikacje hostowane w przeglądarce, dodatkowy element  **\<hostInBrowser / >** , należy dodać do manifestu aplikacji jako show w następującym przykładzie:  
  
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
  
 <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> Zadanie zostanie uruchomione, gdy [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] projekt został skompilowany w celu dodania `<hostInBrowser />` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak upewnić się, że `<hostInBrowser />` element znajduje się w pliku manifestu aplikacji.  
  
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
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Aplikacje przeglądarek WPF XAML — omówienie](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
