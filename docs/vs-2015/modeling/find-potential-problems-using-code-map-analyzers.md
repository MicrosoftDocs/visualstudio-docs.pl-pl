---
title: Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6656ae4e5dc4acc0cb95b40fbb3eaa10b473d9e1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802398"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uruchomić analizatory na mapach kodu, aby ułatwić identyfikację kodu, który może być zbyt skomplikowana, lub który może być konieczne poprawy jakości obsługi. Na przykład można użyć tych analizatory:  
  
|**Aby znaleźć kod, który posiada**|**Sprawdź tych obszarów, aby zobaczyć, czy**|  
|-------------------------------|--------------------------------------------|  
|Pętle lub zależności cykliczne|Możesz uprościć i należy wziąć pod uwagę, czy możesz przerwać tych cykli.|  
|Zbyt wiele zależności|Działają one zbyt wiele funkcji lub określić wpływ zmiany na tych obszarów. Mapy kodu z dobrze sformułowany pokaże minimalnej liczby zależności. Aby ułatwić kod obsługi, zmienianie, przetestować i ponownie użyć, należy rozważyć, czy Refaktoryzacja tych obszarów, aby wyraźniej zdefiniowano lub tego, czy można scalać kod, który wykonuje podobne funkcje.|  
|Brak zależności|Jest to konieczne, lub czy należy usunąć ten kod.|  
  
## <a name="analyze-code-maps"></a>Analizowanie mapy kodu  
  
1. Na pasku narzędzi mapy wybierz **układ**, **analizatory**, a następnie analizatora, które chcesz uruchomić:  
  
   |**Analyzer**|**Do identyfikowania węzłów,**|  
   |------------------|--------------------------------|  
   |**Analizator odwołań cyklicznych**|Mają zależności cykliczne na siebie nawzajem. **Uwaga:** zależności cykliczne, które znajdują się w **ogólne** grupy nie są wyświetlane na mapie, po rozwinięciu grupy.|  
   |**Znajdź analizator koncentratory**|Znajdują się w 25% najlepszych wysoce połączone węzły<br /><br /> **Aby ukryć wszystkie węzły na mapie**<br /><br /> -Otwórz menu skrótów dla mapy, wybierz **zaawansowane**, **wybierz**, **Ukryj niezaznaczone**.<br />     Mapa ukrywa węzły niezaznaczone i analizatora identyfikuje nowe węzły rolę piast.|  
   |**Analizator węzłów bez odwołań**|Nie ma odwołań z innych węzłów. **Uwaga:** Sprawdź każdy z tych przypadków przed przy założeniu, że kod nie jest używany. Niektóre zależności, np. zależności XAML i środowiska wykonawczego zależności nie można odnaleźć statycznie w kodzie.|  
  
   Analizatorów mapy kodu będzie kontynuowane po ich zastosowania. W przypadku zmiany mapy analizatorów zastosowany zostanie automatycznie ponownie przetworzyć zaktualizowano mapę. Aby zatrzymać analizatora, na pasku narzędzi mapy, wybierz opcję **układ**, **analizatory**. Wyłącz wybrane analizatora.  
  
> [!TIP]
>  W przypadku bardzo dużych mapy uruchomiony analizator może spowodować wyjątek braku pamięci. Jeśli ten problem wystąpi, Edytuj mapę, aby zmniejszyć jego zakres lub wygenerować mniejszych, a następnie uruchom analizator.  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)   
 [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)



