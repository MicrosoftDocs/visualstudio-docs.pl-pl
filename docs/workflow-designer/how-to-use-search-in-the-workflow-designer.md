---
title: 'Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy'
description: Dowiedz się, jak wyszukiwać w Projektant przepływu pracy, aby znaleźć elementy według słowa kluczowego, dzięki czemu można ułatwić tworzenie większych, bardziej złożonych przepływów pracy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb30d4846c24638f87989d2a7a716df06b0523b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894117"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy

Aby ułatwić tworzenie większych, bardziej złożonych przepływów pracy, można wyszukiwać w Projektant przepływu pracy, aby znaleźć elementy według słowa kluczowego. Należy pamiętać, że projektant nie obsługuje zastępowania.

## <a name="quick-find"></a>Szybkie wyszukiwanie

Szybkie znajdowanie umożliwia znalezienie następujących danych w projektancie:

- Właściwości <xref:System.Activities.Activity> obiektów, <xref:System.Activities.Statements.FlowNode> obiektów, <xref:System.Activities.Statements.State> obiektów, przejść i innych niestandardowych elementów sterowania przepływem.

- Zmienne

- Argumenty

- Wyrażenia

### <a name="use-quick-find"></a>Użyj szybkiego wyszukiwania

1. Po otwarciu projektanta przepływu pracy naciśnij **klawisze CTRL + F** lub wybierz pozycję **Edytuj**  >  **Znajdź i Zamień**  >  **szybkie znajdowanie**.

2. Wprowadź wyszukiwany termin w polu **Znajdź** element TextBox i kliknij przycisk **Znajdź dalej**.

3. Termin wyszukiwania znajduje się w bieżącym przepływie pracy. Na poniższej ilustracji przedstawiono nazwę wyświetlaną działania znajdującą się w projektancie:

   ![Wyniki wyszukiwania w Projektant przepływu pracy](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Znajdź w plikach

Znajdź w plikach lokalizuje ciągi w plikach przepływu pracy, w tym pliki XAML.

### <a name="use-find-in-files"></a>Użyj Znajdź w plikach

1. W programie Visual Studio naciśnij klawisz **Ctrl** + **SHIFT** + **F** lub wybierz pozycję **Edytuj**  >  **Znajdź i Zamień**  >  **Znajdź w plikach**.

2. Wprowadź element wyszukiwania do pola tekstowego **Znajdź co** i kliknij przycisk **Znajdź wszystko**.

3. Wyniki wyszukiwania są wyświetlane w widoku **wyników wyszukiwania** . Dwukrotne kliknięcie elementu wyniku powoduje przejście do działania, które zawiera dopasowanie w Projektancie przepływu pracy.