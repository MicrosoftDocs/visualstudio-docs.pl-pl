---
title: Opcje krokowe debugowania (starsza wersja) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656878"
---
# <a name="debug-stepping-options-legacy"></a>Opcje debugowania wykonywania krokowego (starsza wersja)
W tym temacie opisano sposób debugowania [!INCLUDE[wf](../includes/wf-md.md)] aplikacji, które mają współbieżne działania w starszej wersji [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Użyj starszej wersji, [!INCLUDE[wfd2](../includes/wfd2-md.md)] gdy musisz być celem [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Podczas debugowania starszych działań, które są wykonywane współbieżnie, takich jak **działaniu ParallelActivity** lub **ConditionedActivityGroup**, można użyć jednej z poniższych dwóch opcji, aby krokowo przekroczyć swój kod.

- **Przechodzenie do gałęzi.** Ten tryb wykonywania krok po kroku umożliwia przechodzenie między konkretną gałęzią działania złożonego, takiego jak **działaniu ParallelActivity** lub **ConditionalActivityGroup** . Gdy ta opcja jest używana do debugowania, nie należy zauważyć, że zmiana w kontroli występuje ze względu na współbieżne wykonywanie innych działań w przepływie pracy. Debuger wykonuje tylko kroki wykonywane przez działania w obecnie wybranej gałęzi, podczas gdy inne działania w przepływie pracy mogą być wykonywane współbieżnie. Na przykład domyślnie gałąź z lewej strony w działaniu **działaniu ParallelActivity** i pierwsze działanie podrzędne działania **ConditionedActivityGroup** jest używany do wykonywania kroków. Jeśli użytkownik chce debugować wszystkie inne gałęzie lub działania podrzędne, należy umieścić w niej jawny punkt przerwania. W przypadku wyzwolenia punktu przerwania kontynuuje wykonywanie kroków w tej gałęzi.

- **Krokowe wystąpienie.** Ten tryb wykonywania krok po kroku umożliwia przechodzenie i debugowanie współbieżnie wykonywanych działań w przepływie pracy. Po wybraniu tej opcji można zauważyć, że zmiana w kontroli odbywa się, gdy jednocześnie wykonywane są działania wykonywane w ramach przepływu pracy.

  Domyślnie opcja wykonywania gałęzi jest zaznaczona, a użytkownicy mogą przełączać się między tymi dwiema opcjami podczas debugowania starszego przepływu pracy.

  Podczas debugowania przepływów pracy starszego stanu nie należy wybierać opcji krokowe wystąpienie.

## <a name="see-also"></a>Zobacz też
 [Debugowanie starszych przepływów pracy](../workflow-designer/debugging-legacy-workflows.md) [: Zmiana opcji stopniowego debugowania (starsza wersja)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)