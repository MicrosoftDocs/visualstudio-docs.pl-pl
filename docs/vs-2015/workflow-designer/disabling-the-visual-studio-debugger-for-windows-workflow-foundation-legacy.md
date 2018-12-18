---
title: Wyłączanie debugera dla programu Windows Workflow Foundation (starsza wersja) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: fafa90b547e84df9b300b83dfcb63f9a2f56ada5
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063705"
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