---
title: 'Instrukcje: W Projektancie przepływu pracy przy użyciu funkcji Wyszukaj | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1d62f1936e4cf424bde526301210e61f38e5b767
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60038808"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Instrukcje: Używanie funkcji wyszukiwania w Projektancie przepływu pracy
W celu ułatwienia tworzenia większych i bardziej skomplikowanych przepływów pracy, wyszukiwanie może służyć w Projektancie przepływu pracy można znaleźć elementy według słów kluczowych. Należy pamiętać, że projektant nie obsługuje Zastąp. W Projektancie wyszukiwania zawiera następujące:  
  
## <a name="quick-find"></a>Szybkie wyszukiwanie  
 W Projektancie szybkiego wyszukiwania zawiera następujące:  
  
- Właściwości <xref:System.Activities.Activity> obiektów <xref:System.Activities.Statements.FlowNode> obiektów <xref:System.Activities.Statements.State> obiektów, przejścia i inne elementy niestandardowe sterowanie przepływem.  
  
- Zmienne  
  
- Argumenty  
  
- Wyrażenia  
  
#### <a name="using-quick-find"></a>Za pomocą szybkiego wyszukiwania  
  
1. Otwórz projektanta przepływów pracy naciśnij **Ctrl + F**, lub wybierz **Edytuj**, **Znajdź i Zamień**, **szybkie znajdowanie**.  
  
2. Wprowadź wyszukiwany termin do **Znajdź** polu tekstowym i kliknij przycisk **Znajdź następny**.  
  
3. Wyszukiwany termin będzie znajdować się w bieżącej przepływu pracy. Poniższy zrzut ekranu przedstawia wyświetlana nazwa działania znajdujących się w projektancie.  
  
     ![Wynik wyszukiwania w Projektancie przepływu pracy](../workflow-designer/media/designersearch.png "DesignerSearch")  
  
## <a name="find-in-files"></a>Znajdź w plikach  
 Korzystania z funkcji znajdowania w plikach zlokalizować ciągi w plikach przepływu pracy, w tym plików XAML.  
  
#### <a name="using-find-in-files"></a>Korzystania z funkcji znajdowania w plikach  
  
1. W programie Visual Studio, naciśnij klawisz **Ctrl + Shift + F**, lub wybierz **Edytuj**, **Znajdź i Zamień**, **Znajdź w plikach**  
  
2. Wprowadź szukany element do **Znajdź** polu tekstowym i kliknij przycisk **Znajdź wszystkie**  
  
3. Wynik wyszukiwania zostaną wyświetlone w [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **Znajdź wynik** widoku. Dwukrotne kliknięcie elementu wynik spowoduje przejście do działania, które zawiera dopasowanie w Projektancie przepływu pracy.