---
title: 'Instrukcje: korzystanie z okna wątków | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824256"
---
# <a name="how-to-use-the-threads-window"></a>Porady: korzystanie z okna wątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W oknie **wątki** można analizować i współpracować z wątkami w debugowanej aplikacji.  
  
 Okno **wątki** zawiera tabelę, w której każdy wiersz reprezentuje wątek w aplikacji. Domyślnie w tabeli znajduje się lista wszystkich wątków w aplikacji, ale można filtrować listę, aby pokazać tylko te wątki, które Cię interesują. Każda kolumna zawiera różne rodzaje informacji. Możesz również ukryć niektóre kolumny. W przypadku wyświetlenia wszystkich kolumn wyświetlane są następujące informacje od lewej do prawej:  
  
- Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę. Aby uzyskać informacje o sposobie oflagowania wątku, zobacz [How to: flag i unflaging](../debugger/how-to-flag-and-unflag-threads.md)Threads.  
  
- Kolumna aktywnego wątku, gdzie żółta strzałka wskazuje aktywny wątek. Kontur strzałki wskazuje wątek, w którym wykonywanie zostało zerwane w debugerze.  
  
- Kolumna **ID** , która zawiera numer identyfikacyjny dla każdego wątku.  
  
- Kolumna **Identyfikator zarządzany** , która zawiera zarządzane numery identyfikacyjne dla zarządzanych wątków.  
  
- Kolumna **Kategoria** , która klasyfikuje wątki jako wątki interfejsu użytkownika, procedury obsługi zdalnego wywoływania procedur lub wątków roboczych. Specjalna kategoria identyfikuje główny wątek aplikacji.  
  
- Kolumna **name** , która identyfikuje każdy wątek według nazwy, jeśli ma jeden, lub jako \<No Name> .  
  
- Kolumna **lokalizacji** , która pokazuje, gdzie działa wątek. Można rozwinąć tę lokalizację, aby pokazać pełny stos wywołań wątku.  
  
- Kolumna **priorytet** , która zawiera priorytet lub pierwszeństwo, które system przypisał do każdego wątku.  
  
- Kolumna **maska koligacji** , która jest zaawansowaną kolumną, która jest zwykle ukryta. W tej kolumnie jest wyświetlana maska koligacji procesorów dla każdego wątku. W systemie wieloprocesorowym maska koligacji określa procesory, w których można uruchomić wątek.  
  
- Kolumna **Liczba wstrzymanych** , która zawiera liczbę wstrzymanych. Ta liczba określa, czy można uruchomić wątek. Aby uzyskać wyjaśnienie liczby wstrzymanych, zobacz sekcję "zamrażanie i odblokowywanie wątków" w dalszej części tego tematu.  
  
- Kolumna **Nazwa procesu** , która zawiera proces, do którego należy każdy wątek. Ta kolumna może być przydatna podczas debugowania wielu procesów, ale zazwyczaj jest ukryta.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Aby wyświetlić okno wątki w trybie przerwania lub w trybie uruchamiania  
  
- W menu **debugowanie** wskaż polecenie **Windows**, a następnie kliknij pozycję **wątki**.  
  
### <a name="to-display-or-hide-a-column"></a>Aby wyświetlić lub ukryć kolumnę  
  
- Na pasku narzędzi u góry okna **wątki** kliknij pozycję **kolumny**, a następnie wybierz lub wyczyść nazwę kolumny, która ma być wyświetlana lub ukryta.  
  
### <a name="to-switch-the-active-thread"></a>Aby przełączyć aktywny wątek  
  
- Wykonaj jedną z następujących czynności:  
  
  - Kliknij dwukrotnie dowolny wątek.  

  - Kliknij prawym przyciskiem myszy wątek i kliknij polecenie **Przełącz do wątku**.  

    Żółta strzałka pojawia się obok nowego aktywnego wątku. Szary kontur strzałki wskazuje wątek, w którym wykonywanie zostało zerwane w debugerze.  
  
## <a name="grouping-and-sorting-threads"></a>Grupowanie i sortowanie wątków  
 Gdy grupujesz wątki, w tabeli dla każdej grupy pojawi się nagłówek. Nagłówek zawiera opis grupy, taki jak "wątek roboczy" lub "wątki nieoflagowane" oraz kontrolka drzewa. Wątki elementów członkowskich każdej grupy są wyświetlane pod nagłówkiem grupy. Aby ukryć wątki elementów członkowskich dla grupy, można zwinąć grupę przy użyciu kontrolki drzewa.  
  
 Ponieważ grupowanie ma pierwszeństwo przed sortowaniem, można grupować wątki według kategorii, na przykład, a następnie sortować je według identyfikatora w każdej kategorii.  
  
#### <a name="to-sort-threads"></a>Aby posortować wątki  
  
1. Na pasku narzędzi u góry okna **wątki** kliknij przycisk w górnej części dowolnej kolumny.  
  
     Wątki są teraz sortowane według wartości w tej kolumnie.  
  
2. Jeśli chcesz odwrócić porządek sortowania, kliknij ten sam przycisk ponownie.  
  
     Wątki, które pojawiły się w górnej części listy, teraz pojawiają się u dołu.  
  
#### <a name="to-group-threads"></a>Do grup wątków  
  
