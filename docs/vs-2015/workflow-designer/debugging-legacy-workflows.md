---
title: Debugowanie starszych przepływów pracy | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656867"
---
# <a name="debugging-legacy-workflows"></a>Debugowanie starszych wersji przepływów pracy
Jeśli używasz starszej [!INCLUDE[wfd1](../includes/wfd1-md.md)] w [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] do kompilowania aplikacji [!INCLUDE[wf](../includes/wf-md.md)], które target.NET Framework 3,0 lub 3,5, można debugować przepływy pracy, podobnie jak każdy inny program, ustawiając punkty przerwania, dołączając do procesów i sprawdzając wątki oraz stos wywołań. Istnieje również możliwość debugowania zdalnego.

> [!NOTE]
> Jeśli na maszynie zainstalowano i odinstalowano wiele wersji programu Visual Studio, debugowanie WF3 może zakończyć się niepowodzeniem z jedną z dwóch następujących możliwości:
>
> - Twoje punkty przerwania nie trafią.
>   - Zostanie wyświetlony następujący komunikat:
>
>   **Nie można rozpocząć debugowania na serwerze sieci Web. Debuger nie jest poprawnie zainstalowany.  Nie można debugować żądanego typu kodu.  Uruchom Instalatora, aby zainstalować lub naprawić debuger.**
>
>   Jeśli jeden z tych scenariuszy występuje podczas debugowania .NET Framework 3,0 lub 3,5 przepływów pracy, wykonaj naprawę instalacji programu Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] integruje się z następującym standardowym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowania systemu Windows:

- **Punkt przerwania**: działa zgodnie z oczekiwaniami, ale określono działanie dla nazwy funkcji.

- **Stos wywołań**: zmodyfikowany w celu zapewnienia konspektu działań, które zostały wykonane w wystąpieniu przepływu pracy. Wpisy w oknie **stos wywołań** to pierwsze wyszukiwanie wykonywanych działań. Możesz kliknąć dwukrotnie wpis, aby ustawić fokus w wybranym działaniu.

- **Wątki**: zawiera identyfikator wystąpienia wystąpienia przepływu pracy, które jest debugowane.

  Program Visual Studio dla Windows Workflow Foundation nie obsługuje następujących funkcji debugowania:

- Warunkowe punkty przerwania na powierzchni projektanta.

- QuickWatch.

- Ustaw następną instrukcję.

- Uruchom do kursora.

- Edytuj i Kontynuuj.

- Debugowanie just in Time.

- Debugowanie w trybie mieszanym.

## <a name="in-this-section"></a>W tej sekcji
 [Wywoływanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Wyłączanie debugera programu Visual Studio dla programu Windows Workflow Foundation (starsza wersja)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Instrukcje: Debugowanie przepływów pracy opartych na programie ASP.NET (starsza wersja)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Instrukcje: Ustawianie punktów przerwania w przepływach pracy (starsza wersja)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Debugowanie przepływów pracy ze zdalnego komputera (starsza wersja)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Opcje debugowania wykonywania krokowego (starsza wersja)](../workflow-designer/debug-stepping-options-legacy.md)

 [Instrukcje: Opcja zmiany debugowania krokowego (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)