---
title: Language Server Protocol — omówienie | Dokumentacja firmy Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f6f114d7165b85051092234ea33dfc7f73e1487
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309626"
---
# <a name="language-server-protocol"></a>Language Server Protocol

## <a name="what-is-the-language-server-protocol"></a>Co to jest Language Server Protocol?

Pomocnicze zaawansowane funkcje edycji, takie jak auto uzupełnianie kodu źródłowego lub **przejdź do definicji** dla języka programowania, w edytorze IDE jest tradycyjnie bardzo trudna i czasochłonna. Zwykle wymaga zapisywania modelu domeny (skaner, analizator składni, sprawdzanie typu, konstruktora i inne) w języku programowania w IDE lub edytora. Na przykład wtyczki Eclipse czasu CDT, który zapewnia obsługę języka C/C++ w środowisku IDE programu Eclipse jest napisany w języku Java, ponieważ środowisko Eclipse IDE, sama jest napisany w języku Java. Następujące takie podejście, oznaczałoby to Implementowanie modelu domeny C/C++ w TypeScript dla programu Visual Studio Code i modelu w oddzielnej domenie C# dla programu Visual Studio.

Tworzenie modeli specyficznych dla języka domeny są również znacznie łatwiejsze, jeśli narzędzie programistyczne umożliwiające ponowne użycie istniejącej biblioteki charakterystyczne dla języka. Jednak te biblioteki zwykle są implementowane w języku programowania (na przykład dobrą C/C++ domeny modeli są implementowane w języku C/C++). Integrowanie bibliotekę języka C/C++ edytor, który został napisany w TypeScript jest technicznie możliwe, ale ciężko.

### <a name="language-servers"></a>Serwery języka

Innym rozwiązaniem jest uruchomienie biblioteki w swoim własnym procesie i użyj komunikacji między procesami, aby porozmawiać do niego. Komunikaty wysyłane do i z powrotem tworzą protokołu. Protokołu language server protocol (LSP) jest wynikiem standaryzacji wiadomości wymieniane między narzędziem do projektowania i proces serwera języka. Używanie serwerów języka lub demons nie jest pomysłem nowych lub nowej. Edytory, takich jak Vim i Emacs ma zostały w ten sposób przez pewien czas zapewnić obsługę semantyki automatycznego uzupełniania. Celem LSP była możliwość uproszczenia tego rodzaju integracji i oferują przydatna strukturę umożliwiającą udostępnianie funkcje językowe z szeroką gamą narzędzi.

Mających wspólny protokół umożliwia integrację programowania funkcje języka do narzędzia tworzenia, z minimalnym problemów dzięki ponownemu wykorzystaniu istniejącą implementację programu języka modelu domeny. Język serwera zaplecza może być napisana w PHP, Python lub Java i LSP umożliwia mu można łatwo integruje się z szeroką gamą narzędzi. Protokół działa na wspólnej poziomie abstrakcji, tak, aby narzędzie zaoferować bogaty język usługi bez konieczności pełni poznać wszystkie szczegóły specyficzne dla podstawowego modelu domeny.

## <a name="how-work-on-the-lsp-started"></a>Sposób działania na LSP pracę

Czasem ewoluował LSP i obecnie jest w wersji 3.0. Jego uruchomienia, gdy pojęcia języka serwera zostało odebrane przez technologię OmniSharp aby zapewnić zaawansowane funkcje edycji dla C#. Początkowo technologię OmniSharp używany protokół HTTP z ładunkiem JSON i zostało zintegrowane kilka edytorów, w tym [programu Visual Studio Code](https://code.visualstudio.com).

Tym samym czasie Microsoft zaczęła pracy na serwerze języka TypeScript z myślą o obsłudze TypeScript w edytorach, takich jak Emacs i Sublime Text. W tej implementacji redaktorem komunikuje się za pośrednictwem stdin/stdout z procesem serwera TypeScript i używany przez protokół debuger V8 ładunek JSON dla żądań i odpowiedzi. Serwer TypeScript zostało zintegrowane TypeScript Sublime wtyczki i program VS Code do edycji sformatowanego TypeScript.

