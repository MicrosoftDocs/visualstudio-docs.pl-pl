---
title: Narzędzia języka R dla programu Visual Studio
description: Narzędzia języka R dla programu Visual Studio 2017 (RTVS, R Tools for Visual Studio) to bezpłatne rozszerzenie typu open source, które zapewnia wiele funkcji języka, w tym funkcję IntelliSense, debugowanie i zdalne obszary robocze.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 89aa8b9d1b1f288e19252b8a111666f5b4e3e087
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238715"
---
# <a name="work-with-r-in-visual-studio"></a>Praca z językiem R w programie Visual Studio

R to wysoce rozszerzalny język i środowisko do obliczeń statystycznych i graficznych. Jest on dystrybuowany bezpłatnie na ogólnej licencji publicznej GNU, ma silne wsparcie społeczności i jest znany z możliwości generowania wysokiej jakości wykresów z symbolami matematycznymi i formułami nadających się do publikacji. Więcej informacji na temat języka R można znaleźć w witrynie [r-project.org](https://www.r-project.org/about.html) i na stronie [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html) (Wprowadzenie do języka R).

Narzędzia języka R dla programu Visual Studio (RTVS) to bezpłatne rozszerzenie typu [open source](https://github.com/microsoft/RTVS) dla programu Visual Studio 2017 i Visual Studio 2015 Update 3 (lub nowszego) wydane na licencji MIT. (Drugi składnik typu open source o nazwie [RHost](https://github.com/microsoft/R-Host), który zapewnia połączenie z plikami binarnymi interpretera języka R, jest wydawany na licencji publicznej GNU V2).

> [!Note]
> Narzędzia RTVS są obecnie obsługiwane tylko w programie Visual Studio 2017 w systemie Windows; nie są obsługiwane w programie Visual Studio dla komputerów Mac. Nie są dostępne dla programu Visual Studio 2019.

Aby korzystać z języka R w programie Visual Studio, wykonaj następujące czynności:

- [Zainstaluj narzędzia języka R](installing-r-tools-for-visual-studio.md).
- Postępuj zgodnie z przewodnikiem [Wprowadzenie](getting-started-with-r.md) oraz artykułami [Przykłady](getting-started-samples.md) i [Uzyskiwanie pomocy](getting-started-help.md).

Następnie skorzystaj z poniższych linków, aby dowiedzieć się więcej na temat funkcji związanych z językiem R, a także ogólnych możliwości programu Visual Studio.

| Cechy | Opis | Ogólna dokumentacja programu Visual Studio |
| --- | --- | --- |
| [System projektu programu Visual Studio](r-projects-in-visual-studio.md) | Organizuj powiązane pliki i zarządzaj nimi w wygodnej strukturze oraz korzystaj z przydatnych szablonów dla elementów takich jak kod języka R, dokumentacja języka R, znaczniki R Markdown, zapytania SQL i procedury składowane. Możesz także korzystać z [menedżera pakietów](r-package-manager-in-visual-studio.md) oraz [integracji programu SQL Server](integrating-sql-server-with-r.md).  | [Rozwiązania i projekty w programie Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Workspace](r-workspaces-in-visual-studio.md) | Narzędzia RTVS można powiązać z lokalnymi i zdalnymi obszarami roboczymi, co pozwala na pisanie kodu R lokalnie przy użyciu mniejszych zestawów danych, a następnie uruchamianie kodu na bardziej zaawansowanych komputerach opartych na chmurze ze znacznie większymi zestawami danych. | nie dotyczy |
| [Opcje narzędzi języka R](options-for-r-tools-in-visual-studio.md) | Kontroluj różne aspekty narzędzi RTVS. | [Opcje — Okno dialogowe](../ide/reference/options-dialog-box-visual-studio.md) |
| [Zaawansowane edytowanie, IntelliSense i fragmenty kodu](editing-r-code-in-visual-studio.md) | Zawiera kolorowanie składni, funkcję [IntelliSense](r-intellisense.md) w całym kodzie i wszystkich bibliotekach, formatowanie kodu, pomoc dotyczącą sygnatury, funkcję Przejdź do definicji, funkcję Znajdź wszystkie odwołania, [fragmenty kodu](code-snippets-for-r.md) i inne funkcje. | [Funkcje edytora kodu](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Znaczniki R Markdown](rmarkdown-with-r-in-visual-studio.md) | Dokumenty ze znacznikami R Markdown ułatwiają udostępnianie wyników danych przy użyciu zintegrowanego kodu języka R w blokach kodu Markdown. | nie dotyczy |
| [Okno interaktywne](interactive-repl-for-r-in-visual-studio.md) | Zapewnia pełne środowisko REPL dla języka R z możliwością łatwego uruchamiania kodu w pliku źródłowym w oknie interaktywnym. | nie dotyczy |
| [Wizualizowanie danych](visualizing-data-with-r-in-visual-studio.md) | Kreślenie jest integralną częścią środowiska języka R, a narzędzia RTVS obsługują wiele niezależnych okien wykresów, z których każde ma własną historię i możliwość przenoszenia wykresów między oknami. Wykresy można zapisywać w plikach map bitowych i PDF albo kopiować do schowka jako mapy bitowe lub metapliki.  | nie dotyczy |
| [Eksplorator zmiennych](variable-explorer.md) | Sprawdzaj zmienne w zakresach globalnych lub specyficznych dla pakietów z możliwością wyświetlania sortowalnych tabel i eksportowania do pliku CSV. | nie dotyczy |
| [W pełni funkcjonalne debugowanie](debugging-r-in-visual-studio.md) | Obejmuje integrację z oknem interaktywnym. | [Debugowanie w Visual Studio](../debugger/debugger-feature-tour.md) |

Zobacz także [Często zadawane pytania](faq.md).

![ikona kamery dla wideo](../install/media/video-icon.png "Obejrzyj film") [Obejrzyj wideo (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ), aby zapoznać się z omówieniem rozszerzenia R Tools for Visual Studio (12 min 36 s). Zobacz też [więcej klipów wideo dotyczących narzędzi języka R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio).

## <a name="send-us-your-feedback"></a>Wyślij nam swoją opinię!

1. **Problemy w witrynie GitHub**: Najlepszym sposobem na skontaktowanie się z zespołem narzędzi RTVS jest [zarejestrowanie problemu w serwisie GitHub](https://github.com/Microsoft/RTVS/issues) lub użycie menu **Narzędzia języka R** > **Opinia**.

1. **Wyślij uśmiech/grymas**: Przy użyciu menu **Narzędzia języka R** > **Opinia** możesz szybko przesłać opinię i dołączyć pliki dziennika narzędzi RTVS ułatwiające zdiagnozowanie problemu. (Jeśli chcesz wysłać dzienniki oddzielnie, znajdziesz je w pliku *%temp%/RTVSlogs.zip*). Rejestrowanie jest wyłączone, jeśli nie wyrażono zgody na wysyłanie telemetrii programu Visual Studio przy użyciu polecenia menu **Pomoc** > **Opinia** > **Ustawienia** lub podczas instalacji.

1. **Poczta e-mail**: Możesz wysłać zespołowi bezpośrednią opinię na adres *rtvsuserfeedback (at) microsoft.com*.
