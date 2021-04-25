---
title: Debugowanie zarządzanego zrzutu pamięci za pomocą analizatorów diagnostycznych .NET | Microsoft Docs
description: Dowiedz się, jak używać Visual Studio diagnostyki .NET do analizowania zarządzanego zrzutu pamięci
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2021
ms.locfileid: "107952918"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>Jak debugować zarządzany zrzut pamięci za pomocą analizatorów diagnostycznych .NET



W tym samouczku wykonasz następujące czynności:

> [!div class="checklist"]
> * Otwieranie zrzutu pamięci
> * Wybieranie i wykonywanie analizatorów względem zrzutu
> * Przeglądanie wyników analizatorów
> * Przechodzenie do problematycznego kodu


W przykładzie opisanym w tym artykule należy pamiętać, że aplikacja nie odpowiada na żądania w terminowy sposób. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Otwieranie zrzutu pamięci w Visual Studio

1. Otwórz zrzut pamięci w programie Visual Studio za pomocą polecenia menu Otwórz > otwórz plik **>** i wybierz zrzut pamięci.

1. Na stronie Podsumowanie zrzutu pamięci zwróć uwagę na nową **akcję o** **nazwie Uruchom analizę diagnostyczną**.

   ![Akcja — analiza diagnostyki](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Wybierz tę akcję, aby uruchomić debuger i otworzyć nową stronę **Analiza** diagnostyczna z listą dostępnych opcji analizatora uporządkowaną według podstawowego objawu.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Wybieranie i wykonywanie analizatorów względem zrzutu

Aby zbadać te objawy, w obszarze Czas odpowiedzi procesu są dostępne najlepsze **opcje,** ponieważ najlepiej pasuje do problemu w tym przykładzie.

   ![Wybieranie analizatorów diagnostycznych](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Kliknij przycisk **Analizuj,** aby rozpocząć proces badania 

1. Analizator przedstawi wyniki na podstawie kombinacji informacji o procesie i danych CLR przechwyconych w zrzucie pamięci.
 
## <a name="review-the-results-of-the-analyzers"></a>Przeglądanie wyników analizatorów

1. W tym przypadku analizator znalazł dwa błędy. Wybierz wynik analizatora, aby wyświetlić podsumowanie **analizy** i sugerowane **korygowanie.**

   ![Wyniki analizatorów diagnostycznych](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. W **podsumowaniu analizy** stwierdzono, że "w puli wątków CLR występuje zator". Te informacje sugerują, że clr aktualnie używa wszystkich dostępnych wątków puli wątków, co oznacza, że usługa nie może odpowiadać na żadne nowe żądania, dopóki wątek nie zostanie zwolniony.

    > [!NOTE] 
    > Korygowanie **w** tym przypadku to "Nie czekaj synchronicznie na monitory, zdarzenia, zadanie lub inne obiekty, które mogą blokować wątek. Sprawdź, czy możesz zaktualizować metodę tak, aby był asynchroniczna".

## <a name="navigating-to-the-problematic-code"></a>Przechodzenie do problematycznego kodu

Następnym zadaniem jest znalezienie tego problematycznego kodu.

1. Kliknięcie linku **Pokaż stos wywołań** Visual Studio natychmiast przełączy się na wątki, które wykazują to zachowanie.

1. W **oknie Stos** wywołań będą wyświetlane metody, które mogą potencjalnie szybko odróżnić kod (SyncOverAsyncExmple. ) od kodu struktury *(System.*).

   ![Linki analizatorów diagnostycznych do stosu wywołań](../debugger/media/diagnostic-analyzer-call-stack.png)

1. Każda ramka stosu wywołań odpowiada metodzie i dwukrotne kliknięcie ramek stosu Visual Studio przejście do kodu, który prowadzi bezpośrednio do tego scenariusza w tym wątku.

1. W tym przykładzie nie ma symboli ani  kodu, jednak na stronie Symbole nie załadowane można wybrać opcję **[Dekompiluj kod źródłowy.](../debugger/decompilation.md)**

   ![Dekompilacji](../debugger/media/diagnostic-analyzer-decompilation.png)

1. W poniższym zdekompilowanych źródłach jest oczywiste, że asynchroniczne zadanie (ConsumeThreadPoolThread) wywołują synchroniczną funkcję blokowania.

    > [!NOTE]  
    > Metoda "DoSomething()", która zawiera metodę WaitHandle.WaitOne, która blokuje bieżący wątek puli wątków do momentu otrzymania sygnału.

   Aby poprawić czas odpowiedzi aplikacji, należy usunąć blokujący kod synchroniczny ze wszystkich kontekstów asynchronicznych.

   ![Analizowanie dekompilowanych kodu](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Zobacz też

* [Używanie plików zrzutu w debugerze](../debugger/using-dump-files.md)
* [Generowanie kodu źródłowego z zestawów .NET podczas debugowania](../debugger/decompilation.md)
* [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