Po posiadające zintegrowany dwa serwery w innym języku, program VS Code zespół zaczął poznać typowe protokołu language server protocol edytorami i środowiskami IDE. Wspólny protokół umożliwia dostawcy języka utworzyć serwer jednego języka, które mogą być używane przez różne środowiska IDE. Konsument języka serwera ma tylko raz zaimplementować protokół po stronie klienta. Skutkuje to sytuacja win win zarówno dla dostawcy języka i konsumentów języka.

Protokołu language server protocol pracę z usługą protokół używany przez serwer TypeScript, rozszerzając go za pomocą większej liczby funkcji języka przez język programu VS Code interfejsu API. Protokół jest obsługiwane przy użyciu wywołania JSON-RPC dla zdalnego wywołania ze względu na prostotę i istniejących bibliotek.

VS kodu zespołu prototypowane protokołu implementując kilka serwerów linter języka, które odpowiadanie na żądania do przeanalizowania linterem (skanowanie) pliku i zwrócić zestaw wykryte ostrzeżenia i błędy. Celem było do przeanalizowania linterem pliku jako użytkownik dokona edycji w dokumencie, co oznacza, że będzie istniało wiele żądań Zaznaczanie błędów podczas sesji przy użyciu edytora. Jego miało sens, aby zachować server do pracy, aby nowy proces Zaznaczanie błędów nie musiał można uruchomić dla każdej modyfikacji użytkownika. Kilka serwerów linter zostały wdrożone z tym program VS Code ESLint i TSLint rozszerzenia. Te dwa serwery linter są zaimplementowane w języku TypeScript/JavaScript i uruchom na języku Node.js. Współużytkują one bibliotekę, która implementuje klientów i serwerów część protokołu.

## <a name="how-the-lsp-works"></a>Jak działa LSP

Serwer języka jest uruchamiany w swoim własnym procesie i narzędzi, takich jak Visual Studio lub programu VS Code komunikować się z serwerem przy użyciu protokołu language za pośrednictwem wywołania RPC JSON. Inną zaletą obsługi w dedykowanym procesie serwera języka to uniknąć problemów z wydajnością związanych z modelem jednego procesu. Kanał transportowy rzeczywiste może być stdio —, gniazda, nazwanych potoków lub węzeł ipc Jeśli klienta i serwera są zapisywane w środowisku Node.js.

Poniżej przedstawiono przykład sposobu narzędzie a serwerem języka komunikację w ramach procedury edytuje sesji:

![diagram przepływu LSP](media/lsp-flow-diagram.png)

* **Użytkownik otwiera plik (nazywane dokumentu) w narzędziu**: Narzędzie informuje serwer języka czy dokument jest otwarty ("textDocument/didOpen"). Od teraz prawdziwych informacji o zawartości dokumentu nie jest już w systemie plików, ale przechowywane za pomocą narzędzia w pamięci.

* **Użytkownik dokona edycji**: Narzędzie informuje serwer o zmianie dokumentów ("textDocument/didChange"), a następnie informacji semantycznych programu jest aktualizowana przez serwer języka. Ponieważ tak się stanie, serwer języka analizuje te informacje i powiadamia narzędzie z wykrytych błędów i ostrzeżeń ("textDocument/publishDiagnostics").

