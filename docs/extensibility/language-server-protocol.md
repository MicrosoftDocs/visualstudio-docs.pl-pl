---
title: Omówienie protokołu serwera języka | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703099"
---
# <a name="language-server-protocol"></a>Language Server Protocol

## <a name="what-is-the-language-server-protocol"></a>Co to jest protokół serwera języka?

Obsługa zaawansowanych funkcji edycji, takich jak Autouzupełnianie kodu źródłowego, lub **Przejdź do definicji** dla języka programowania w edytorze lub IDE jest tradycyjnie bardzo trudne i czasochłonne. Zwykle wymaga to zapisania modelu domeny (skanera, analizatora, sprawdzania typu, konstruktora i innych) w języku programowania edytora lub IDE. Na przykład wtyczka CDT, która zapewnia obsługę języka C/C++ w środowisku IDE, jest zapisywana w języku Java od momentu, w którym sam IDE jest zapisywana w języku Java. Zastosowanie tej metody oznacza wdrożenie modelu domeny C/C++ w TypeScript for Visual Studio kodzie i oddzielnego modelu domeny w języku C# dla programu Visual Studio.

Tworzenie modeli domen specyficznych dla języka jest również znacznie łatwiejsze, jeśli narzędzie programistyczne może ponownie użyć istniejących bibliotek specyficznych dla języka. Jednak te biblioteki są zwykle zaimplementowane w języku programowania (na przykład dobry modele domen C/C++ są implementowane w C/C++). Integrowanie biblioteki C/C++ z edytorem pisanym w języku TypeScript jest technicznie możliwe, ale trudne do zrobienia.

### <a name="language-servers"></a>Serwery języka

Innym rozwiązaniem jest uruchomienie biblioteki w osobnym procesie i używanie komunikacji między procesami w celu komunikowania się z nią. Komunikaty wysłane z powrotem i są zgodne z protokołem. Language Server Protocol (LSP) to iloczyn standaryzacji komunikatów wymienianych między narzędziem deweloperskim i procesem serwera języka. Korzystanie z serwerów języka lub Demons nie jest nowym lub nową koncepcją. Edytory, takie jak vim i Emacs:, wykonywały to przez pewien czas w celu zapewnienia obsługi semantyki automatycznego uzupełniania. Celem dostawcy LSP było uproszczenie tego rodzaju integracji i zapewnienie przydatnej struktury umożliwiającej udostępnianie funkcji języka w różnych narzędziach.

Wspólny protokół umożliwia integrację funkcji języka programowania w narzędziu programistycznym o minimalnej Fuss przez ponowne użycie istniejącej implementacji modelu domeny języka. Zaplecze serwera języka można napisać w języku PHP, Python lub Java, a dostawcy LSP, dzięki czemu można łatwo zintegrować go z różnymi narzędziami. Protokół działa na wspólnym poziomie abstrakcji, dzięki czemu narzędzie może oferować zaawansowane usługi językowe bez potrzeby pełnego zrozumienia wszystkie szczegóły specyficznych dla podstawowego modelu domeny.

## <a name="how-work-on-the-lsp-started"></a>Jak działa na serwerze LSP

LSP został rozwijający się wraz z upływem czasu, a dzisiaj jest w wersji 3,0. Zostało uruchomione, gdy koncepcji serwera języka zostało pobrane przez OmniSharp, aby zapewnić zaawansowane funkcje edycji dla języka C#. Początkowo OmniSharp użył protokołu HTTP z ładunkiem JSON i został zintegrowany z kilkoma edytorami, w tym [Visual Studio Code](https://code.visualstudio.com).

W tym samym czasie firma Microsoft rozpoczęła pracę na serwerze języka TypeScript, z pomysłem obsługi języka TypeScript w edytorach, takich jak Emacs: i subwapno. W tej implementacji Edytor komunikuje się za pośrednictwem stdin/stdout z procesem serwera TypeScript i używa ładunku JSON inspirowanego protokołem debugera V8 dla żądań i odpowiedzi. Serwer TypeScript został zintegrowany z wtyczką podwapna języka TypeScript i VS Code, aby sformatować edycję języka TypeScript.

Po zintegrowaniu dwóch różnych serwerów języka zespół VS Code rozpoczął się w celu eksplorowania protokołu wspólnego serwera języka dla edytorów i środowisk IDE. Typowy protokół umożliwia dostawcy języka tworzenie jednego serwera języka, który może być używany przez różne środowisk IDE. Klient serwera języka musi tylko raz zaimplementować po stronie klienta. Powoduje to sytuację wygraną zarówno dla dostawcy języka, jak i konsumenta języka.

Protokół serwera języka został uruchomiony z protokołem używanym przez serwer TypeScript, rozszerzając go o więcej funkcji języka inspirowanych interfejsem API języka VS Code. Ten protokół jest objęty usługą JSON-RPC dla zdalnego wywołania z powodu prostoty i istniejących bibliotek.

VS Code zespół zaprototypuje protokół, implementując kilka serwerów języka Linter, które reagują na żądania lint (Skanuj) plik i zwracają zestaw wykrytych ostrzeżeń i błędów. Celem było lint pliku jako edycji użytkownika w dokumencie, co oznacza, że w trakcie sesji edytora będzie wiele żądań Zaznaczanie błędów. Warto zachować i uruchomić serwer, aby nowy proces Zaznaczanie błędów nie musiał być uruchamiany dla każdej edycji użytkownika. Wdrożono kilka serwerów Linter, w tym VS Code ESLint i TSLint rozszerzenia. Te dwa serwery Linter są implementowane w języku TypeScript/JavaScript i uruchamiane na Node.js. Korzystają one z biblioteki implementującej składnik klienta i serwer.

