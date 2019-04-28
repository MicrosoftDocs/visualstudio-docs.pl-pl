---
title: Debugowanie starszych wersji przepływów pracy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 80edcfb171e8e87c384a05b889a8fa11b1e7a723
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439190"
---
# <a name="debugging-legacy-workflows"></a>Debugowanie starszych wersji przepływów pracy
Jeśli używasz starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] w [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] tworzenie [!INCLUDE[wf](../includes/wf-md.md)] aplikacji czy target.NET Framework 3.0 lub 3.5, można debugować z przepływami pracy, jak każdy inny program ustawiania punktów przerwania, dołączanie do procesów i wątków badanie i stos wywołań. Istnieje również możliwość debugowania zdalnego.  
  
> [!NOTE]
> Jeśli zostały zainstalowane i odinstalować na komputerze wielu wersji programu Visual Studio, debugowanie WF3 może zakończyć się niepowodzeniem przy użyciu jednego z dwóch następujące możliwości:  
> 
> - Nie są osiągane punktów przerwania.  
>   - Zostanie wyświetlony następujący komunikat:  
> 
>   **Nie można rozpocząć debugowania na serwerze sieci web. Debuger nie jest poprawnie zainstalowany.  Nie można debugować żądanego typu kodu.  Uruchom Instalatora, aby zainstalować lub naprawić debuger.**  
> 
>   Jeśli wystąpi jedno z tych scenariuszy podczas debugowania środowiska .NET Framework 3.0 lub 3.5 przepływy pracy, wykonaj naprawę instalacji programu Visual Studio.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] integruje się z następujących standardowych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowania systemu windows:  
  
- **Punkt przerwania**: Działa zgodnie z oczekiwaniami, ale Określ działanie dla nazwy funkcji.  
  
- **Stos wywołań**: Zmodyfikowane w celu zapewnienia zarys czynności, które zostały wykonane w wystąpieniu przepływu pracy. Wpisy w **stos wywołań** są najpierw głębokość wyszukiwania wykonywania działań. Możesz kliknąć dwukrotnie wpis, aby Umieść fokus na wybrane działanie.  
  
- **Wątki**: Zawiera identyfikator wystąpienia wystąpienia przepływu pracy, która jest debugowana.  
  
  Visual Studio dla Windows Workflow Foundation nie obsługuje następujących funkcji debugowania:  
  
- Warunkowe punkty przerwania na powierzchni projektowej.  
  
- QuickWatch.  
  
- Ustaw następną instrukcję.  
  
- Uruchom do kursora.  
  
- Edytuj i Kontynuuj.  
  
- Debugowanie just in time.  
  
- Debugowanie w trybie mieszanym.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Wyłączanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)  
  
 [Instrukcje: Debugowanie przepływów pracy opartych na programie ASP.NET (starsza wersja)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)  
  
 [Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)  
  
 [Debugowanie przepływów pracy ze zdalnego komputera (starsza wersja)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)  
  
 [Opcje debugowania wykonywania krokowego (starsza wersja)](../workflow-designer/debug-stepping-options-legacy.md)  
  
 [Instrukcje: Opcja zmiany debugowania krokowego (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)