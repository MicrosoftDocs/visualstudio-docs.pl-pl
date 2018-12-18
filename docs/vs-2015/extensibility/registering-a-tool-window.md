---
title: Rejestrowanie okna narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c9e8a6a86fb858b5c0e85aafc21095bd579b396
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786174"
---
# <a name="registering-a-tool-window"></a>Rejestrowanie okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz zarejestrować się przy użyciu narzędzia systemu windows <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> i  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## <a name="example"></a>Przykład  
  
```csharp  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 W powyższym kodzie <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> rejestruje okien narzędzi PersistedWindowPane i DynamicWindowPane za pomocą programu Visual Studio. Okno narzędzia utrwalonych jest zadokowany i z zakładkami z **Eksploratora rozwiązań**, i dynamiczne okno otrzymuje od położenia i rozmiaru domyślnego. Dynamiczne okna składa się błędem przejściowym, co oznacza, że nie jest tworzony podczas uruchamiania. Ta zapisuje wartość DontForceCreate w kluczu ToolWindows w rejestrze systemowym. Aby uzyskać więcej informacji, zobacz [konfiguracji wyświetlania okna narzędzia](../extensibility/tool-window-display-configuration.md).

