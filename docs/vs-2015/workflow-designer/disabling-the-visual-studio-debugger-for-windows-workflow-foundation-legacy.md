---
title: Wyłączanie debugera dla Windows Workflow Foundation (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656782"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wyłączanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)
W tym temacie opisano, jak wyłączyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debuger przy użyciu pliku konfiguracji podczas kompilowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Domyślnie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debuger dla programu [!INCLUDE[wf](../includes/wf-md.md)] jest włączony dla procesu hosta. Aby wyłączyć debugowanie przepływu pracy, należy jawnie ją wyłączyć przez dodanie elementu wpisu "DisableWorkflowDebugging" **\<switches>** w **\<system.diagnostics>** sekcji pliku konfiguracji hosta.

 Poniższy przykład pokazuje, jak zmodyfikować plik konfiguracji hosta w celu wyłączenia debugowania przepływu pracy.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Zobacz też
 [Wywoływanie debugera programu Visual Studio dla Windows Workflow Foundation (starsze)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)