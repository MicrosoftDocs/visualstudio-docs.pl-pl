---
title: Wyłączanie debugera dla programu Windows Workflow Foundation (starsza wersja) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e5065de4ec0217123f76eb23d32bcb0facd25dcc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771575"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Wyłączanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)
W tym temacie opisano sposób wyłączania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera przy użyciu pliku konfiguracji, podczas kompilowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Użyj starszego [!INCLUDE[wfd2](../includes/wfd2-md.md)] konieczność docelowy: [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Domyślnie [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debugera dla [!INCLUDE[wf](../includes/wf-md.md)] jest włączone dla procesu hosta. Aby wyłączyć debugowanie przepływów pracy, musisz jawnie wyłączyć go, dodając wpis "DisableWorkflowDebugging"  **\<przełączników >** element  **\<system.diagnostics >** części pliku konfiguracyjnego hosta.

 Poniższy przykład pokazuje, jak zmodyfikować hosta plik konfiguracji, aby wyłączyć debugowanie przepływów pracy.

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
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [debugowanie starszych wersji przepływów pracy](../workflow-designer/debugging-legacy-workflows.md)