---
title: Omówienie protokołu serwera języka | Dokumenty firmy Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703099"
---
# <a name="language-server-protocol"></a>Language Server Protocol

## <a name="what-is-the-language-server-protocol"></a>Co to jest protokół Language Server Protocol?

Obsługa rozbudowanych funkcji edycji, takich jak automatyczne uzupełnianie kodu źródłowego lub **Przejdź do definicji** dla języka programowania w edytorze lub IDE jest tradycyjnie bardzo trudne i czasochłonne. Zazwyczaj wymaga zapisu modelu domeny (skaner, analizator, moduł sprawdzania typów, konstruktor i więcej) w języku programowania edytora lub IDE. Na przykład wtyczka Eclipse CDT, która zapewnia obsługę języka C/C++ w środowisku Eclipse IDE, jest napisana w języku Java, ponieważ sam eclipse IDE jest napisany w języku Java. Zgodnie z tym podejściem oznaczałoby implementowanie modelu domeny C/C++ w języku TypeScript dla programu Visual Studio Code i oddzielnego modelu domeny w języku C# dla programu Visual Studio.

Tworzenie modeli domeny specyficznych dla języka jest również o wiele łatwiejsze, jeśli narzędzie programistyczne może ponownie użyć istniejących bibliotek specyficznych dla języka. Jednak te biblioteki są zwykle implementowane w samym języku programowania (na przykład dobre modele domeny C/C++ są implementowane w języku C/C++). Integracja biblioteki C/C++ z edytorem napisanym w języku TypeScript jest technicznie możliwa, ale trudna do zrobienia.

### <a name="language-servers"></a>Serwery językowe

Innym podejściem jest uruchomienie biblioteki we własnym procesie i użycie komunikacji między procesami, aby z nią porozmawiać. Wiadomości wysyłane tam iz powrotem tworzą protokół. Protokół serwera języka (LSP) jest produktem standaryzacji wiadomości wymienianych między narzędziem programistycznym a procesem serwera języka. Używanie serwerów językowych lub demonów nie jest nowym ani nowatorskim pomysłem. Redaktorzy tacy jak Vim i Emacs robią to od jakiegoś czasu, aby zapewnić semantyczne wsparcie automatycznego uzupełniania. Celem LSP było uproszczenie tego rodzaju integracji i zapewnienie przydatnych ram dla ujawniania funkcji językowych na różne narzędzia.

Posiadanie wspólnego protokołu umożliwia integrację funkcji języka programowania z narzędziem programistycznym przy minimalnym zamieszaniu, ponownie korzystając z istniejącej implementacji modelu domeny języka. Back-end serwera językowego może być napisany w PHP, Python, lub Java i LSP pozwala łatwo zintegrować się z różnymi narzędziami. Protokół działa na wspólnym poziomie abstrakcji, dzięki czemu narzędzie może oferować usługi języka rozszerzonego bez konieczności pełnego zrozumienia niuansów specyficznych dla podstawowego modelu domeny.

## <a name="how-work-on-the-lsp-started"></a>Jak rozpoczęły się prace nad LSP

LSP ewoluował w czasie i dziś jest w wersji 3.0. Zaczęło się, gdy koncepcja serwera języka została odebrana przez OmniSharp, aby zapewnić zaawansowane funkcje edycji języka C#. Początkowo OmniSharp używał protokołu HTTP z ładunkiem JSON i został zintegrowany z kilkoma edytorami, w tym [z programem Visual Studio Code.](https://code.visualstudio.com)

Mniej więcej w tym samym czasie Microsoft zaczął pracować nad serwerem języka TypeScript, z pomysłem wspierania TypeScript w edytorach takich jak Emacs i Sublime Text. W tej implementacji edytor komunikuje się za pośrednictwem stdin/stdout z procesem serwera TypeScript i używa ładunku JSON inspirowanego protokołem debugera V8 dla żądań i odpowiedzi. Serwer TypeScript został zintegrowany z wtyczką TypeScript Sublime i kodem VS w celu zaawansowanej edycji TypeScript.

Po zintegrowaniu dwóch różnych serwerów językowych zespół programu VS Code rozpoczął eksplorowanie protokołu serwera języka wspólnego dla edytorów i adresów IP. Wspólny protokół umożliwia dostawcy języka utworzenie serwera pojedynczego języka, który może być zużywany przez różne adresy IP. Konsument serwera języka tylko raz musi zaimplementować stronę klienta protokołu. Powoduje to sytuację korzystną dla dostawcy języka i konsumenta języka.

Protokół serwera języka został uruchomiony z protokołem używanym przez serwer TypeScript, rozszerzając go o więcej funkcji językowych inspirowanych interfejsem API języka vs code. Protokół jest wspierany przez JSON-RPC do zdalnego wywoływania ze względu na jego prostotę i istniejące biblioteki.

Zespół kodu VS prototyped protokołu implementując kilka serwerów języka linter, które odpowiadają na żądania do lint (skanowanie) pliku i zwraca zestaw wykrytych ostrzeżeń i błędów. Celem było siekać plik, jak użytkownik edytuje w dokumencie, co oznacza, że będzie wiele linting żądań podczas sesji edytora. Warto było utrzymać serwer w górę i działa tak, że nowy proces linting nie trzeba uruchamiać dla każdego użytkownika edycji. Zaimplementowano kilka serwerów linter, w tym rozszerzenia ESLint i TSLint programu VS Code. Te dwa serwery linter są zaimplementowane w TypeScript/JavaScript i działają na node.js. Udostępniają one bibliotekę, która implementuje klienta i część serwera protokołu.

## <a name="how-the-lsp-works"></a>Jak działa LSP

