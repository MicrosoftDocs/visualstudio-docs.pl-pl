---
title: Funkcje IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 73
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c41889e0e9d570ecdb415b6487c48c7c2b7c7c4
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847223"
---
# <a name="intellitrace-features"></a>Funkcje IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą IntelliTrace można rejestrować zdarzenia i metody wywołania aplikacji, co umożliwia badanie stanu (stos wywołań i wartości zmiennych lokalnych) w różnych punktach wykonywania. Po prostu Rozpocznij debugowanie w zwykły sposób — IntelliTrace jest domyślnie włączone i zobaczysz, że IntelliTrace informacje są rejestrowane w nowym oknie **Narzędzia diagnostyczne** na karcie **zdarzenia** . Wybierz zdarzenie, a następnie kliknij pozycję **Aktywuj debugowanie historyczne** , aby zobaczyć stos wywołań i lokalne zarejestrowane dla tego zdarzenia.  
  
 Aby zapoznać się z opisem krok po kroku, zobacz [Przewodnik: korzystanie z IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 Program IntelliTrace jest dostępny w wersji Visual Studio Enterprise, ale nie w wersjach Visual Studio Professional i Community.  
  
 Aby potwierdzić, że IntelliTrace jest włączona, Otwórz stronę opcje **Narzędzia/Opcje/IntelliTrace** . Opcja **Włącz IntelliTrace** powinna być domyślnie zaznaczona.  
  
> [!NOTE]
> Zakres wszystkich ustawień na stronie opcji **IntelliTrace** to program Visual Studio jako całość, a nie pojedyncze projekty lub rozwiązania. Zmiana tych ustawień dotyczy wszystkich wystąpień programu Visual Studio, wszystkich sesji debugowania i wszystkich projektów lub rozwiązań.  
  
## <a name="ChooseEvents"></a>Wybierz zdarzenia, które IntelliTrace rekordy  
 Możesz włączyć lub wyłączyć nagrywanie dla określonych zdarzeń IntelliTrace.  
  
 Jeśli debugujesz, Zatrzymaj debugowanie. Przejdź do pozycji **Narzędzia/Opcje/IntelliTrace/IntelliTrace**. Wybierz zdarzenia, które mają być rejestrowane przez IntelliTrace.  
  
## <a name="GoingFurther"></a>Zbierz zdarzenia IntelliTrace i informacje o wywołaniu  
 Ta funkcja nie jest domyślnie włączona, ale IntelliTrace może rejestrować wywołania metod wraz ze zdarzeniami. Aby włączyć zbieranie wywołań metod, przejdź do pozycji **Narzędzia/Opcje/IntelliTrace/ogólne**, a następnie wybierz pozycję **zdarzenia IntelliTrace i informacje o wywołaniu**.  
  
 Dzięki temu można zobaczyć historię stosu wywołań i przejść do tyłu i do przodu przez wywołania w kodzie. IntelliTrace rejestruje dane, takie jak nazwy metod, wejścia do metody i punkty wyjścia oraz pewne wartości parametrów i wartości zwracane.  
  
> [!TIP]
> Ta opcja nie jest domyślnie włączona, ponieważ zwiększa nakłady pracy. Nie tylko IntelliTrace muszą przechwycić każde wywołanie metody dla aplikacji, ale również musi zająć dużo większego zestawu danych, gdy jest on wyświetlany na ekranie lub utrwala go na dysku.  
>   
> Możesz zmniejszyć obciążenie wydajności, ograniczając listę zdarzeń, które IntelliTrace rekordy i utrzymując liczbę modułów, które są zbierane do minimum. Aby uzyskać więcej informacji, zobacz [kontrolowanie, jak dużo informacji o wywołaniu IntelliTrace rekordy](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Korzystanie z marginesu nawigacyjnego  
 Możesz użyć marginesu nawigacji, który pojawia się po lewej stronie okna kod. Jeśli nie widzisz marginesu nawigacyjnego, przejdź do pozycji **Narzędzia/Opcje/IntelliTrace/zaawansowane**i wybierz opcję **Wyświetl margines nawigacyjny w trybie debugowania**.  
  
 Margines nawigacyjny umożliwia przechodzenie do przodu i do tyłu przez wywołania metod i zdarzenia w trybie debugowania historycznego. Aby uzyskać więcej informacji na temat debugowania historycznego, zobacz [debugowanie historyczne](../debugger/historical-debugging.md). Zawiera kilka poleceń:  
  
|||  
|-|-|  
|**Ustaw tutaj kontekst debugera**|Ustaw kontekst debugowania na czas wywołania, gdzie się pojawi.<br /><br /> Ta ikona jest wyświetlana tylko na bieżącym stosie wywołań.|  
|**Wróć do witryny wywołania**|Przenieś wskaźnik i kontekst debugowania z powrotem do miejsca, w którym wywołano bieżącą funkcję.<br /><br /> W trybie debugowania na żywo to polecenie włącza debugowanie historyczne. Jeśli wrócisz do oryginalnego przerwania wykonywania, debugowanie historyczne jest wyłączone, a debugowanie na żywo jest włączone.|  
|**Przejdź do poprzedniego wywołania lub zdarzenia IntelliTrace**|Przenieś wskaźnik i kontekst debugowania z powrotem do poprzedniego wywołania lub zdarzenia.<br /><br /> W trybie debugowania na żywo to polecenie włącza debugowanie historyczne.|  
|**Wkrocz**|Wkrocz do aktualnie wybranej funkcji.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|  
|**Przejdź do następnego wywołania lub zdarzenia IntelliTrace**|Przenieś wskaźnik i kontekst debugowania do następnego wywołania lub zdarzenia, dla którego istnieją dane IntelliTrace.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|  
|**Przejdź do trybu na żywo**|Wróć do trybu debugowania na żywo.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Wyszukaj wiersz lub metodę w IntelliTrace  
 Metody wyszukiwania można wyszukiwać tylko wtedy, gdy zostały włączone informacje o wywołaniu metody. Historię IntelliTrace można wyszukiwać dla konkretnego wiersza lub metody. Podczas gdy wykonywanie debugera jest zatrzymane, kliknij prawym przyciskiem myszy wewnątrz treści funkcji, aby wyświetlić menu kontekstowe, a następnie kliknij opcję **Wyszukaj ten wiersz w IntelliTrace** lub **Wyszukaj tę metodę w IntelliTrace**.  
  
### <a name="ControlCallData"></a>Sterowanie ilością rekordów IntelliTrace informacji o wywołaniu  
 Domyślnie IntelliTrace rejestruje informacje dla wszystkich modułów używanych przez rozwiązanie. Możesz ustawić IntelliTrace, aby rejestrować informacje o wywołaniu tylko dla interesujących Cię modułów. W obszarze **Narzędzia/Opcje/IntelliTrace/moduły**można określić moduły do uwzględnienia lub moduły, które mają zostać wykluczone z IntelliTrace. IntelliTrace będzie zbierać tylko zdarzenia pochodzące z określonych modułów i wywołania metody, które wystąpiły w ramach interesujących Cię modułów.  
  
 Aby dodać wiele modułów, użyj symbolu wieloznacznego * na początku lub końcu ciągu. W przypadku nazwy modułów użyj nazw plików, nie nazw zestawów. Ścieżki plików nie są akceptowane.  
  
 Spróbuj zachować minimalną liczbę modułów. Lepsza wydajność jest mniejsza niż ilość danych do zebrania. Możesz również uzyskać mniej szumów w interfejsie użytkownika, ponieważ dostępne są mniej danych.  
  
## <a name="SaveSession"></a>Zapisywanie danych IntelliTrace do pliku  
 Dane, które IntelliTrace zostały zebrane, przechodzą do **debugowania/IntelliTrace/Save IntelliTrace Session** podczas debugowania, a aplikacja jest w stanie przerwania. Element menu jest wyłączony i nie będzie można zapisać IntelliTrace danych, jeśli aplikacja nadal działa lub jeśli zatrzymano debugowanie.  
  
 Można skonfigurować IntelliTrace do automatycznego zapisywania do pliku, przechodząc do **opcji Narzędzia/Opcje/IntelliTrace/Advanced** i wybierając pozycję **przechowuj IntelliTrace nagrania w tym katalogu**. Możesz również skonfigurować rozmiar wygenerowanego pliku, który powoduje, że program IntelliTrace ma zapisywać starsze dane, gdy zabraknie miejsca. Program Visual Studio tworzy dwa pliki dla każdej sesji IntelliTrace, gdy są one automatycznie zapisywane, a proces hostingu programu Visual Studio (vshost. exe) jest włączony.  
  
> [!TIP]
> Aby zaoszczędzić miejsce na dysku, Wyłącz zapisywanie plików automatycznie, gdy nie są już potrzebne. Wszystkie istniejące pliki nie zostaną usunięte. Zawsze możesz zapisywać na żądanie z menu kontekstowego.  
  
 Gdy zapisujesz dane IntelliTrace w pliku, uzyskasz jeden plik. iTrace dla każdego procesu, który IntelliTrace zbierany z. Następnie możesz otworzyć plik. iTrace w programie Visual Studio, przechodząc do **pliku/Otwórz/plik** i wybierając plik. iTrace z okna dialogowego Otwórz plik. Aby uzyskać więcej informacji, zobacz [Korzystanie z zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogi  
 [IntelliTrace w Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)  
  
 [Przewodnik po debugowaniu na żywo przy użyciu IntelliTrace w programie Visual Studio 2015 (Edytor tekstu)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)  
  
 [Przewodnik po debugowaniu na żywo za pomocą IntelliTrace w programie Visual Studio 2015 (klub społeczny)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)  
  
 [IntelliTrace w Visual Studio Enterprise 2015 obsługuje teraz dołączanie!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)  
  
 [Zbieranie danych z usługi systemu Windows przy użyciu autonomicznego modułu zbierającego IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)  
  
 [Edytowanie planu kolekcji IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan/)  
  
 [Niestandardowe TraceSource i debugowanie przy użyciu IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)  
  
 [IntelliTrace autonomiczny moduł zbierający i pule aplikacji działające w ramach kont Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)  
  
## <a name="forums"></a>Fora  
 [Visual Studio Debugger](https://social.msdn.microsoft.com/Forums/vsdebug)  
  
## <a name="videos"></a>Wideo  
 [Środowisko IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Debugowanie historyczne z IntelliTrace w Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
