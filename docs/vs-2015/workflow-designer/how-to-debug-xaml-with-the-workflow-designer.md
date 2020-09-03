---
title: 'Instrukcje: Debugowanie kodu XAML przy użyciu Projektant przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a696123551c24fd0d14fecde67826cf14f88826f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668652"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Instrukcje: Debugowanie kodu XAML za pomocą Projektanta przepływu pracy
Przepływy pracy są zdefiniowane w postaci języka XAML. Reprezentacja interfejsu użytkownika jest tworzona na podstawie drzewa XAML definiującego przepływ pracy. Środowisko debugowania jest podobne do debugowania przepływów pracy w programie [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Na przykład podczas debugowania XAML, okna lokalne, czujka i wątki działają tak samo, jak w przypadku [!INCLUDE[wfd2](../includes/wfd2-md.md)] debugowania. Ponadto widok stosu wywołań podczas debugowania XAML to hierarchiczny widok przepływu wykonywania przepływu pracy w oparciu o wiersz.

> [!NOTE]
> Jeśli kod XAML dla przepływu pracy znajduje się w tym samym zestawie co działania, część nazw klas nie jest uwzględniana. Bez tej części nazw klas (Activity) nie można załadować kodu XAML w czasie wykonywania. Nie zaleca się definiowania działań w tej samej przestrzeni nazw co projekt główny; w przeciwnym razie kod XAML będzie musiał być edytowany ręcznie po edycji w projektancie.

### <a name="to-debug-workflow-xaml"></a>Aby debugować kod XAML przepływu pracy

1. Otwórz przepływ pracy lub projekt działania w temacie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

2. Ustaw punkt przerwania działania lub działań, które chcesz debugować zgodnie z opisem w [instrukcje: ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Kliknij prawym przyciskiem myszy plik XAML, który zawiera definicję przepływu pracy, a następnie wybierz polecenie **Wyświetl kod**. Punkt przerwania jest wyświetlany w tym samym wierszu co Deklaracja elementu XAML działania, dla którego ustawisz punkt przerwania w widoku projektu.

4. Wywołaj debuger zgodnie z opisem w temacie [How to: Invoke The Workflow Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md).

5. Gdy wykonanie kodu osiągnie jeden z punktów przerwania, element XAML skojarzony z tym punktem przerwania zostanie wyróżniony. Aby przejść do następnego punktu przerwania, użyj klawisza **F10** lub **F11** .

## <a name="see-also"></a>Zobacz też
 [Instrukcje: ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [instrukcje: wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)