---
title: 'Instrukcje: Wymuszanie kodu łatwego w utrzymaniu za pomocą zasad analizy kodu ewidencjonowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5676bfaabb20ebf6dabea7bae66527d17891b362
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753020"
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Instrukcje: Wymuszanie kodu łatwego w utrzymaniu za pomocą zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Deweloperzy mogą używać narzędzia metryki kodu do mierzenie złożoności i łatwości konserwacji kodu, ale ich nie można wywołać metryki kodu jako części zasad ewidencjonowania. Jednak zespół można włączyć reguły analizy kodu Sprawdź zgodność kodu z normami metryki kodu i Wymuszanie reguł za pomocą zasad ewidencjonowania. Aby uzyskać więcej informacji na temat metryki kodu, zobacz [wartości metryk kodów](../code-quality/code-metrics-values.md).  
  
 Deweloperzy mogą włączać głębokość dziedziczenia, sprzężenia klas, indeks łatwości utrzymania i złożoności wymuszanie kodu łatwego w utrzymaniu za pomocą zasad ewidencjonowania analizy kodu. Wszystkie cztery te zasady znajdują się w kategorii "Reguły utrzymania kodu" w edytorze zasad analizy kodu.  
  
 Administratorzy wersji kontrola dla [!INCLUDE[esprfound](../includes/esprfound-md.md)] można dodać reguły utrzymania kodu analizy kodu do wymagań zasad ewidencjonowania. Te ewidencjonowania zasadami wymagających deweloperów uruchomić analizę kodu na podstawie tych reguł zmian przed zainicjowaniem ewidencjonowania.  
  
### <a name="to-open-the-code-analysis-policy-editor"></a>Aby otworzyć Edytor zasad analizy kodu  
  
1.  W **Team Explorer**, kliknij prawym przyciskiem myszy projekt zespołowy, kliknij przycisk **ustawienia projektu zespołowego**, a następnie kliknij przycisk **kontroli źródła**.  
  
     **Kontroli źródła** pojawi się okno dialogowe.  
  
2.  Na **zasad ewidencjonowania** kartę, a następnie kliknij przycisk **Dodaj**.  
  
     **Dodaj zasady ewidencjonowania** pojawi się okno dialogowe.  
  
3.  W **zasad ewidencjonowania** listy wybierz **analizy kodu** pole wyboru, a następnie kliknij przycisk **OK**.  
  
     **Edytor zasad analizy kodu** pojawi się okno dialogowe.  
  
### <a name="to-enable-code-analysis-maintainability-rules"></a>Aby włączyć reguły utrzymania kodu analizy kodu  
  
1.  W **Edytor zasad analizy kodu** dialogowego **ustawienia reguły**, rozwiń węzeł **reguły utrzymania kodu** węzła.  
  
2.  Zaznacz pola wyboru dla następujących reguł:  
  
    -   Głębokość dziedziczenia: **CA1501 AvoidExcessiveInheritance** -progu: Ostrzeżenie o więcej niż 5 poziomów w głąb  
  
    -   Złożoność: **CA1502 AvoidExcessiveComplexity** -progu: Ostrzeżenie na więcej niż 25  
  
    -   Indeks łatwości utrzymania: **CA1505 AvoidUnmaintainableCode** - Threshold: Ostrzeżenie w mniej niż 20  
  
    -   Sprzężenia klas: **CA1506 AvoidExcessiveClassCoupling** - Threshold: Ostrzeżenie na więcej niż 80 dla klasy i więcej niż 30 dla metody  
  
    -   Ponadto naruszenie reguły, aby uniemożliwić kompilacji, wybierz **Traktuj ostrzeżenie jako błąd** pole wyboru obok opis reguły.  
  
3.  Kliknij przycisk **OK**. Nowe zasady ewidencjonowania dotyczy teraz przyszłych zaewidencjonowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wartości metryk kodów](../code-quality/code-metrics-values.md)   
 [Tworzenie zasad zaewidencjonowania analizy kodu i korzystanie z nich](../code-quality/creating-and-using-code-analysis-check-in-policies.md)
