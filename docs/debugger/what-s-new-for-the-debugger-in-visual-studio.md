---
title: Co nowego w debugerze programu Visual Studio 2017 | Dokumentacja firmy Microsoft
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff14414415f86aeb704920f722eb221a2530a35c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993237"
---
# <a name="whats-new-for-the-debugger-in-includevsdev15miscincludesvsdev15mdmd"></a>Co nowego w debugerze programu [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Debuger zawiera następujące nowe funkcje:

- Nowość w wersji 15.5, **rozszerzenia Snapshot Debugger** tworzy migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który Cię interesuje. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

    Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:

  * Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
  * Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

    Aby uzyskać więcej informacji, zobacz [debugowania działających aplikacji platformy ASP.NET przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Nowość w wersji 15.5 w programie Visual Studio Enterprise, **IntelliTrace krok do tyłu** umożliwia automatyczne utworzenie migawki aplikacji na każdym punkcie przerwania i debuger krok zdarzenia. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

    Można poruszać się i Wyświetl migawki za pomocą **krok do tyłu** i **krok do przodu** przycisków na pasku narzędzi debugowania. Te przyciski nawigacji zdarzenia, które pojawiają się w **zdarzenia** karcie **narzędzia diagnostyczne** okna.

    ![Krok do tyłu i do przodu przyciski](../debugger/media/intellitrace-step-back-icons-description.png  "przyciski krok do tyłu i do przodu")

    Aby uzyskać więcej informacji, zobacz [Sprawdź poprzednie Stany aplikacji za pomocą funkcji IntelliTrace](../debugger/view-historical-application-state.md) strony.

- **Pomocnika wyjątków** zastępuje Asystenta wyjątków i pojawia się w polu kompaktowym niemodalnym oknie dialogowym, w którym wystąpił błąd. **Pomocnika wyjątków** zapewnia szybszy dostęp do wszelkich wyjątków wewnętrznych, dodatkowe analizy ze strony debugera (jeśli jest dostępny) i uzyskać natychmiastowy dostęp do **ustawienia wyjątków** dla wyjątku. Pomocnika wyjątków mogą być przeciągnięte do widoku zmiennoprzecinkowy, jeżeli blokuje coś, co chcesz zobaczyć.

    Na przykład **obiektu NullReferenceException** pojawi się na zmiennej, która ma odwołanie o wartości null (informacje o dodatkowych).

    ![Pomocnik wyjątków debugera](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Aby uzyskać więcej informacji, zobacz [przy użyciu nowego pomocnika wyjątków w programie Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/) wpis w blogu.

- Teraz możesz uruchamiać do wiersza kodu podczas wstrzymaniu w debugerze, wybierając **uruchom wykonywanie do tego miejsca** Ikona zielona strzałka (pojawi się ikona podczas najeżdżania kursorem na wiersz kodu). Eliminuje to potrzebę ustawiać tymczasowych punktów przerwania.

    ![Debuger na uruchamianie do kliknięcia](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Możesz ustawić warunki dotyczące wyjątków w **ustawienia wyjątków** okno dialogowe (można to zrobić za pomocą **Edytuj warunek** ikonę w oknie dialogowym Ustawienia wyjątków lub za pomocą menu kliknij prawym przyciskiem myszy na wyjątek.) Obecnie obsługiwane warunki obejmują nazwy modułu do dołączania lub wykluczania dla wyjątku.

    ![Warunki po wystąpieniu wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Dołącz do procesu, okno dialogowe zawiera nową funkcję wyszukiwania, które mogą pomóc Ci szybko zidentyfikować proces, który chcesz dołączyć do.

    ![Wyszukaj w dołączyć do procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Aby uzyskać więcej informacji na temat tych nowych funkcjach, zobacz [informacje o wersji dla [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes#debuggingdiag).

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)