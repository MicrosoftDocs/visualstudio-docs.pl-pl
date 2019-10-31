---
title: Narzędzia języka R dla programu Visual Studio
description: R Tools for Visual Studio 2017 (RTVS) to bezpłatne rozszerzenie typu "open source", które zapewnia wiele funkcji języka, w tym IntelliSense, debugowanie i zdalne obszary robocze.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 1132a7a0363e2d508d6eff1026192aad3407fca4
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189244"
---
# <a name="work-with-r-in-visual-studio"></a>Współpraca z językiem R w programie Visual Studio

R to wysoce rozszerzalny język i środowisko do obliczeń statystycznych i graficznych. Jest ona dystrybuowana bezpłatnie na podstawie ogólnej publicznej licencji GNU, ma silne wsparcie społecznościowe i jest znana, aby można było tworzyć wykresy z jakością publikacji, w tym symbole matematyczne i wzory. Więcej informacji na temat języka R można znaleźć pod adresem [r-Project.org](https://www.r-project.org/about.html) i [wprowadzeniem do języka r](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R Tools for Visual Studio (RTVS) to bezpłatne rozszerzenie [typu open source](https://github.com/microsoft/RTVS) dla programu visual Studio 2017 i programu visual Studio 2015 Update 3 (lub nowszego), wydane w ramach licencji MIT. (Drugi składnik typu open source o nazwie [RHost](https://github.com/microsoft/R-Host), który łączy się z danymi binarnymi interpretera języka R, jest wydawany w ramach programu GNU Public License v2).

> [!Note]
> RTVS jest obecnie obsługiwana tylko w programie Visual Studio 2017 w systemie Windows, a nie Visual Studio dla komputerów Mac. Nie jest on dostępny dla programu Visual Studio 2019.

Aby środowiska R w programie Visual Studio:

- [Zainstaluj narzędzia języka R](installing-r-tools-for-visual-studio.md).
- Skorzystaj z przewodnika [wprowadzającego](getting-started-with-r.md) , a także [przykładów](getting-started-samples.md) i [uzyskiwania artykułów pomocy](getting-started-help.md) .

Następnie skorzystaj z poniższych linków, aby dowiedzieć się więcej na temat funkcji związanych z językiem R, a także ogólnych możliwości programu Visual Studio.

| Funkcja | Opis | Ogólna Dokumentacja programu Visual Studio |
| --- | --- | --- |
| [System projektu programu Visual Studio](r-projects-in-visual-studio.md) | Organizuj powiązane pliki i zarządzaj nimi w wygodnej strukturze i korzystaj z przydatnych szablonów dla elementów, takich jak kod R, Dokumentacja języka R, R Markdown, zapytania SQL i procedury składowane. Ciesz się również [menedżerem pakietów](r-package-manager-in-visual-studio.md) i [integracją SQL Server](integrating-sql-server-with-r.md).  | [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Obszary](r-workspaces-in-visual-studio.md) | RTVS można powiązać z lokalnymi i zdalnymi obszarami roboczymi, co pozwala na tworzenie kodu R lokalnie przy użyciu mniejszych zestawów danych, a następnie uruchamianie kodu na bardziej zaawansowanych komputerach opartych na chmurze z znacznie większymi zestawami danych. | n/d |
| [Opcje narzędzi języka R](options-for-r-tools-in-visual-studio.md) | Kontroluj różne aspekty RTVS. | [Opcje — okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md) |
| [Bogate edytowanie, IntelliSense i fragmenty kodu](editing-r-code-in-visual-studio.md) | Obejmuje kolorowanie składni, funkcję [IntelliSense](r-intellisense.md) we wszystkich kodzie i bibliotekach, formatowanie kodu, pomoc dotyczącą podpisu, przejdź do definicji, Znajdź wszystkie odwołania, [fragmenty kodu](code-snippets-for-r.md)i inne elementy. | [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Znaczniki R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown dokumenty ułatwiają udostępnianie wyników danych przy użyciu zintegrowanego kodu R w blokach kodu o promocji. | n/d |
| [Okno interaktywne](interactive-repl-for-r-in-visual-studio.md) | Oferuje pełne środowisko REPL dla języka R z możliwością łatwego uruchamiania kodu w pliku źródłowym w oknie interaktywnym. | n/d |
| [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md) | Wykreślanie jest integralną częścią środowiska R, a RTVS obsługuje wiele niezależnych okien kreślenia, z których każdy ma własną historię i możliwość przenoszenia wykresów między oknami. Wykresy mogą być zapisane w plikach map bitowych i PDF albo kopiowane do Schowka jako mapa bitowa lub metaplik.  | n/d |
| [Eksplorator zmiennych](variable-explorer.md) | Sprawdź zmienne w zakresach globalnych lub specyficznych dla pakietów, umożliwiając wyświetlanie tabel do sortowania i eksportowanie do pliku CSV. | n/d |
| [W pełni funkcjonalne debugowanie](debugging-r-in-visual-studio.md) | Obejmuje integrację z oknem interaktywnym. | [Debugowanie w programie Visual Studio](../debugger/debugger-feature-tour.md) |

Zobacz również [często zadawane pytania](faq.md).

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](../install/media/video-icon.png "Obejrzyj wideo") | [Obejrzyj film wideo (YouTube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) , aby zapoznać się z omówieniem R Tools for Visual Studio (12M 36s). Zobacz też [Więcej klipów wideo dotyczących narzędzi R Tools](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię.

1. **Problemy**z usługą GitHub: najlepszym sposobem osiągnięcia dostępu do zespołu RTVS jest [zgłoszenie problemu w usłudze GitHub](https://github.com/Microsoft/RTVS/issues)lub użycie menu **opinii** **narzędzi R Tools** > .

1. **Wyślij uśmiech/niezadowolenie**: menu **opinii** o **narzędziach R Tools** > jest szybkim sposobem na wysłanie opinii i dołączenie plików dziennika RTVS, aby pomóc w zdiagnozowaniu problemu. (Dzienniki są zapisywane w *katalogu% Temp%/RTVSlogs.zip* w przypadku, gdy chcesz je wysłać oddzielnie). Rejestrowanie jest wyłączone, jeśli wybrałeś **opcję dane telemetryczne programu Visual** Studio za pomocą polecenia menu **Ustawienia** >  > **informacji zwrotnych** , lub podczas instalacji.

1. **Adres e-mail**: możesz wysłać bezpośrednią opinię do zespołu pod adresem *rtvsuserfeedback (at) Microsoft.com*.
