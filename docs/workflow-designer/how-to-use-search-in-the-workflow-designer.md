---
title: 'Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 52adbded9f570689cd5749cc620ca8f74222e308
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854675"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy

W celu ułatwienia tworzenia większych i bardziej skomplikowanych przepływów pracy, można wyszukać w Projektancie przepływu pracy, aby znaleźć elementy według słów kluczowych. Należy pamiętać, że projektant nie obsługuje Zastąp.

## <a name="quick-find"></a>Szybkie wyszukiwanie

Szybkiego wyszukiwania umożliwia znalezienie następujące w Projektancie:

-   Właściwości <xref:System.Activities.Activity> obiektów <xref:System.Activities.Statements.FlowNode> obiektów <xref:System.Activities.Statements.State> obiektów, przejścia i inne elementy niestandardowe sterowanie przepływem.

-   Zmienne

-   Argumenty

-   Wyrażenia

### <a name="use-quick-find"></a>Zastosowanie szybkiego wyszukiwania

1. Otwórz projektanta przepływów pracy naciśnij **Ctrl + F**, lub wybierz **Edytuj** > **Znajdź i Zamień** > **szybkie znajdowanie**.

2. Wprowadź wyszukiwany termin do **Znajdź** polu tekstowym i kliknij przycisk **Znajdź następny**.

3. Termin wyszukiwania znajduje się w bieżącym przepływu pracy. Na poniższej ilustracji przedstawiono wyświetlana nazwa działania znajdujących się w Projektancie:

   ![Wynik wyszukiwania w Projektancie przepływu pracy](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Znajdź w plikach

Znajdź w plikach lokalizuje ciągów w pliki przepływu pracy, w tym plików XAML.

### <a name="use-find-in-files"></a>Za pomocą narzędzia Znajdź w plikach

1.  W programie Visual Studio, naciśnij klawisz **Ctrl**+**Shift**+**F**, lub wybierz **Edytuj**  >   **Znajdź i Zamień** > **Znajdź w plikach**.

2.  Wprowadź szukany element do **Znajdź** polu tekstowym i kliknij przycisk **Znajdź wszystkie**.

3.  Wynik wyszukiwania jest wyświetlany w **Znajdź wynik** widoku. Dwukrotne kliknięcie elementu wyniku powoduje przejście do działania, który zawiera dopasowanie w Projektancie przepływu pracy.