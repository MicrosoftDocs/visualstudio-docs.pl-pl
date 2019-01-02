---
title: Narzędzia języka R dla programu Visual Studio
description: Narzędzia R Tools for Visual Studio (RTVS) to bezpłatne, typu open source rozszerzenie, które udostępnia wiele funkcji języka, w tym funkcji IntelliSense, debugowania i zdalnych obszarów roboczych.
ms.date: 11/13/2017
ms.prod: visual-studio-dev15
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: c2ae060c889065f7f8ba543e0cb20e8ea40ec758
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883084"
---
# <a name="work-with-r-in-visual-studio"></a>Praca z języka R w programie Visual Studio

R jest wysoce rozszerzalny język i środowisko na potrzeby obliczeń statystycznych i grafiki. Jego program jest dystrybuowany za darmo licencji GNU General Public License cieszy się silne wsparcie społeczności i jest znana z możliwości tworzenia publikacji jakości powierzchni symbole matematyczne i pochodnych w tym. Dowiedz się więcej na temat języka R w [r-project.org](https://www.r-project.org/about.html) i [wprowadzenie do języka R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

Narzędzia R Tools for Visual Studio (RTVS) to bezpłatny, [typu open-source](https://github.com/microsoft/RTVS) rozszerzenie dla programu Visual Studio 2017 i Visual Studio 2015 Update 3 (lub nowszy), wydawane na mocy licencji MIT. (Drugi składnik typu open source o nazwie [RHost](https://github.com/microsoft/R-Host), jakie łącza do plików binarnych interpreter języka R, jest wydawane na mocy V2 licencji publicznej GNU.)

> [!Note]
> RTVS obecnie jest obsługiwana tylko w programie Visual Studio na Windows i nie Visual Studio dla komputerów Mac.

Aby wystąpić języka R w programie Visual Studio:

- [Zainstaluj narzędzia języka R](installing-r-tools-for-visual-studio.md).
- Postępuj zgodnie z [wprowadzenie](getting-started-with-r.md) przewodniku, jak również [przykłady](getting-started-samples.md) i [uzyskiwanie pomocy](getting-started-help.md) artykułów.

Następnie użyj linków poniżej, aby dowiedzieć się więcej o funkcjach języka R, a także ogólne możliwości programu Visual Studio.

| Funkcja | Opis | Dokumentacja usługi Visual Studio — ogólne |
| --- | --- | --- |
| [System projektu usługi Visual Studio](r-projects-in-visual-studio.md) | Organizowanie i zarządzanie plikami pokrewne wygodny struktury i korzystać z zalet przydatne szablony dla elementów, takich jak kod R, dokumentace R, R Markdown, zapytań SQL i procedur składowanych. Korzystaj również [Menedżera pakietów](r-package-manager-in-visual-studio.md) i [integracji z programem SQL Server](integrating-sql-server-with-r.md).  | [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Workspace](r-workspaces-in-visual-studio.md) | RTVS można powiązać z lokalnych i zdalnych obszarów roboczych, co pozwala tworzyć kod R lokalnie z mniejszych zestawów danych, a następnie łatwe uruchamianie kodu na bardziej zaawansowanych komputerów opartych na chmurze znacznie większych zestawów danych. | n/d |
| [Opcje narzędzia języka R](options-for-r-tools-in-visual-studio.md) | Kontrolować różne aspekty RTVS. | [Okno dialogowe Opcje](../ide/reference/options-dialog-box-visual-studio.md) |
| [Zaawansowane edytowanie, IntelliSense i fragmentów kodu](editing-r-code-in-visual-studio.md) | Obejmuje kolorowania, [IntelliSense](r-intellisense.md) we wszystkich Twojego kodu i bibliotek, formatowanie kodu, pomocy dotyczącej sygnatur, przejdź do definicji i Znajdź wszystkie odwołania [fragmenty kodu](code-snippets-for-r.md)i nie tylko. | [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Znaczniki R Markdown](rmarkdown-with-r-in-visual-studio.md) | Dokumenty R Markdown ułatwić udostępnianie wyników danych przy użyciu zintegrowanego kodu języka R wewnątrz bloków kodu w języku znaczników markdown. | n/d |
| [Okno interaktywne](interactive-repl-for-r-in-visual-studio.md) | Zapewnia pełne środowisko REPL dla języka R, umożliwia łatwe uruchamianie kodu w pliku źródłowym, w oknie interaktywnym. | n/d |
| [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md) | Plotting jest integralną częścią środowiska języka R, a RTVS obsługuje wiele powierzchni niezależnie od systemu windows, każdy z własnych historii i możliwość przenoszenia drukuje między oknami. Wykresy można zapisać mapy bitowej i pliki PDF lub skopiowany do Schowka jako mapa bitowa lub metaplik.  | n/d |
| [Eksplorator zmiennych](variable-explorer.md) | Sprawdź zmienne w zakresach globalnych lub specyficzne dla pakietu, z możliwością oglądania tabel można sortować i Eksportuj do pliku CSV. | n/d |
| [Oferujący debugowania](debugging-r-in-visual-studio.md) | Obejmuje integrację z okna interaktywnego. | [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour) |

Zobacz też [— często zadawane pytania](faq.md).

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | [Obejrzyj film wideo (w witrynie youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) omówienie R Tools for Visual Studio (12 min 36s). Zobacz też [więcej wideo na temat narzędzia języka R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię!

1. **Problemy usługi GitHub**: Najlepszym sposobem skontaktować się z zespołem RTVS jest [rejestrując problem w serwisie GitHub](https://github.com/Microsoft/RTVS/issues), lub za pomocą **R Tools** > **opinii** menu.

1. **Wyślij uśmiech / łuk w dół**: **R Tools** > **opinii** menu jest szybkim sposobem wysyłania opinii i dołączenie plików dziennika RTVS, aby pomóc w diagnozowaniu problemu. (Dzienniki są zapisywane do *%temp%/RTVSlogs.zip* w przypadku, gdy chcesz wysyłać je oddzielnie.) Rejestrowanie jest wyłączona, jeśli został wyłączony, z telemetrii programu Visual Studio za pośrednictwem **pomocy** > **opinii** > **ustawienia** polecenie menu lub podczas instalacji.

1. **adres e-mail**: Możesz wysłać bezpośrednich opinii do zespołu w *rtvsuserfeedback (adresem)*.
