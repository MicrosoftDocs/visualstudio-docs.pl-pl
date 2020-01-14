---
title: Co nowego w debugerze w programie Visual Studio 2017 | Microsoft Docs
titleSuffix: ''
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
monikerRange: vs-2017
ms.openlocfilehash: 523867a8f9aa074e9122c74deb8bcd91cddd8bee
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944219"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Co nowego w debugerze w programie Visual Studio 2017

Debuger obejmuje następujące nowe funkcje:

- Nowość w wersji 15,5, **Snapshot Debugger** wykonuje migawkę aplikacji w produkcji, gdy interesujący kod jest wykonywany. Aby nakazać debugera, aby utworzyć migawkę, należy ustawić punkty przyciągania i punkty rejestrowania w kodzie. Debuger pozwala zobaczyć dokładnie tego, co poszło, bez wywierania wpływu na ruch z aplikacji produkcyjnej. Rozszerzenie Snapshot Debugger może pomóc w znacznie skrócić czas potrzebny do rozwiązywania problemów występujących w środowiskach produkcyjnych.

    Zbieranie migawek jest dostępna dla następujących aplikacji sieci web działające w usłudze Azure App Service:

  * Aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
  * Aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.

    Aby uzyskać więcej informacji, zobacz [debugowanie live ASP.NET Apps przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md).

- Nowość w wersji 15,5 tylko w Visual Studio Enterprise, **IntelliTrace krokowo do tyłu** wykonuje migawkę aplikacji przy każdym punkcie przerwania i zdarzeniu debugera. Zarejestrowane migawek umożliwiają wrócić do poprzednich punktów przerwania lub kroków i wyświetlić stan aplikacji, tak jak w przeszłości. IntelliTrace krok do tyłu pozwalają zaoszczędzić czas podczas mają być wyświetlane poprzedni stan aplikacji, ale nie chcesz ponownie uruchomić debugowanie lub Utwórz ponownie stan żądaną aplikację.

    Możesz nawigować i przeglądać migawki przy użyciu przycisków **krok wstecz** i **dalej** na pasku narzędzi debugowania. Te przyciski służą do przechodzenia do zdarzeń, które pojawiają się na karcie **zdarzenia** w oknie **Narzędzia diagnostyczne** .

    ![Przyciski do tyłu i do przodu](../debugger/media/intellitrace-step-back-icons-description.png  "Przyciski do tyłu i do przodu")

    Aby uzyskać więcej informacji, zobacz stronę [Sprawdzanie stanu poprzedniej aplikacji przy użyciu IntelliTrace](view-historical-application-state.md) .

- **Pomocnik wyjątku** zastępuje asystenta wyjątków i pojawia się w niemodalnym oknie dialogowym, w którym wystąpił błąd. **Pomocnik wyjątków** zapewnia szybszy dostęp do wszelkich wyjątków wewnętrznych, dodatkową analizę przez debuger (jeśli jest dostępny) i natychmiastowy dostęp do **ustawień wyjątków** dla wyjątku. Pomocnika wyjątków można również przeciągać do widoku swobodnego, jeśli blokuje coś, czego potrzebujesz do wyświetlenia.

    Na przykład **NullReferenceException** jest teraz wyświetlana zmienna, która ma odwołanie o wartości null (dodatkowe informacje).

    ![Pomocnik wyjątku debugera](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Aby uzyskać więcej informacji, zobacz wpis w blogu [using the new Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) .

- Teraz można uruchomić wiersz kodu, gdy jest wstrzymany w debugerze, zaznaczając ikonę **Uruchom wykonywanie do tutaj** zieloną strzałkę (zobaczysz ikonę przy umieszczeniu wskaźnika myszy nad wierszem kodu). Eliminuje to potrzebę ustawiania tymczasowych punktów przerwania.

    ![Uruchomienie debugera do kliknięcia](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Warunki dotyczące wyjątków można ustawić w oknie dialogowym **Ustawienia wyjątku** (można to zrobić za pomocą ikony **Edytuj warunek** w oknie dialogowym Ustawienia wyjątku lub przy użyciu menu po kliknięciu prawym przyciskiem myszy dla wyjątku). Obecnie obsługiwane warunki obejmują nazwy modułów, które mają zostać dołączone lub wykluczone dla wyjątku.

    ![Warunki dotyczące wyjątku](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Okno dialogowe Dołączanie do procesu zawiera nową funkcję wyszukiwania, która może ułatwić szybkie zidentyfikowanie procesu, który należy dołączyć do programu.

    ![Wyszukaj w obszarze Dołącz do procesu](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Aby uzyskać więcej informacji o tych nowych funkcjach, zapoznaj się z informacjami o [wersji [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)