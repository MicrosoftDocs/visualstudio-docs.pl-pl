---
title: 'Instrukcje: korzystanie z wyszukiwania w Projektant przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659119"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy
Aby ułatwić tworzenie większych, bardziej złożonych przepływów pracy, wyszukiwanie może być używane w Projektant przepływu pracy do znajdowania elementów według słowa kluczowego. Należy pamiętać, że projektant nie obsługuje zastępowania. W projektancie znajdą się następujące elementy:

## <a name="quick-find"></a>Szybkie wyszukiwanie
 W projektancie znajdą się następujące elementy:

- Właściwości <xref:System.Activities.Activity> obiektów, <xref:System.Activities.Statements.FlowNode> obiektów, <xref:System.Activities.Statements.State> obiektów, przejść i innych niestandardowych elementów sterowania przepływem.

- Zmienne

- Argumenty

- Wyrażenia

#### <a name="using-quick-find"></a>Używanie szybkiego wyszukiwania

1. Po otwarciu projektanta przepływu pracy naciśnij **klawisze CTRL + F**lub wybierz pozycję **Edytuj**, **Znajdź i Zamień**, **szybkie znajdowanie**.

2. Wprowadź wyszukiwany termin w polu **Znajdź** element TextBox i kliknij przycisk **Znajdź dalej**.

3. Termin wyszukiwania będzie znajdować się w bieżącym przepływie pracy. Poniższy zrzut ekranu przedstawia nazwę wyświetlaną działania znajdującą się w projektancie.

     ![Wyniki wyszukiwania w Projektant przepływu pracy](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Znajdź w plikach
 Użycie Znajdź w plikach zlokalizuje ciągi w plikach przepływu pracy, w tym pliki XAML.

#### <a name="using-find-in-files"></a>Korzystanie z funkcji Znajdź w plikach

1. W programie Visual Studio naciśnij **klawisze Ctrl + Shift + F**lub wybierz pozycję **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**

2. Wprowadź element wyszukiwania do pola tekstowego **Znajdź co** i kliknij przycisk **Znajdź wszystko**

3. Wynik Znajdź zostanie wyświetlony w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] widoku **wyszukiwania wyników** . Dwukrotne kliknięcie elementu wynikowego spowoduje przejście do działania, które zawiera dopasowanie w Projektancie przepływu pracy.