* **Użytkownik wykonuje "Przejdź do definicji" w symbolu w edytorze**: Narzędzie wysyła żądanie "textDocument/definicji" z dwoma parametrami: (1 identyfikator URI dokumentu i (2 położenie tekstu, z której zainicjowano przejdź do definicji żądania do serwera. W odpowiedzi serwer podaje identyfikator URI dokumentu i położenie definicji symbolu w dokumencie.

* **Użytkownik zamyka dokument (plik)** : Za pomocą narzędzia informowanie serwera języka, który dokument jest już w pamięci, które bieżącą zawartość jest teraz na bieżąco w systemie plików jest wysyłane powiadomienie "textDocument/didClose".

Ten przykład ilustruje, jak protokół komunikuje się z serwerem języka na poziomie funkcji edytora, takich jak "Przejdź do definicji", "Znajdź wszystkie odwołania". Typy danych używany przez protokół to edytor lub IDE "typy danych", takie jak dokument tekstowy aktualnie otwarte i położenie kursora. Typy danych nie są na poziomie modelu programowania domeny języka, który zapewni zwykle drzewa abstrakcyjnej składni i kompilatora symbole (na przykład rozpoznać typy, przestrzenie nazw,...). Znacznie upraszcza protokołu.

Teraz Przyjrzyjmy się bardziej szczegółowo w żądaniu "textDocument/definicji". Poniżej przedstawiono ładunków, których przełączać się między narzędzia klienta i serwera języka dla żądania "Przejdź do definicji" w dokumencie języka C++.

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

Jest to odpowiedzi:

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

Spoglądając wstecz zawierająca opis typów danych na poziomie edytora, a nie na poziomie modelu języka programowania jest jednym z powodów, dla pomyślnego działania protokołu language server protocol. Jest znacznie prostsza do standaryzacji dokument tekstowy identyfikator URI lub pozycji kursora w porównaniu z standaryzacji abstrakcyjnej składni drzewa kompilatora symbole w różnych językach programowania.

Podczas pracy w różnych językach, program VS Code rozpoczyna się zwykle serwer języka każdy język programowania. W poniższym przykładzie pokazano sesji, w którym pracuje użytkownik języka Java i rozszerzenie SASS plików.

![Java i sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Możliwości

Nie każdy serwer język może obsłużyć wszystkie funkcje zdefiniowane przez protokół. W związku z tym klient i serwer ogłasza ich zestaw funkcji obsługiwanych przez "capabilities". Na przykład serwer ogłasza, aby go mogą obsługiwać żądania "textDocument/definicji", ale go nie może obsłużyć żądanie "w obszarze roboczym na symbol". Podobnie klienci ogłaszamy czy możliwość zapewnienia "chcesz zapisać" powiadomienia przed zapisaniem dokumentu, dzięki czemu serwer może obliczyć tekstową zmiany można automatycznie sformatować dokumentu edytowanego.

## <a name="integrating-a-language-server"></a>Integrowanie serwera języka

Rzeczywiste integracji serwera języka do określonego narzędzia nie jest zdefiniowany przez protokołu language server protocol i pozostanie na implementors narzędzia. Niektóre narzędzia integracji języka serwerów objęty przez rozszerzenie, które można uruchomić i komunikować się z dowolnego rodzaju języka serwera. Inne, takich jak program VS Code, utworzyć niestandardowego rozszerzenia na serwer języka, aby rozszerzenie jest nadal w stanie zapewnić niektóre funkcje języka niestandardowego.

Aby uprościć implementacji języka serwerów i klientów, znajdują się biblioteki lub zestawów SDK dla części klienta i serwera. Tych bibliotek znajdują się w różnych językach. Na przykład istnieje [moduł npm klienta języka](https://www.npmjs.com/package/vscode-languageclient) działają nawet pod dużym integracji serwera języka rozszerzenie programu VS Code i innym [moduł npm serwera języka](https://www.npmjs.com/package/vscode-languageserver) do zapisania serwera języka przy użyciu środowiska Node.js. Jest to bieżący [listy](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) bibliotek pomocy technicznej.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>W programie Visual Studio przy użyciu protokołu Language Server Protocol

* [Dodawanie rozszerzenia protokołu Language Server Protocol](adding-an-lsp-extension.md) — Dowiedz się więcej o integrację serwera język w programie Visual Studio.
