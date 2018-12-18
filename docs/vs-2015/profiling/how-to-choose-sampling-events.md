---
title: 'Porady: Wybieranie zdarzeń próbkowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.sampling
helpviewer_keywords:
- clock cycles sample event
- sample events, choosing
- profiling tools, sample events
- page faults sample event
- system calls sample event
- performance counter sample event
- performance tools, sample events
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96bf47c6bfc28e0939f6feb9fd7999e898c042a1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734513"
---
# <a name="how-to-choose-sampling-events"></a>Porady: wybieranie zdarzeń pobierania próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools zbiera dane dotyczące wydajności w odstępach czasu, który jest określony jako liczba cykli procesora, które są używane przez profilowany proces. Domyślna liczba cykli interwału jest 10 000 000, czyli około 0,01 sekund na 1 komputerze GH. Można zmienić liczbę cykli w interwale, i możesz zmienić zdarzenie próbkowania. Dostępne są następujące przykładowe zdarzenia:  
  
-   Cykle zegara — w przypadku problemów z Procesora CPU.  
  
-   Błędy strony — w przypadku problemów związanych z pamięcią.  
  
-   Wywołania systemowe — w przypadku problemów I dotyczących wejścia/wyjścia.  
  
-   Licznik wydajności - liczniki procesora CPU dla problemów z wydajnością niskiego poziomu.  
  
> [!IMPORTANT]
>  Przypadku zbierania danych pamięci .NET (alokacje czasów istnienia obiektów i/lub) przy użyciu metody próbkowania zdarzeń próbkowania wszystkie określone przez użytkownika są ignorowane i alokacje odpowiedniej ilości pamięci i/lub zdarzenia odzyskiwania pamięci, które są używane do zbierania danych.  
  
### <a name="to-select-a-sample-event"></a>Aby wybrać zdarzenie próbkowania  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **próbkowania** właściwości.  
  
3.  Z **zdarzenie próbkowania** listy rozwijanej wybierz zdarzenie próbkowania, którego chcesz użyć do profilu aplikacji.  
  
    > [!NOTE]
    >  **Dostępnych liczników wydajności** są włączone tylko wtedy, gdy wybierzesz **licznika wydajności** z **zdarzenie próbkowania** listy rozwijanej.  
  
4.  Jeśli wybierzesz **licznika wydajności**, Wybieranie określonego licznika Procesora z **dostępnych liczników wydajności** kontrolki widoku drzewa.  
  
    -   Liczniki **zdarzenia przenośne** węzła są dostępne dla wszystkich typów procesorów.  
  
    -   Liczniki **zdarzenia platformy** węzeł specyficznych dla procesora na bieżącym komputerze i mogą nie być dostępne dla innych typów procesorów.  
  
5.  Po wybraniu zdarzenie próbkowania, domyślna wartość interwału próbkowania jest wyświetlana w **interwał próbkowania** pola tekstowego. Jeśli to konieczne, można wprowadzić wartość, która ma w polu tekstowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [CPU i liczniki Windows](../profiling/cpu-and-windows-counters.md)   
 [Z wartościami danych próbkowania opis](../profiling/understanding-sampling-data-values.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)