- Na pasku narzędzi okna **wątki** kliknij listę **Grupuj według** , a następnie kliknij kryteria, według których chcesz grupować wątki.  
  
#### <a name="to-sort-threads-within-groups"></a>Aby posortować wątki w grupach  
  
1. Na pasku narzędzi u góry okna **wątki** kliknij listę **Grupuj według** , a następnie kliknij kryteria, według których chcesz grupować wątki.  
  
2. W oknie **wątki** kliknij przycisk w górnej części dowolnej kolumny.  
  
     Wątki są teraz sortowane według wartości w tej kolumnie.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Aby rozwinąć lub zwinąć wszystkie grupy  
  
- Na pasku narzędzi u góry okna **wątki** kliknij opcję **Rozwiń grupy** lub **Zwiń grupy**.  
  
## <a name="searching-for-specific-threads"></a>Wyszukiwanie określonych wątków  
 W programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] można wyszukać wątki pasujące do określonego ciągu. Podczas wyszukiwania wątków w oknie **wątki** , w oknie są wyświetlane wszystkie wątki, które pasują do ciągu wyszukiwania w dowolnej kolumnie. Te informacje obejmują lokalizację wątku wyświetlaną w górnej części stosu wywołań w kolumnie **Lokalizacja** . Domyślnie jednak cały stos wywołań nie jest przeszukiwany.  
  
#### <a name="to-search-for-specific-threads"></a>Aby wyszukać określone wątki  
  
- Na pasku narzędzi u góry okna **wątki** przejdź do pola **wyszukiwania** , a następnie:  
  
  - Wpisz ciąg wyszukiwania, a następnie naciśnij klawisz ENTER.  

    \- oraz  

  - Kliknij listę rozwijaną obok pola **wyszukiwania** i wybierz ciąg wyszukiwania z poprzedniego wyszukiwania.  
  
- Obowiązkowe Aby dołączyć pełny stos wywołań w wyszukiwaniu, wybierz pozycję **Wyszukaj stos wywołań**.  
  
## <a name="freezing-and-thawing-threads"></a>Zamrażanie i odblokowywanie wątków  
 W przypadku zablokowania wątku system nie uruchomi wykonywania wątku, nawet jeśli dostępne są zasoby.  
  
 W kodzie natywnym można wstrzymywać lub wznawiać wątki przez wywoływanie funkcji systemu Windows `SuspendThread` i `ResumeThread` lub funkcji MFC [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) i [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Jeśli wywołasz `SuspendThread` lub `ResumeThread` , zmienisz *liczbę wstrzymania*, która pojawia się w oknie **wątki** . Jednak w przypadku zablokowania lub odblokowania wątku macierzystego nie jest zmieniana liczba wstrzymań. W kodzie natywnym wątek nie może zostać wykonany, chyba że zostanie odmrożony i ma wstrzymaną liczbę zero.  
  
 W kodzie zarządzanym, zamrażanie lub odblokowywanie wątku zmienia liczbę wstrzymania. W kodzie zarządzanym wątek zablokowany ma wstrzymaną liczbę 1. W kodzie natywnym wątek mrożony ma wstrzymaną liczbę 0, chyba że wątek został zawieszony przez `SuspendThread` wywołanie.  
  
> [!NOTE]
> Podczas debugowania wywołania z kodu natywnego do kodu zarządzanego, kod zarządzany jest uruchamiany w tym samym wątku fizycznym co kod natywny, który go wywołał. Zawieszanie lub zamrażanie wątku natywnego blokuje również kod zarządzany.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Aby zablokować lub odblokować wykonywanie wątku  
  
- Na pasku narzędzi u góry okna **wątki** kliknij pozycję **Zablokuj wątki** lub Odblokuj **wątki**.  
  
     Ta akcja ma wpływ tylko na wątki, które są wybrane w oknie **wątki** .  
  
## <a name="displaying-flagged-threads"></a>Wyświetlanie oflagowanych wątków  
 Można oflagować wątek, który ma dawać szczególną uwagę, poprzez oznaczenie go ikoną w oknie **wątki** . Aby uzyskać więcej informacji, zobacz [How to: flag i unflaging Threads](../debugger/how-to-flag-and-unflag-threads.md). W oknie wątki można wyświetlić wszystkie wątki lub tylko Oflagowane wątki.  
  
#### <a name="to-display-only-flagged-threads"></a>Aby wyświetlić tylko Oflagowane wątki  
  
- Wybierz przycisk flagi w lewym górnym rogu okna **wątki** .  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Wyświetlanie stosów wywołań wątków i przełączanie między ramkami  
 W programie wielowątkowym każdy wątek ma własny stos wywołań. Okno **wątki** zapewnia wygodny sposób wyświetlania tych stosów.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Aby wyświetlić stos wywołań wątku  
  
- W kolumnie **Lokalizacja** kliknij odwrócony trójkąt obok lokalizacji wątku.  
  
     Lokalizacja rozszerza się, aby pokazać stos wywołań wątku.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Aby wyświetlić lub zwinąć stosy wywołań wszystkich wątków  
  
- Na pasku narzędzi u góry okna **wątki** kliknij pozycję **Rozwiń stosy wywołań** lub **Zwiń stosy wywołań**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Przewodnik: debugowanie aplikacji wielowątkowych](../debugger/walkthrough-debugging-a-multithreaded-application.md)
