---
title: Funkcje IntelliTrace | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9b1fc7da90eb4f263aaf3de19eb37cfa3272a249
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105735"
---
# <a name="intellitrace-features"></a>Funkcje IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć funkcji IntelliTrace do rejestrowania zdarzeń i aplikacji, dzięki czemu można sprawdzić stanu (stos wywołań i wartościach zmiennych lokalnych) w różnych momentach podczas wykonywania wywołania metod. Rozpocznij standardowe debugowanie — funkcja IntelliTrace jest domyślnie włączona i znajdują się informacje funkcji IntelliTrace jest rejestrowanie w nowym **narzędzia diagnostyczne** okna w obszarze **zdarzenia** kartę. Wybierz zdarzenie, a następnie kliknij przycisk **Uaktywnij debugowanie historyczne** aby zobaczyć stos wywołań i zmienne lokalne zapisane dla tego zdarzenia.  
  
 Aby uzyskać opis krok po kroku, zobacz [instruktażu: Za pomocą funkcji IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 Funkcja IntelliTrace jest dostępne w programie Visual Studio Enterprise, ale nie w Visual Studio Professional lub Community Edition.  
  
 Aby upewnić się, że IntelliTrace jest włączony, należy otworzyć **narzędzia / Opcje / IntelliTrace** Strona opcji. **Włączenie funkcji IntelliTrace** powinno być zaznaczone domyślnie.  
  
> [!NOTE]
>  Zakres wszystkie ustawienia na **IntelliTrace** strona opcje to program Visual Studio jako całości, nie do poszczególnych projektów lub rozwiązań. Zmiany w tych ustawieniach mają zastosowanie do wszystkich wystąpień programu Visual Studio, wszystkie debugowania sesji i wszystkich projektów i rozwiązań.  
  
## <a name="ChooseEvents"></a> Wybierz zdarzenia przez IntelliTrace  
 Można włączyć lub wyłączyć rejestrowanie dla określonych zdarzeń IntelliTrace.  
  
 Jeśli debugujesz, Zatrzymaj debugowanie. Przejdź do **narzędzia / Opcje / IntelliTrace / zdarzenia IntelliTrace**. Wybierz zdarzenia funkcji IntelliTrace do rejestrowania.  
  
## <a name="GoingFurther"></a> Zbierz zdarzenia IntelliTrace i wywołania informacji  
 To nie jest domyślnie włączona, ale IntelliTrace może rejestrować wywołania metody wraz z wydarzeniami. Aby włączyć zbieranie wywołań, przejdź do metody **narzędzia / Opcje / IntelliTrace / ogólne**i wybierz **zdarzenia IntelliTrace i wywołania informacji**.  
  
 Dzięki temu można wyświetlić historię stosu wywołań, poruszać i wywołań w kodzie. IntelliTrace zapisuje dane, takie jak nazwy metod, punkty wejścia i wyjścia metody i niektóre wartości parametrów i zwracanych wartości.  
  
> [!TIP]
>  Ta opcja nie jest włączona domyślnie, ponieważ dodaje znaczne obciążenie. Nie tylko ma IntelliTrace do przechwycenia wywołania metody, co sprawia, że aplikacja, ale ma również radzenia sobie z dużo większego zbioru danych, jeśli chodzi o jej wyświetlanie na ekranie lub utrwalanie go na dysku.  
>   
>  Można zmniejszyć obciążenie przez ograniczenie możliwości wykonywania listy zdarzeń przez IntelliTrace i przechowując liczba modułów są zbierane do minimum. Aby uzyskać więcej informacji, zobacz [kontroli ilości informacji o wywołaniach funkcji IntelliTrace rejestruje](../debugger/intellitrace-features.md#ControlCallData).  
  
### <a name="using-the-navigation-gutter"></a>Za pomocą trasę nawigacji  
 Można użyć marginesu nawigacyjnego pojawiającego się po lewej stronie okna kodu. Jeśli nie widzisz marginesu nawigacyjnego pojawiającego, przejdź do strony **narzędzia / Opcje / IntelliTrace / zaawansowane**i wybierz **Wyświetl Margines nawigacyjny w trybie debugowania**.  
  
 Trasę nawigacji umożliwia przeniesienie do przodu i wstecz za pośrednictwem wywołania metod i zdarzeń w trybie debugowania historycznego. Aby uzyskać więcej informacji na temat debugowania historycznego, zobacz [debugowania historycznego](../debugger/historical-debugging.md). Ma pewną liczbę poleceń:  
  
|||  
|-|-|  
|**Ustaw kontekst debugera tutaj**|Ustaw kontekst debugowania do parametrów czasowych wywołania tam, gdzie jest dostępny.<br /><br /> Ikona ta pojawia się tylko na bieżący stos wywołań.|  
|**Wróć do strony wywołań**|Przenieść wskaźnik i kontekst debugowania do gdy wywołana została funkcja bieżąca.<br /><br /> Jeśli jesteś w trybie debugowania na żywo, to polecenie włącza debugowanie historyczne. Jeśli przejdziesz do oryginalnego przerwania wykonywania debugowania historycznego jest wyłączona i debugowania na żywo jest włączona.|  
|**Przejdź do poprzedniego wywołania lub zdarzenia funkcji IntelliTrace**|Przenieść wskaźnik i kontekst debugowania z powrotem do poprzedniego wywołania lub zdarzenia.<br /><br /> Jeśli jesteś w trybie debugowania na żywo, to polecenie włącza debugowanie historyczne.|  
|**Wkrocz**|Wejdź do aktualnie wybranej funkcji.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|  
|**Przejdź do następnego wywołania lub zdarzenia funkcji IntelliTrace**|Przenieść wskaźnik i kontekst debugowania do kolejnego wywołania lub zdarzenia, dla którego IntelliTrace istnieją dane.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|  
|**Przejdź do trybu na żywo**|Wróć do trybu debugowania na żywo.|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>Wyszukaj wiersz lub metody w IntelliTrace  
 Metody można przeszukiwać tylko wtedy, gdy włączono informacje dotyczące wywołania metody. Możesz wyszukiwać historię IntelliTrace dla określonego wiersza lub metody. Gdy debuger, wykonywanie zostało zatrzymane, kliknij prawym przyciskiem myszy wewnątrz treści funkcji, aby wyświetlić menu kontekstowe i kliknij opcję **wyszukiwania dla tego wiersza w funkcji IntelliTrace** lub **wyszukiwania dla tej metody w funkcji IntelliTrace**.  
  
### <a name="ControlCallData"></a> Kontroluj, ile informacji wywołań IntelliTrace  
 Domyślnie IntelliTrace zapisuje informacje dla wszystkich modułów, które są używane przez rozwiązania. Można ustawić funkcji IntelliTrace do rejestrowania informacji o wywołaniach tylko moduły, które Cię interesują. W **narzędzia / Opcje / IntelliTrace / modułów**, można określić moduły, aby dołączyć lub modułów, które mają zostać wykluczone z IntelliTrace. IntelliTrace będzie zbierać zdarzenia, które pochodzą z modułów, które określono i wywołania metody, które wystąpiły w ramach modułów Cię interesuje.  
  
 Aby dodać wiele modułów, użyj symbolu wieloznacznego * na początku lub końcu ciągu. W przypadku nazwy modułów użyj nazw plików, nie nazw zestawów. Ścieżki plików nie są akceptowane.  
  
 Spróbuj przechowywać liczba modułów do minimum. Możesz uzyskać lepszą wydajność, ponieważ istnieje mniejszej ilości danych, które mają być zbierane. Mniej szumu możesz także uzyskać w interfejsie użytkownika, ponieważ mniejszej ilości danych, aby wykonać kroki.  
  
## <a name="SaveSession"></a> Zapisywanie danych funkcji IntelliTrace do pliku  
 Można zapisać dane IntelliTrace zebrał zamierza **debugowanie / IntelliTrace / Zapisz sesję IntelliTrace** podczas debugowania, a aplikacja jest w stanie przerwania. Element menu jest wyłączona, a nie będziesz w stanie zapisywać dane IntelliTrace zebrał, jeśli aplikacja jest nadal uruchomiona lub zatrzymaniu debugowania.  
  
 Możesz skonfigurować IntelliTrace, aby automatycznie zapisać do pliku, przechodząc do **narzędzia / Opcje / IntelliTrace / zaawansowane** i wybierając polecenie **nagrania Store IntelliTrace w tym katalogu**. Można również skonfigurować Ustaw rozmiar generowanego pliku, co powoduje, że IntelliTrace, aby móc starszych danych, gdy zabraknie mu miejsca. Program Visual Studio utworzy dwa pliki, dla każdej sesji IntelliTrace, gdy są one automatycznie zapisywane i programu Visual Studio, proces hostingu (vshost.exe) jest włączona.  
  
> [!TIP]
>  Aby zaoszczędzić miejsce na dysku, wyłącz zapisywanie plików automatycznie, gdy użytkownik nie są już potrzebne. Wszelkie istniejące pliki nie zostaną usunięte. Można zapisać do pliku na żądanie z poziomu menu kontekstowego.  
  
 Po zapisaniu danych funkcji IntelliTrace do pliku, uzyskujesz jeden plik .itrace dla każdego procesu, które funkcji IntelliTrace zebrane. Można następnie otwórz plik .itrace w Visual Studio, przechodząc do **pliku / Otwórz / pliku** i wybierając plik .itrace z okna dialogowego otwierania pliku. Aby uzyskać więcej informacji, zobacz [używanie zapisanych danych funkcji IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## <a name="blogs"></a>Blogi  
 [Funkcja IntelliTrace w Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Przewodnik z debugowania na żywo za pomocą funkcji IntelliTrace w programie Visual Studio 2015 (Edytor tekstu)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Przewodnik z debugowania na żywo za pomocą funkcji IntelliTrace w programie Visual Studio 2015 (społecznościowych Club)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [Funkcja IntelliTrace w Visual Studio Enterprise 2015 teraz obsługuje dołączanie!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Zbieranie danych z usługi systemu windows przy użyciu autonomicznego modułu zbierającego IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Edytowanie planu kolekcji funkcji IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Niestandardowe TraceSource i debugowania przy użyciu funkcji IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Uruchamianie IntelliTrace Standalone Collector i pule aplikacji w ramach kont usługi Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>Fora  
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>Wideo  
 [Środowisko funkcji IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Debugowanie historyczne za pomocą IntelliTrace w programie Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
