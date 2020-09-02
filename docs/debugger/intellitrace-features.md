---
title: Funkcje IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ac7ca0e59a479aff3386486d2ceaf061038db68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536581"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>Funkcje IntelliTrace (C#, Visual Basic, C++)

Za pomocą IntelliTrace można rejestrować zdarzenia i metody wywołania aplikacji, co umożliwia badanie stanu (stos wywołań i wartości zmiennych lokalnych) w różnych punktach wykonywania. Po prostu Rozpocznij debugowanie w zwykły sposób — IntelliTrace jest domyślnie włączone i zobaczysz, że IntelliTrace informacje są rejestrowane w nowym oknie **Narzędzia diagnostyczne** na karcie **zdarzenia** . Wybierz zdarzenie, a następnie kliknij pozycję **Aktywuj debugowanie historyczne** , aby zobaczyć stos wywołań i zarejestrowane lokalnie dla tego zdarzenia.

Aby zapoznać się z opisem krok po kroku, zobacz [Przewodnik: korzystanie z IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

Program IntelliTrace jest dostępny w wersji Visual Studio Enterprise, ale nie w wersjach Visual Studio Professional i Community.

Aby potwierdzić, że IntelliTrace jest włączona, Otwórz stronę opcje **> > Opcje IntelliTrace** . Opcja **Włącz IntelliTrace** powinna być domyślnie zaznaczona.

> [!NOTE]
> Zakres wszystkich ustawień na stronie opcji **IntelliTrace** to program Visual Studio jako całość, a nie pojedyncze projekty lub rozwiązania. Zmiana tych ustawień dotyczy wszystkich wystąpień programu Visual Studio, wszystkich sesji debugowania i wszystkich projektów lub rozwiązań.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> Wybierz zdarzenia, które IntelliTrace rekordy (C#, Visual Basic)

Możesz włączyć lub wyłączyć nagrywanie dla określonych zdarzeń IntelliTrace.

Jeśli debugujesz, Zatrzymaj debugowanie. Przejdź do pozycji **narzędzia > opcje > IntelliTrace > zdarzenia IntelliTrace**. Wybierz zdarzenia, które mają być rejestrowane przez IntelliTrace.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> Zbierz migawki (C#, Visual Basic, C++)

Ta funkcja nie jest domyślnie włączona, ale IntelliTrace może przechwytywać migawki aplikacji w każdym punkcie przerwania i zdarzeniu debugera. można je wyświetlić w historycznej sesji debugowania. Migawka umożliwia wyświetlenie pełnego stanu aplikacji. Aby włączyć przechwytywanie migawek, przejdź do pozycji **narzędzia > opcje > IntelliTrace > ogólne**i wybierz pozycję **migawki IntelliTrace (zarządzane i natywne)**. Aby uzyskać więcej informacji, zobacz [Inspekcja poprzednich stanów aplikacji przy użyciu IntelliTrace](../debugger/view-historical-application-state.md).

Migawki są dostępne w Visual Studio Enterprise 2017 w wersji 15,5 lub nowszej. wymaga to również rocznicowej aktualizacji systemu Windows 10.  W przypadku aplikacji .NET Core i ASP.NET Core jest wymagana Visual Studio Enterprise 2017 wersja 15,7. W przypadku aplikacji natywnych przeznaczonych dla systemu Windows jest wymagana Visual Studio Enterprise 2017 wersja 15,9 Preview 2.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> Zbierz zdarzenia IntelliTrace i informacje o wywołaniu (C#, Visual Basic)

Ta funkcja nie jest domyślnie włączona, ale IntelliTrace może rejestrować wywołania metod wraz ze zdarzeniami. Aby włączyć zbieranie wywołań metod, przejdź do pozycji **narzędzia > opcje > IntelliTrace > ogólne**, a następnie wybierz pozycję **zdarzenia IntelliTrace i informacje o wywołaniu (tylko zarządzane)**.

Informacje o wywołaniu nie są obecnie dostępne dla aplikacji .NET Core i ASP.NET Core.

Dzięki temu można zobaczyć historię stosu wywołań i przejść do tyłu i do przodu przez wywołania w kodzie. IntelliTrace rejestruje dane, takie jak nazwy metod, wejścia do metody i punkty wyjścia oraz pewne wartości parametrów i wartości zwracane.

> [!TIP]
> Ta opcja nie jest domyślnie włączona, ponieważ zwiększa nakłady pracy. Nie tylko IntelliTrace muszą przechwycić każde wywołanie metody dla aplikacji, ale również musi zająć dużo większego zestawu danych, gdy jest on wyświetlany na ekranie lub utrwala go na dysku.
>
> Możesz zmniejszyć obciążenie wydajności, ograniczając listę zdarzeń, które IntelliTrace rekordy i utrzymując liczbę modułów, które są zbierane do minimum. Aby uzyskać więcej informacji, zobacz [kontrolowanie, jak dużo informacji o wywołaniu IntelliTrace rekordy](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Używanie marginesu nawigacji

Możesz użyć marginesu nawigacji, który pojawia się po lewej stronie okna kod. Jeśli nie widzisz marginesu nawigacyjnego, przejdź do pozycji **narzędzia > opcje > IntelliTrace > zaawansowane**i wybierz opcję **Wyświetl margines nawigacyjny w trybie debugowania**.

Margines nawigacyjny umożliwia przechodzenie do przodu i do tyłu przez wywołania metod i zdarzenia w trybie debugowania historycznego. Aby uzyskać więcej informacji na temat debugowania historycznego, zobacz [debugowanie historyczne](../debugger/historical-debugging.md). Zawiera kilka poleceń:

|Polecenie|Opis|
|-|-|
|**Ustaw tutaj kontekst debugera**|Ustaw kontekst debugowania na czas wywołania, gdzie się pojawi.<br /><br /> Ta ikona jest wyświetlana tylko na bieżącym stosie wywołań.|
|**Wróć do witryny wywołania**|Przenieś wskaźnik i kontekst debugowania z powrotem do miejsca, w którym wywołano bieżącą funkcję.<br /><br /> W trybie debugowania na żywo to polecenie włącza debugowanie historyczne. Jeśli wrócisz do oryginalnego przerwania wykonywania, debugowanie historyczne jest wyłączone, a debugowanie na żywo jest włączone.|
|**Przejdź do poprzedniego wywołania lub zdarzenia IntelliTrace**|Przenieś wskaźnik i kontekst debugowania z powrotem do poprzedniego wywołania lub zdarzenia.<br /><br /> W trybie debugowania na żywo to polecenie włącza debugowanie historyczne.|
|**Wkrocz**|Wkrocz do aktualnie wybranej funkcji.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|
|**Przejdź do następnego wywołania lub zdarzenia IntelliTrace**|Przenieś wskaźnik i kontekst debugowania do następnego wywołania lub zdarzenia, dla którego istnieją dane IntelliTrace.<br /><br /> To polecenie jest dostępne tylko wtedy, gdy jesteś w trybie debugowania historycznego.|
|**Przejdź do trybu na żywo**|Wróć do trybu debugowania na żywo.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Wyszukaj wiersz lub metodę w IntelliTrace

Metody wyszukiwania można wyszukiwać tylko wtedy, gdy zostały włączone informacje o wywołaniu metody. Historię IntelliTrace można wyszukiwać dla konkretnego wiersza lub metody. Podczas gdy wykonywanie debugera jest zatrzymane, kliknij prawym przyciskiem myszy wewnątrz treści funkcji, aby wyświetlić menu kontekstowe, a następnie kliknij opcję **Wyszukaj ten wiersz w IntelliTrace** lub **Wyszukaj tę metodę w IntelliTrace**.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> Sterowanie ilością rekordów IntelliTrace informacji o wywołaniu

Domyślnie IntelliTrace rejestruje informacje dla wszystkich modułów używanych przez rozwiązanie. Możesz ustawić IntelliTrace, aby rejestrować informacje o wywołaniu tylko dla interesujących Cię modułów. W obszarze **narzędzia > opcje > IntelliTrace > moduły**, można określić moduły do uwzględnienia lub moduły do wykluczenia z IntelliTrace. IntelliTrace będzie zbierać tylko zdarzenia pochodzące z określonych modułów i wywołania metody, które wystąpiły w ramach interesujących Cię modułów.

Aby dodać wiele modułów, użyj symbolu wieloznacznego * na początku lub końcu ciągu. W przypadku nazwy modułów użyj nazw plików, nie nazw zestawów. Ścieżki plików nie są akceptowane.

Spróbuj zachować minimalną liczbę modułów. Lepsza wydajność jest mniejsza niż ilość danych do zebrania. Możesz również uzyskać mniej szumów w interfejsie użytkownika, ponieważ dostępne są mniej danych.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> Zapisz dane IntelliTrace w pliku (C#, Visual Basic, C++)

Można zapisać dane, które IntelliTrace zostały zebrane do **debugowania > IntelliTrace > zapisywania sesji IntelliTrace** podczas debugowania, a aplikacja jest w stanie przerwania. Element menu jest wyłączony i nie będzie można zapisać IntelliTrace danych, jeśli aplikacja nadal działa lub jeśli zatrzymano debugowanie.

Można skonfigurować IntelliTrace do automatycznego zapisywania do pliku, przechodząc do **opcji narzędzia > opcje > IntelliTrace > zaawansowane** i wybierając pozycję **przechowuj IntelliTrace nagrania w tym katalogu**. Możesz również skonfigurować rozmiar wygenerowanego pliku, który powoduje, że program IntelliTrace ma zapisywać starsze dane, gdy zabraknie miejsca. Program Visual Studio tworzy dwa pliki dla każdej sesji IntelliTrace, gdy są one automatycznie zapisywane, a proces hostingu programu Visual Studio (vshost.exe) jest włączony.

> [!TIP]
> Aby zaoszczędzić miejsce na dysku, Wyłącz zapisywanie plików automatycznie, gdy nie są już potrzebne. Wszystkie istniejące pliki nie zostaną usunięte. Zawsze możesz zapisywać na żądanie z menu kontekstowego.

Gdy zapisujesz dane IntelliTrace w pliku, uzyskasz jeden plik. iTrace dla każdego procesu, który IntelliTrace zbierany z. Następnie możesz otworzyć plik. iTrace w programie Visual Studio, przechodząc do **pliku > Otwórz plik >** i wybierając plik. iTrace z okna dialogowego Otwórz plik. Aby uzyskać więcej informacji, zobacz [Korzystanie z zapisanych danych IntelliTrace](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogi

[IntelliTrace w Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Przewodnik po debugowaniu na żywo przy użyciu IntelliTrace w programie Visual Studio 2015 (Edytor tekstu)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/)

[Przewodnik po debugowaniu na żywo za pomocą IntelliTrace w programie Visual Studio 2015 (klub społeczny)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/)

[IntelliTrace w Visual Studio Enterprise 2015 obsługuje teraz dołączanie!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/)

[Zbieranie danych z usługi systemu Windows przy użyciu autonomicznego modułu zbierającego IntelliTrace](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/)

[Edytowanie planu kolekcji IntelliTrace](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan)

[Niestandardowe TraceSource i debugowanie przy użyciu IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/)

[IntelliTrace autonomiczny moduł zbierający i pule aplikacji działające w ramach kont Active Directory](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/)

## <a name="forums"></a>Fora

[Visual Studio Debugger](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Filmy wideo

[Środowisko IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)

[Debugowanie historyczne z IntelliTrace w Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)