Serwer języka działa w swoim własnym procesie, a narzędzia takie jak Visual Studio lub VS Code komunikują się z serwerem przy użyciu protokołu języka za pośrednictwem języka JSON-RPC. Kolejną zaletą serwera języka działającego w dedykowanym procesie jest unikanie problemów z wydajnością związanych z pojedynczym modelem procesu. Rzeczywistym kanałem transportu może być stdio, gniazda, nazwane potoki lub węzeł ipc, jeśli zarówno klient, jak i serwer są zapisywane w pliku Node.js.

Poniżej znajduje się przykład komunikacji narzędzia i serwera języka podczas rutynowej sesji edycji:

![diagram przepływu lsp](media/lsp-flow-diagram.png)

* **Użytkownik otwiera plik (określany jako dokument) w narzędziu**: Narzędzie powiadamia serwer języka, że dokument jest otwarty ("textDocument/didOpen"). Od teraz prawda o zawartości dokumentu nie jest już w systemie plików, ale jest przechowywana przez narzędzie w pamięci.

* **Użytkownik wprowadza zmiany**: Narzędzie powiadamia serwer o zmianie dokumentu ("textDocument/didChange"), a informacje semantyczne programu są aktualizowane przez serwer języka. W takim przypadku serwer języka analizuje te informacje i powiadamia narzędzie o wykrytych błędach i ostrzeżeniach ("textDocument/publishDiagnostics").

* **Użytkownik wykonuje "Przejdź do definicji" na symbolu w edytorze:** Narzędzie wysyła żądanie "textDocument/definition" z dwoma parametrami: (1) identyfikator URI dokumentu i (2) pozycja tekstowa, z której żądanie Przejdź do definicji zostało zainicjowane do serwera. Serwer odpowiada identyfikatorem URI dokumentu i położeniem definicji symbolu wewnątrz dokumentu.

* **Użytkownik zamyka dokument (plik)**: Powiadomienie "textDocument/didClose" jest wysyłane z narzędzia, informując serwer języka, że dokument nie jest już w pamięci i że bieżąca zawartość jest teraz aktualna w systemie plików.

W tym przykładzie pokazano, jak protokół komunikuje się z serwerem języka na poziomie funkcji edytora, takich jak "Przejdź do definicji", "Znajdź wszystkie odwołania". Typy danych używane przez protokół to edytor lub IDE "typy danych", takie jak aktualnie otwarty dokument tekstowy i położenie kursora. Typy danych nie są na poziomie modelu domeny języka programowania, który zwykle zapewnia abstrakcyjne drzewa składni i symbole kompilatora (na przykład rozwiązane typy, przestrzenie nazw, ...). Znacznie upraszcza to protokół.

Teraz przyjrzyjmy się "textDocument / definicja" wniosek bardziej szczegółowo. Poniżej znajdują się ładunki, które przechodzą między narzędziem klienta a serwerem języka dla żądania "Przejdź do definicji" w dokumencie C++.

Jest to żądanie:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Oto odpowiedź:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Z perspektywy czasu opisywanie typów danych na poziomie edytora, a nie na poziomie modelu języka programowania, jest jedną z przyczyn sukcesu protokołu serwera języka. Znacznie prostsze jest standaryzowanie identyfikatora URI dokumentu tekstowego lub pozycji kursora w porównaniu z standaryzacją abstrakcyjnych symboli drzewa składni i kompilatora w różnych językach programowania.

Gdy użytkownik pracuje z różnymi językami, program VS Code zazwyczaj uruchamia serwer języka dla każdego języka programowania. Poniższy przykład przedstawia sesję, w której użytkownik pracuje nad plikami Java i SASS.

![java i sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Możliwości

Nie każdy serwer języka może obsługiwać wszystkie funkcje zdefiniowane przez protokół. W związku z tym klient i serwer ogłasza ich obsługiwany zestaw funkcji za pośrednictwem "możliwości". Na przykład serwer informuje, że może obsługiwać żądanie "textDocument/definition", ale może nie obsługiwać żądania "obszar roboczy/symbol". Podobnie klienci mogą ogłosić, że są w stanie dostarczyć powiadomienia "o zapisaniu" przed zapisaniem dokumentu, dzięki czemu serwer może obliczyć zmiany tekstowe, aby automatycznie sformatować edytowany dokument.

## <a name="integrating-a-language-server"></a>Integracja serwera językowego

Rzeczywista integracja serwera języka z określonym narzędziem nie jest zdefiniowana przez protokół serwera języka i pozostaje w lewo do implementorów narzędzia. Niektóre narzędzia integrują serwery językowe ogólnie, mając rozszerzenie, które można uruchomić i rozmawiać z dowolnego rodzaju serwera języka. Inne, takie jak VS Code, utworzyć rozszerzenie niestandardowe na serwer języka, tak aby rozszerzenie jest nadal w stanie zapewnić niektóre funkcje języka niestandardowego.

Aby uprościć implementację serwerów i klientów języka, istnieją biblioteki lub zestawy SDK dla części klienta i serwera. Biblioteki te są dostępne dla różnych języków. Na przykład istnieje [moduł npm klienta języka](https://www.npmjs.com/package/vscode-languageclient) w celu ułatwienia integracji serwera języka z rozszerzeniem kodu VS i innym [modułem npm serwera języka](https://www.npmjs.com/package/vscode-languageserver) do pisania serwera języka przy użyciu node.js. Jest to bieżąca [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) bibliotek pomocy technicznej.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Korzystanie z protokołu serwera języka w programie Visual Studio

* [Dodawanie rozszerzenia protokołu serwera języka](adding-an-lsp-extension.md) — dowiedz się więcej o integrując serwer języka z programem Visual Studio.