## <a name="how-the-lsp-works"></a>Jak działa LSP

Serwer języka jest uruchamiany we własnym procesie, a narzędzia takie jak Visual Studio lub VS Code komunikują się z serwerem przy użyciu protokołu języka over JSON-RPC. Inną zaletą działania serwera języka w dedykowanym procesie jest uniknięcie problemów z wydajnością związanych z pojedynczym modelem procesów. Rzeczywistym kanałem transportu może być stdio, Sockets, nazwane potoki lub węzeł IPC, jeśli zarówno klient, jak i serwer są zapisywana w Node.js.

Poniżej przedstawiono przykład sposobu komunikacji narzędzia i serwera języka podczas rutynowej sesji edytowania:

![Diagram przepływu dostawcy LSP](media/lsp-flow-diagram.png)

* **Użytkownik otwiera plik (nazywany dokumentem) w narzędziu**: Narzędzie powiadamia serwer języka o otwartym dokumencie ("TextDocument/didOpen"). Od teraz w rzeczywistości prawdziwie dotyczące zawartości dokumentu nie ma już w systemie plików, ale zachowano narzędzie w pamięci.

* **Użytkownik wprowadza zmiany**: Narzędzie powiadamia serwer o zmianie dokumentu ("TextDocument/didChange"), a informacje o semantyce programu są aktualizowane przez serwer języka. W takim przypadku serwer języka analizuje te informacje i powiadamia narzędzie z wykrytymi błędami i ostrzeżeniami ("TextDocument/publishDiagnostics").

* **Użytkownik wykonuje polecenie "przejdź do definicji" w symbolu w edytorze**: narzędzie wysyła żądanie "TextDocument/Definition" z dwoma parametrami: (1) identyfikator URI dokumentu oraz (2) położenie tekstu, z którego żądanie przejdź do definicji zostało zainicjowane na serwerze. Serwer odpowiada identyfikatorowi URI dokumentu i pozycji definicji symbolu wewnątrz dokumentu.

* **Użytkownik zamknie dokument (plik)**: powiadomienie "TextDocument/didClose" jest wysyłane z tego narzędzia, informując serwer języka, że dokument nie znajduje się już w pamięci i że bieżąca zawartość jest teraz aktualna w systemie plików.

Ten przykład ilustruje sposób komunikowania się protokołu z serwerem języka na poziomie funkcji edytora, takich jak "przejdź do definicji", "Znajdź wszystkie odwołania". Typy danych używane przez protokół to edytor lub środowisko IDE typu danych, takie jak aktualnie otwarty dokument tekstowy i położenie kursora. Typy danych nie są na poziomie modelu domeny języka programowania, który zwykle udostępnia abstrakcyjne drzewa składniowe i symbole kompilatora (na przykład rozpoznane typy, przestrzenie nazw,...). Upraszcza to protokół.

Teraz przyjrzyjmy się żądaniu "TextDocument/Definition" w bardziej szczegółowy sposób. Poniżej znajdują się ładunki między narzędziem klienta i serwerem języka dla żądania "przejdź do definicji" w dokumencie języka C++.

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

Jest to odpowiedź:

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

W Spoglądając wstecz, opisujące typy danych na poziomie edytora, a nie na poziomie modelu języka programowania, jest jedną z przyczyn sukcesu protokołu serwera języka. Jest to znacznie prostsze do standaryzacji identyfikatora URI dokumentu tekstowego lub położenia kursora w porównaniu z standaryzacją abstrakcyjnego drzewa składni i symboli kompilatora w różnych językach programowania.

Gdy użytkownik pracuje z innymi językami, VS Code zwykle uruchamia serwer języka dla każdego języka programowania. W poniższym przykładzie pokazano sesję, w której użytkownik pracuje na plikach Java i SASS.

![Java i Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Możliwości

Nie każdy serwer języka może obsługiwać wszystkie funkcje zdefiniowane przez protokół. W związku z tym klient i serwer ogłaszają obsługiwane przez niego funkcje. Na przykład serwer ogłasza, że może obsłużyć żądanie "TextDocument/Definition", ale może nie obsługiwać żądania "obszar roboczy/symbol". Podobnie klienci mogą poinformować, że mogą podać powiadomienia "o zapisaniu" przed zapisaniem dokumentu, aby serwer mógł obliczać edycje tekstu w celu automatycznego formatowania edytowanego dokumentu.

## <a name="integrating-a-language-server"></a>Integrowanie serwera języka

Rzeczywista integracja serwera języka z określonym narzędziem nie jest definiowana przez protokół serwera języka i jest pozostawiona do realizatorów narzędzi. Niektóre narzędzia integrują serwery języka ogólnie poprzez posiadanie rozszerzenia, które może rozpocząć pracę i komunikować się z dowolnym rodzajem serwera języka. Inne, takie jak VS Code, tworzą rozszerzenie niestandardowe dla każdego serwera języka, aby rozszerzenie nadal mogło udostępniać niestandardowe funkcje językowe.

Aby uprościć implementację serwerów języków i klientów, istnieją biblioteki lub zestawy SDK dla części klienta i serwera. Te biblioteki są dostępne dla różnych języków. Można na przykład użyć [modułu npm klienta języka](https://www.npmjs.com/package/vscode-languageclient) , aby ułatwić integrację serwera języka z rozszerzeniem vs Code i innego [modułu npm serwera języka](https://www.npmjs.com/package/vscode-languageserver) w celu zapisania serwera języka przy użyciu Node.js. Jest to bieżąca [Lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) bibliotek obsługi.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Korzystanie z protokołu języka serwera w programie Visual Studio

* [Dodawanie rozszerzenia protokołu serwera języka](adding-an-lsp-extension.md) — informacje o integrowaniu serwera języka z Visual Studio.
