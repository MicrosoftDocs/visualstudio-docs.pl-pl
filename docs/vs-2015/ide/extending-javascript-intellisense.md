---
title: Rozszerzenie JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- JavaScript, intellisense object
- extending JavaScript IntelliSense
- customizing JavaScript IntelliSense
- JavaScript, extending IntelliSense
- IntelliSense [JavaScript], extending
ms.assetid: 004e1ab6-bd7a-4327-9e01-89b9be96ba2f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf16b6fdc307e11875f30cfad6e4bb35580b0b04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665749"
---
# <a name="extending-javascript-intellisense"></a>Rozszerzanie JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja rozszerzalności JavaScript IntelliSense umożliwia dostosowywanie wyników IntelliSense w edytorze JavaScript dla bibliotek innych firm. Może to poprawić doświadczenie deweloperów korzystających z tych bibliotek.

 Usługa języka JavaScript udostępnia funkcje IntelliSense dla bibliotek języka JavaScript innych firm, które są dodawane do projektu. W przypadku większości bibliotek uzupełnianie instrukcji jest dostarczane automatycznie przez usługę języka. Na poniższej ilustracji przedstawiono przykład uzupełniania instrukcji:

 ![Przykład uzupełniania instrukcji](../ide/media/js-intellisense-completion.png "js_intellisense_completion")

 Jeśli biblioteka zawiera opisy zmiennych, funkcji i obiektów w standardowych tagach komentarzy języka JavaScript (//), automatycznie korzystamy z funkcji rozszerzalności IntelliSense, które udostępniają informacje opisowe w oknie podręcznym, które pojawia się po prawej stronie elementów na liście uzupełniania lub po wpisaniu nawiasu otwierającego w wywołaniu funkcji. Komentarze w polu podręcznym zawierają opis elementu członkowskiego. Poniższy przykład pokazuje podręczny pole listy uzupełniania.

 ![Przykład szybkiej informacji w oknie&#45;podręcznym](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")

 Aby dodatkowo ulepszyć środowisko deweloperskie, możesz chcieć podać informacje o typie dla deweloperów w polu podręcznym. Możesz podać informacje o typie, używając [komentarzy dokumentacji XML](../ide/xml-documentation-comments-javascript.md) języka JavaScript zamiast standardowych tagów komentarzy. Komentarze dokumentacji XML są dodawane przy użyciu tagów z komentarzem z potrójnym ukośnikiem (///) i zdefiniowanego zestawu elementów XML.

 Alternatywnie można podać informacje o typie przy użyciu rozszerzalności JavaScript IntelliSense. Ta funkcja umożliwia dostosowywanie wyników IntelliSense przez tworzenie rozszerzeń języka JavaScript i dodawanie ich do kontekstu skryptu. W rozszerzeniu, który jest plikiem JavaScript, subskrybujesz zdarzenia, które są udostępniane przez obiekt `intellisense` usługi językowej. Rozszerzalność kodu JavaScript IntelliSense jest preferowanym rozwiązaniem dla bibliotek, Jeśli wzorzec zachowania w bibliotece uniemożliwia usłudze języka JavaScript podawanie żądanego poziomu obsługi technologii IntelliSense i jeśli alternatywą dla deklaratywnego kodu XML Komentarze do dokumentacji są również zbędne. Dostosowując wyniki funkcji IntelliSense, można utworzyć pierwsze środowisko funkcji IntelliSense, niezależnie od wzorców zachowania, które mogą ograniczać domyślne możliwości usługi językowej. Aby uzyskać więcej informacji, zobacz [uzupełnianie instrukcji dla identyfikatorów](../ide/statement-completion-for-identifiers.md).

## <a name="adding-an-extension-to-the-script-context"></a>Dodawanie rozszerzenia do kontekstu skryptu
 Aby rozszerzenie IntelliSense zostało wykonane, należy je dodać do bieżącego kontekstu skryptu. Rozszerzenie może być automatycznie dodawane do kontekstu skryptu przez mechanizm odnajdywania automatycznego lub można dodać rozszerzenie do kontekstu skryptu ręcznie przy użyciu grup referencyjnych lub dyrektywy referencyjnej.

 Mechanizm automatycznego odnajdywania umożliwia usłudze języka Automatyczne znajdowanie rozszerzeń, które są zgodne z *biblioteką*konwencji nazewnictwa plików. IntelliSense. js, które znajdują się w tym samym katalogu, w którym znajduje się rozszerzenie dotyczy. Na przykład prawidłowe rozszerzenie biblioteki jQuery to jQuery. IntelliSense. js. W przypadku bardziej restrykcyjnych rozszerzeń jQuery można użyć nazw plików, takich jak jQuery-1.7.1. IntelliSense. js (rozszerzenie specyficzne dla wersji) lub jQuery. UI. IntelliSense. js (rozszerzenie dla biblioteki jQuery z zakresem). Najbardziej restrykcyjna wersja rozszerzenia jest używana w przypadku znalezienia więcej niż jednego rozszerzenia dla danej biblioteki.

 Jeśli chcesz użyć rozszerzenia dla wszystkich plików projektu JavaScript, możesz zamiast tego dodać rozszerzenie do grupy odwołania. Istnieje kilka typów grup odniesienia, które zawierają odwołania niejawne i te, które zawierają dedykowane odwołania do procesu roboczego. Aby dodać rozszerzenie, zazwyczaj należy dodać plik jako niejawną grupę odwołania, **niejawny (Windows)** , **niejawny (sieć Web)** . Odwołania niejawne znajdują się w zakresie dla każdego pliku. js otwartego w edytorze kodu. Korzystając z tej metody, należy dodać zarówno rozszerzenie, jak i plik, który uzupełnia rozszerzenie.

 Użyj strony **IntelliSense** okna dialogowego **Opcje** , aby dodać rozszerzenie jako grupę referencyjną. Dostęp do strony **IntelliSense** można uzyskać, wybierając pozycję **Narzędzia**, **Opcje** na pasku menu, a następnie wybierając **Edytor tekstu**, **JavaScript**, **IntelliSense**, **odwołania**. Aby uzyskać więcej informacji na temat grup referencyjnych, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md) i [Opcje, Edytor tekstu, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

 Jeśli chcesz użyć rozszerzenia dla określonego zestawu plików, użyj dyrektywy Reference. Korzystając z tej metody, należy odwołać się zarówno do rozszerzenia, jak i do pliku, który uzupełnia rozszerzenie. Aby uzyskać informacje na temat używania dyrektywy Reference, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="handling-intellisense-events"></a>Obsługa zdarzeń IntelliSense
 Funkcja rozszerzalności pozwala dostosować wyniki funkcji IntelliSense, subskrybując zdarzenia, takie jak `statementcompletion` zdarzenie usługi językowej `intellisense` obiektu. W poniższym przykładzie pokazano proste rozszerzenie, które jest używane przez usługę języka do ukrycia elementów członkowskich, które zaczynają się od znaku podkreślenia od zakończenia instrukcji. Ten kod jest zawarty w underscorefilter. js i znajduje się w folderze \\ \\*ścieżka instalacji programu Visual Studio*\JavaScript\References.

```javascript
intellisense.addEventListener('statementcompletion', function (event) {
    if (event.targetName === "this") return;

    var filterRegex;

    if (event.target === undefined || event.target === window)
        filterRegex = /^_.*\d{2,}/;
    else
        filterRegex = /^_.*/;

    event.items = event.items.filter(function (item) {
        return !filterRegex.test(item.name);
    });
});
```

 W poprzednim kodzie rozszerzenie sprawdza [Właściwość TargetName](#TargetName) i [właściwość target](#Target) obiektu zdarzenia `statementcompletion`, aby wykluczyć obiekty takie jak `this` i `window` oraz aby upewnić się, że lista uzupełniania instrukcji może być określonej. Jeśli można zidentyfikować listę uzupełniania, rozszerzenie aktualizuje kolekcję [właściwości elementów](#Items) uzupełniania, filtrując elementy członkowskie, które zaczynają się od znaku podkreślenia.

 Aby uzyskać dodatkowe przykłady, zajrzyj do folderu \\ \\*ścieżka instalacji programu Visual Studio*\JavaScript\References. Plik showPlainComments. js w tym folderze zawiera przykłady użycia innych zdarzeń w celu zapewnienia domyślnej obsługi technologii IntelliSense dla standardowych tagów komentarzy w języku JavaScript (//). Podobnie jak underscorefilter. js, showPlainComments. js jest już dostępny jako rozszerzenie robocze i można zobaczyć uzyskane informacje IntelliSense w przypadku używania tagów komentarzy w kodzie dla zmiennych, funkcji i obiektów. Aby uzyskać więcej przykładów, zobacz [przykłady kodu](#CodeExamples).

> [!WARNING]
> Jeśli zmodyfikujesz pliki rozszerzeń dołączone do programu Visual Studio, możesz wyłączyć obsługę języka JavaScript IntelliSense lub funkcję obsługiwaną przez rozszerzenie.

 W kodzie rozszerzenia można utworzyć programy obsługi dla następujących typów zdarzeń przy użyciu `addEventListener`:

- `statementcompletion`, który dodaje procedurę obsługi dla zdarzenia ukończenia instrukcji. Uzupełnianie instrukcji zawiera listę elementów członkowskich określonego typu, które pojawiają się po wpisaniu znaku specjalnego, takiego jak kropka (.), lub listę identyfikatorów, które pojawiają się podczas wpisywania lub po naciśnięciu klawiszy CTRL + J. Program obsługi odbiera obiekt zdarzenia typu `CompletionEvent`, który obsługuje następujące elementy członkowskie: [Właściwość Items](#Items), [TargetName](#Target), [TargetName](#TargetName)i [SCOPE Property](#Scope).

- `signaturehelp`, który dodaje procedurę obsługi dla informacji o parametrach IntelliSense. Informacje o parametrach umożliwiają uzyskanie informacji o liczbie, nazwach i typach parametrów wymaganych przez funkcję. Program obsługi odbiera obiekt zdarzenia typu `SignatureHelpEvent`, który obsługuje następujące elementy członkowskie: [Właściwość docelowa](#Target), właściwość [ParentObject](#ParentObject), właściwość [functionComments](#FunctionComments), właściwość [functionHelp](#FunctionHelp).

- `statementcompletionhint`, który dodaje procedurę obsługi dla szybkich informacji IntelliSense. W oknie podręcznym szybkie informacje zostanie wyświetlona kompletna deklaracja identyfikatorów w kodzie. Program obsługi odbiera obiekt zdarzenia typu `CompletionHintEvent`, który obsługuje następujące elementy członkowskie: [Właściwość completionItem](#CompletionItem)i [Właściwość symbolHelp](#SymbolHelp).

  Przykłady pokazujące funkcje IntelliSense, takie jak uzupełnianie instrukcji, informacje o parametrach i szybkie informacje, można znaleźć w temacie [using IntelliSense](../ide/using-intellisense.md).

> [!NOTE]
> W języku JavaScript szybkie informacje odnoszą się do okna podręcznego, które pojawia się po prawej stronie listy uzupełniania. Nie można ręcznie wywołać szybkich informacji.

## <a name="intellisenseObject"></a>Obiekt IntelliSense
 W poniższej tabeli przedstawiono funkcje, które są dostępne dla obiektu `intellisense`. Obiekt `intellisense` jest dostępny tylko w czasie projektowania.

|Funkcja|Opis|
|--------------|-----------------|
|`addEventListener(type, handler);`|Dodaje procedurę obsługi zdarzeń dla zdarzenia IntelliSense.<br /><br /> `type` jest wartością ciągu. Prawidłowe wartości to `statementcompletion`, `signaturehelp` i `statementcompletionhint`.<br /><br /> `handler` to funkcja obsługi zdarzeń, która odbiera obiekt zdarzenia jednego z następujących typów:<br /><br /> `CompletionEvent` -    używany dla zdarzenia `statementcompletion`.<br />`SignatureHelpEvent` -    używany dla zdarzenia `signaturehelp`.<br />`CompletionHintEvent` -    używany dla zdarzenia `statementcompletionhint`.<br /><br /> Przykłady korzystające z tej funkcji znajdują się w sekcji [przykłady kodu](#CodeExamples).|
|`annotate(obj, doc);`|Określa dokumentację obiektu przez skopiowanie komentarzy do dokumentacji z jednego obiektu do innego obiektu.<br /><br /> `obj` określa obiekt, do którego ma zostać skopiowana dokumentacja.<br /><br /> `doc` określa obiekt, z którego ma zostać skopiowana dokumentacja.<br /><br /> Aby zapoznać się z przykładem, który pokazuje, jak używać tej funkcji, zobacz [Dodawanie adnotacji IntelliSense](#Annotations).|
|`getFunctionComments(func);`|Zwraca komentarze dla określonej funkcji.<br /><br /> `func` określa funkcję, dla której są zwracane Komentarze.<br /><br /> Parametr `func` można ustawić przy użyciu `completionItem.value`.<br /><br /> Zwrócony obiekt `functionComments` zawiera następujących członków: `above`, `inside` i `paramComment`. Aby uzyskać więcej informacji, zobacz Właściwość [Właściwości functionComments](#FunctionComments) .<br /><br /> `getFunctionComments` można wywołać tylko z poziomu jednego z programów obsługi zdarzeń zarejestrowanych przez `addEventListener`.<br /><br /> Aby zapoznać się z przykładem, który pokazuje, jak używać tej funkcji, zobacz \\ \\*ścieżka instalacji programu Visual Studio*\JavaScript\References\showPlainComments.js.|
|`logMessage(msg);`|Wysyła komunikaty diagnostyczne do okna danych wyjściowych.<br /><br /> `msg` jest ciągiem zawierającym komunikat.<br /><br /> Aby zapoznać się z przykładem, który pokazuje, jak używać tej funkcji, zobacz [wysyłanie komunikatów do okno dane wyjściowe](#Logging).|
|`nullWithCompletionsOf(value);`|Zwraca specjalną wartość null, dla której lista uzupełniania jest określana przez obiekt przekazaną w parametrze `value`.<br /><br /> `value` określa listę uzupełniania dla zwracanej wartości. `value` może być dowolnego typu.<br /><br /> Wartość zwracana null jest traktowana jako null w czasie projektowania, ale lista uzupełniania dla wartości zwracanej jest taka sama jak lista uzupełniania dla parametru `value`.<br /><br /> Jednym z nich użycia dla tej funkcji jest dostarczenie IntelliSense wartości zwracanej, gdy typ zwracany jest przewidywalny w czasie wykonywania, ale wartość zwracana jest `null` w czasie projektowania.|
|`redirectDefinition(func, definition);`|Instruuje funkcję IntelliSense, aby używała podanej funkcji definicji zamiast oryginalnej funkcji Func, gdy żądanie pomocy lub **Przechodzenie do definicji** jest wymagane.<br /><br /> `func` określa funkcję docelową.<br /><br /> `definition` określa funkcję, która ma być używana zamiast funkcji docelowej dla informacji o parametrach i **Przejdź do definicji**.|
|`setCallContext(func, thisArg);`|Ustawia kontekst wywołań lub zakres dla określonej funkcji.<br /><br /> `func` określa funkcję, dla której ma zostać ustawiony zakres.<br /><br /> `thisArg` to literał obiektu, do którego `this` może odwoływać się słowo kluczowe, które określa nowy zakres dla elementu członkowskiego. Można dołączać argumenty do przekazania tego parametru, na przykład `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` zapewnia zachowanie podobne do `Function.prototype.bind`, z tą różnicą, że jest używane tylko do obsługi technologii IntelliSense w czasie projektowania. Za pomocą `setCallContext` można ustawić zakres funkcji, jeśli trzeba symulować wywołanie do kodu, który nie jest dostępny w inny sposób, więc po wywołaniu funkcji wywołanie funkcji będzie zawierać poprawny zakres i argumenty.|
|`undefinedWithCompletionsOf(value);`|Zwraca specjalną niezdefiniowaną wartość, dla której lista uzupełniania jest określana przez obiekt przekazaną w parametrze `value`.<br /><br /> `value` określa listę uzupełniania dla zwracanej wartości. `value` może być dowolnego typu.<br /><br /> Niezdefiniowana wartość zwrotna jest traktowana jako niezdefiniowana w czasie projektowania, ale lista uzupełniania dla wartości zwracanej jest taka sama jak lista uzupełniania dla parametru `value`.<br /><br /> Jednym z nich użycia dla tej funkcji jest dostarczenie technologii IntelliSense dla wartości zwracanej, gdy typ zwracany jest przewidywalny w czasie wykonywania, ale wartość zwracana jest niezdefiniowana w czasie projektowania.|
|`version()`|Zwraca wersję programu Visual Studio.|

## <a name="event-members"></a>Elementy członkowskie zdarzeń
 W poniższych sekcjach opisano elementy członkowskie, które są uwidocznione w obiekcie Event dla następujących zdarzeń: `statementcompletion`, `signaturehelp` i `statementcompletionhint`.

### <a name="CompletionItem"></a>Właściwość completionItem
 Zwraca identyfikator, znany jako element uzupełniania, dla którego zażądano okna podręcznego szybkiej informacji. Ta właściwość jest dostępna dla obiektu zdarzenia `statementcompletionhint` i dla właściwości [Items](#Items) obiektu zdarzenia `statementcompletion`.

 Wartość zwracana: `completionItem` obiektu

 Poniżej znajdują się elementy członkowskie obiektu `completionItem`:

- `name`., Odczyt/zapis, gdy jest używany w kolekcji `items`. w przeciwnym razie, tylko do odczytu. Zwraca ciąg, który identyfikuje element uzupełniający.

- `kind`., Odczyt/zapis, gdy jest używany w kolekcji `items`. w przeciwnym razie, tylko do odczytu. Zwraca ciąg, który reprezentuje typ elementu ukończenia. Możliwe wartości to metody, pola, właściwości, parametru, zmiennej i zastrzeżone.

- `glyph`., Odczyt/zapis, gdy jest używany w kolekcji `items`. w przeciwnym razie, tylko do odczytu. Zwraca ciąg, który reprezentuje ikonę wyświetlaną na liście uzupełniania. Możliwe wartości `glyph` używają następującego formatu: vs:*symbolType*, gdzie *symbolType* odpowiada członkom niezależnym od języka w wyliczeniu <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>. Na przykład `vs:GlyphGroupMethod` jest jedną z możliwych wartości dla `glyph`. Gdy `glyph` nie jest ustawiona, właściwość `kind` określa ikonę domyślną.

- `parentObject`., Tylko do odczytu. Zwraca obiekt nadrzędny.

- `value`., Tylko do odczytu. Zwraca obiekt, który reprezentuje wartość elementu ukończenia.

- `comments`., Tylko do odczytu. Zwraca ciąg zawierający komentarze powyżej pola lub zmiennej.

- `scope`., Tylko do odczytu. Zwraca zakres elementu ukończenia. Możliwe wartości to globalne, lokalne, parametr i składowa.

### <a name="Items"></a>Items — właściwość
 Pobiera lub ustawia tablicę elementów uzupełniania instrukcji. Każdy element w tablicy jest obiektem [Właściwości completionItem](#CompletionItem) . Właściwość `items` jest dostępna dla obiektu zdarzenia `statementcompletion`.

 Wartość zwracana: tablica

### <a name="FunctionComments"></a>Właściwość functionComments
 Zwraca komentarze dla funkcji. Ta właściwość jest dostępna dla obiektu zdarzenia `signaturehelp`.

 Wartość zwracana: `comments` obiektu

 Poniżej znajdują się elementy członkowskie obiektu `comments`:

- `above`., Zwraca komentarze powyżej funkcji.

- `inside`., Zwraca komentarze wewnątrz funkcji, zazwyczaj w formacie VSDoc.

- `paramComments`., Zwraca tablicę reprezentującą komentarze dla każdego parametru w funkcji. Elementy członkowskie tablicy obejmują:

  - `name`., Zwraca ciąg reprezentujący nazwę parametru.

  - `comment`., Zwraca ciąg zawierający komentarz do parametru.

### <a name="FunctionHelp"></a>Właściwość functionHelp
 Zwraca pomoc dla funkcji. Ta właściwość jest dostępna dla obiektu zdarzenia `signaturehelp`.

 Wartość zwracana: `functionHelp` obiektu

 Poniżej znajdują się elementy członkowskie obiektu `functionHelp`:

- `functionName`., Odczyt/zapis. Zwraca ciąg, który zawiera nazwę funkcji.

- `signatures`., Odczyt/zapis. Pobiera lub ustawia tablicę sygnatur funkcji. Każdy element w tablicy jest obiektem `signature`. Niektóre `signature` właściwości, takie jak `locid`, odpowiadają typowym atrybutom [komentarzy dokumentacji XML](../ide/xml-documentation-comments-javascript.md) .

  Elementy członkowskie obiektu `signature` obejmują:

  - `description`., Odczyt/zapis. Zwraca ciąg opisujący funkcję.

  - `locid`., Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje o lokalizacji funkcji.

  - `helpKeyword`., Odczyt/zapis. Zwraca ciąg zawierający słowo kluczowe pomocy.

  - `externalFile`., Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.

  - `externalid`., Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego funkcji.

  - `params`., Odczyt/zapis. Pobiera lub ustawia tablicę parametrów dla funkcji. Każdy element w tablicy parametrów jest obiektem `parameter`, który ma właściwości, które odpowiadają następującym atrybutom [\<param >](../ide/param-javascript.md) elementu:

    - `name`., Odczyt/zapis. Zwraca ciąg, który reprezentuje nazwę parametru.

    - `type`., Odczyt/zapis. Zwraca ciąg, który reprezentuje typ parametru.

    - `elementType`., Odczyt/zapis. Jeśli typ jest `Array`, zwraca ciąg, który reprezentuje typ elementów w tablicy.

    - `description`., Odczyt/zapis. Zwraca ciąg opisujący parametr.

    - `locid`., Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje o lokalizacji funkcji.

    - `optional`., Odczyt/zapis. Zwraca ciąg, który wskazuje, czy parametr jest opcjonalny. `true` wskazuje, że parametr jest opcjonalny;  `false` wskazuje, że nie jest.

  - `returnValue`., Odczyt/zapis. Pobiera lub ustawia obiekt wartości zwracanej z właściwościami odpowiadającymi następującym atrybutom [> \<returns](../ide/returns-javascript.md) elementu:

    - `type`., Odczyt/zapis. Zwraca ciąg, który reprezentuje zwracany typ.

    - `elementType`., Odczyt/zapis. Jeśli typ jest `Array`, zwraca ciąg, który reprezentuje typ elementów w tablicy.

    - `description`., Odczyt/zapis. Zwraca ciąg, który opisuje wartość zwracaną.

    - `locid`., Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje o lokalizacji funkcji.

    - `helpKeyword`., Odczyt/zapis. Zwraca ciąg zawierający słowo kluczowe pomocy.

    - `externalFile`., Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.

    - `externalid`., Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego funkcji.

### <a name="ParentObject"></a>ParentObject — właściwość
 Zwraca obiekt nadrzędny funkcji składowej. Na przykład w przypadku `document.getElementByID` `parentObject` zwraca obiekt `document`. Ta właściwość jest dostępna dla obiektu zdarzenia `signaturehelp`.

 Wartość zwracana: obiekt

### <a name="Target"></a>Target — właściwość
 Zwraca obiekt, który reprezentuje element po lewej stronie znaku wyzwalacza, który jest kropką (.). W przypadku funkcji `target` zwraca funkcję, dla której żądane są informacje o parametrach. Ta właściwość jest dostępna dla obiektów zdarzeń `statementcompletion` i `signaturehelp`.

 Wartość zwracana: obiekt

### <a name="TargetName"></a>TargetName — właściwość
 Zwraca ciąg, który reprezentuje element docelowy. Na przykład dla elementu "this." `targetName` zwraca wartość "This". Dla "A. B" (gdy kursor jest po "B"), `targetName` zwraca "B". Ta właściwość jest dostępna dla obiektu zdarzenia `statementcompletion`.

 Wartość zwracana: ciąg

### <a name="SymbolHelp"></a>Właściwość symbolHelp
 Zwraca element ukończenia, dla którego zażądano okna podręcznego szybkiej informacji. Ta właściwość jest dostępna dla obiektu zdarzenia `statementcompletionhint`.

 Wartość zwracana: `symbolHelp` obiektu.

 Niektóre właściwości obiektu `symbolHelp`, takie jak `locid`, odpowiadają typowym atrybutom [komentarzy dokumentacji XML](../ide/xml-documentation-comments-javascript.md) .

 Poniżej znajdują się elementy członkowskie obiektu `symbolHelp`:

- `name`., Odczyt/zapis. Zwraca ciąg, który zawiera nazwę identyfikatora.

- `symbolType`., Odczyt/zapis. Zwraca ciąg, który reprezentuje typ symbolu. Możliwe wartości to: nieznana, wartość logiczna, liczba, ciąg, obiekt, funkcja, tablica, Data i wyrażenie regularne.

- `symbolDisplayType`., Odczyt/zapis. Zwraca ciąg, który zawiera nazwę typu do wyświetlenia. Jeśli `symbolDisplayType` nie jest ustawiona, `symbolType` jest używany.

- `elementType`., Odczyt/zapis. Jeśli `symbolType` jest `Array`, zwraca ciąg, który reprezentuje typ elementów w tablicy.

- `scope`., Odczyt/zapis. Zwraca ciąg, który reprezentuje zakres symbolu. Możliwe wartości to globalne, lokalne, parametr i składowa.

- `description`., Odczyt/zapis. Zwraca ciąg, który zawiera opis symbolu.

- `locid`., Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje o lokalizacji dotyczące symbolu.

- `helpKeyword`., Odczyt/zapis. Zwraca ciąg zawierający słowo kluczowe pomocy.

- `externalFile`., Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.

- `externalid`., Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego symbolu.

- `functionHelp`., Odczyt/zapis. Zwraca [Właściwość functionHelp](#FunctionHelp), która może zawierać informacje, gdy `symbolType` jest funkcją.

### <a name="Scope"></a>Właściwość Scope
 Zwraca zakres ukończenia zdarzenia. Możliwe wartości dla zakresu ukończenia są globalne i składowe. Ta właściwość jest dostępna dla obiektu zdarzenia `statementcompletion`.

 Wartość zwracana: ciąg

## <a name="debugging-intellisense-extensions"></a>Debugowanie rozszerzeń IntelliSense
 Nie można debugować rozszerzeń, ale można użyć funkcji [obiektu IntelliSense](#intellisenseObject) do wysyłania informacji do okna danych wyjściowych programu Visual Studio. Aby zapoznać się z przykładem, który pokazuje, jak używać tej funkcji, zobacz [wysyłanie komunikatów do okno dane wyjściowe](#Logging) w dalszej części tego tematu. Aby `logMessage` działały, co najmniej jeden program obsługi zdarzeń musi być zarejestrowany w rozszerzeniu.

## <a name="CodeExamples"></a>Przykłady kodu
 Ta sekcja zawiera przykłady kodu, które pokazują, jak używać interfejsów API rozszerzalności IntelliSense. Istnieją także inne sposoby korzystania z tych interfejsów API. Aby uzyskać więcej przykładów, zobacz następujące pliki w \\ \\ folderze*ścieżka instalacji programu Visual Studio*\JavaScript\References. Są to przykłady robocze używane przez usługę języka JavaScript.

- underscoreFilter. js. Ten kod ukrywa prywatne elementy członkowskie z IntelliSense. Obejmuje obsługę zdarzeń dla zdarzenia `statementcompletion`.

- showPlainComments. js. Ten kod zapewnia obsługę funkcji IntelliSense dla standardowych komentarzy. Obejmuje obsługę zdarzeń dla zdarzeń `signaturehelp` i `statementcompletionhint`.

### <a name="Annotations"></a>Dodawanie adnotacji IntelliSense
 Poniższa procedura pokazuje, jak zapewnić obsługę dokumentacji IntelliSense dla biblioteki innej firmy bez bezpośredniej modyfikacji biblioteki. W tym celu można użyć `intellisense.annotate` w rozszerzeniu.

 Aby ten przykład działał, potrzebne są następujące pliki JavaScript w projekcie:

- demoLib. js, który jest plikiem projektu, który reprezentuje bibliotekę innej firmy.

- demoLib. IntelliSense. js, który jest rozszerzeniem IntelliSense. Ten plik nie musi być uwzględniony w projekcie, ale musi znajdować się w tym samym folderze co exampleLib. js.

- Kodzie aplikacji. js, który jest plikiem projektu, który reprezentuje kod aplikacji.

##### <a name="to-add-an-intellisense-annotation"></a>Aby dodać adnotację IntelliSense

1. Dodaj następujący kod do demoLib. js.

    ```javascript
    function someFunc(a) { };
    var rectangle;

    ```

2. Dodaj następujący kod do demoLib. IntelliSense. js.

    ```javascript
    intellisense.annotate(someFunc, function (a) {
        /// <signature>
        /// <summary>Description of someFunc</summary>
        /// <param name="a">Param a</param>
        /// </signature>
    });

    intellisense.annotate(window, {
        // This is a comment on a global variable named rectangle.
        rectangle: undefined
    });
    ```

3. Dodaj następującą dyrektywę referencyjną jako pierwszy wiersz w kodzie aplikacji. js. Ścieżka użyta w tym miejscu wskazuje, że pliki JavaScript znajdują się w tym samym folderze.

    ```javascript
    /// <reference path="demoLib.js" />

    ```

4. W kodzie aplikacji. js wpisz poniższy kod. Zobaczysz komentarze dokumentacji XML w rozszerzeniu wyświetlanym jako informacje o parametrach IntelliSense.

     ![Przykład przedstawiający użycie funkcji IntelliSense. Adnotuj](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")

5. W kodzie aplikacji. js wpisz poniższy kod. Podczas wpisywania zobaczysz standardowe komentarze w rozszerzeniu wyświetlanym jako szybkie informacje IntelliSense.

     ![Przykład przedstawiający użycie funkcji IntelliSense. Adnotuj](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")

### <a name="Logging"></a>Wysyłanie komunikatów do Okno Dane wyjściowe
 Poniższa procedura pokazuje, jak wysyłać komunikaty do okna danych wyjściowych. Można wysyłać komunikaty w celu ułatwienia debugowania rozszerzeń IntelliSense.

 Aby ten przykład działał, potrzebne są następujące pliki JavaScript w projekcie:

- exampleLib. js, który jest plikiem projektu, który reprezentuje bibliotekę innej firmy.

- exampleLib. IntelliSense. js, który jest rozszerzeniem IntelliSense. Ten plik nie musi być uwzględniony w projekcie, ale musi znajdować się w tym samym folderze co exampleLib. js.

- Kodzie aplikacji. js, który jest plikiem projektu, który reprezentuje kod aplikacji.

##### <a name="to-send-a-message-to-the-output-window"></a>Aby wysłać komunikat do okna danych wyjściowych

1. Dodaj następujący kod do exampleLib. js.

    ```javascript
    var someVar = {
        a: 1,
        b: 'hello'
    };
    ```

2. Dodaj następujący kod do exampleLib. IntelliSense. js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        // Prints out statement completion info: Either (1) the member
        // list, if the trigger character was typed, or (2) the
        // statement completion identifiers.
        // e.target represents the object left of the trigger character.
        intellisense.logMessage(
            e.target ? 'member list requested, target: ' + e.targetName : 'statement completion for current scope requested');

        // Prints out all statement completion items.
        e.items.forEach(function (item) {
            intellisense.logMessage('[completion item] ' + item.name + ', kind:' + item.kind + ', scope:' + item.scope + ', value:' + item.value);
        });
    });
    ```

3. Dodaj następującą dyrektywę referencyjną jako pierwszy wiersz w kodzie aplikacji. js. Ścieżka użyta w tym miejscu wskazuje, że pliki JavaScript znajdują się w tym samym folderze.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. W oknie dane wyjściowe wybierz **JavaScript Language Service** z listy **Pokaż dane wyjściowe z** . (Aby wyświetlić okno dane wyjściowe, wybierz pozycję **dane wyjściowe** z menu Widok.)

5. W kodzie aplikacji. js wpisz poniższy kod. Podczas wpisywania, w oknie danych wyjściowych są wyświetlane komunikaty z usługi językowej. Pierwszy komunikat w oknie danych wyjściowych wskazuje, że zażądano zakończenia instrukcji dla bieżącego zakresu.

    ```javascript
    some
    ```

     Poniżej znajduje się częściowy widok danych wyjściowych, który powinien zostać wyświetlony.

    ```scr
    03:16:14.3113: statement completion for current scope requested
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined

    …
    ```

6. Wybierz przycisk **Wyczyść wszystko** w oknie danych wyjściowych.

7. Wpisz następujący kod. Pierwszy komunikat w oknie danych wyjściowych wskazuje, że zażądano listy elementów członkowskich.

    ```javascript
    someVar.
    ```

     Poniżej znajduje się częściowy widok danych wyjściowych, który powinien zostać wyświetlony:

    ```scr
    03:17:43.4032: member list requested, target: someVar
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:

    …
    ```

### <a name="Icons"></a>Zmiana ikon IntelliSense
 Poniższa procedura pokazuje, jak zmienić ikony wyświetlane domyślnie przez funkcję IntelliSense. Może to być przydatne w przypadku dostarczania informacji IntelliSense dotyczących pojęć specyficznych dla biblioteki, takich jak przestrzenie nazw, klasy, interfejsy i wyliczenia.

 Aby uzyskać dostępne wartości ikon, zobacz <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.

 Aby ten przykład działał, potrzebne są następujące pliki JavaScript w projekcie:

- exampleLib. js, który jest plikiem projektu, który represens bibliotekę innej firmy.

- exampleLib. IntelliSense. js, który jest rozszerzeniem IntelliSense. Ten plik nie musi być uwzględniony w projekcie, ale musi znajdować się w tym samym folderze co exampleLib. js.

- Kodzie aplikacji. js, który jest plikiem projektu, który reprezentuje kod aplikacji.

##### <a name="to-change-the-icons"></a>Aby zmienić ikony

1. Dodaj następujący kod do exampleLib. js.

    ```javascript
    function Namespace(name) {
        this._isNamespace = true;
        window[name] = this;
    };

    function Enum(values) {
        var e = Object.create(values);
        e._isEnum = true;
        return e;
    };

    var SomeNamespace = new Namespace('SomeNamespace');
    // A constructor function is considered a class.
    SomeNamespace.SomeClass1 = function () { }
    SomeNamespace.Enum1 = new Enum({ VALUE1: 0, VALUE2: 1 });
    ```

2. Dodaj następujący kod do exampleLib. IntelliSense. js.

    ```javascript
    intellisense.addEventListener('statementcompletion', function (e) {
        e.items.forEach(function (item) {
            // Detect a namespace by using the _isNamespace flag.
            if (item.value && item.value._isNamespace) {
                item.glyph = 'vs:GlyphGroupNamespace';
                }

            if (item.parentObject && item.parentObject._isNamespace) {
                // The item is a member of a namespace.

                // All constructor functions that are part of a namespace
                // are considered classes.
                // A constructor function starts with
                // an uppercase letter by convention.
                if (typeof item.value == 'function' && (item.name[0].toUpperCase()
                    == item.name[0])) {
                    item.glyph = 'vs:GlyphGroupClass';
                }

                // Detect an enumeration by using the _isEnum flag.
                if (item.value && item.value._isEnum) {
                    item.glyph = 'vs:GlyphGroupEnum';
                }
            }
        });
    });

    intellisense.addEventListener('statementcompletionhint', function (e) {
        if (e.completionItem.value) {
            if (e.completionItem.value._isNamespace) {
                e.symbolHelp.symbolDisplayType = 'Namespace';
            }
            if (e.completionItem.value._isEnum) {
                e.symbolHelp.symbolDisplayType = 'Enum';
            }
        }
    });
    ```

3. Dodaj następującą dyrektywę referencyjną jako pierwszy wiersz w kodzie aplikacji. js. Ścieżka użyta w tym miejscu wskazuje, że pliki JavaScript znajdują się w tym samym folderze.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

4. W kodzie aplikacji. js wpisz poniższy kod. Podczas pisania zobaczysz, że ikona dla przestrzeni nazw została zmieniona na "{}", jak jest używana w C#.

     ![Przykład pokazujący użycie właściwości glifu](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")

5. W kodzie aplikacji. js wpisz poniższy kod. Podczas pisania zobaczysz nową ikonę wyliczenia dla elementu członkowskiego Enum1 oraz nową ikonę klasy dla elementu członkowskiego SomeClass1.

     ![Przykład pokazujący użycie właściwości glifu](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")

### <a name="Overriding"></a>Unikanie efektów czasu wykonywania na wynikach funkcji IntelliSense
 Usługa języka JavaScript uruchamia kod w celu dynamicznego dostarczania informacji IntelliSense. W efekcie zachowanie w czasie wykonywania może czasami zakłócać żądane wyniki. Poniższa procedura pokazuje, jak zastąpić wyniki IntelliSense, gdy zachowanie w czasie wykonywania skutkuje nieprawidłowym technologią IntelliSense.

 Aby ten przykład działał, potrzebne są następujące pliki JavaScript w projekcie:

- exampleLib. js, który jest plikiem projektu, który reprezentuje bibliotekę innej firmy.

- exampleLib. IntelliSense. js, który jest rozszerzeniem IntelliSense. Ten plik nie musi być uwzględniony w projekcie, ale musi znajdować się w tym samym folderze co exampleLib. js.

- Kodzie aplikacji. js, który jest plikiem projektu, który reprezentuje kod aplikacji.

##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Aby uniknąć efektów w czasie wykonywania na wynikach funkcji IntelliSense

1. Dodaj następujący kod do exampleLib. js.

    ```javascript
    function after(count, func) {
        return function () {
            if (--times < 1) {
                return func.apply(this, arguments);
            }
        };
    };
    ```

     W poprzednim kodzie funkcja opakowana ignoruje początkowe wywołania, na podstawie wartości `count` i nie zwraca wyników.

2. Dodaj następującą dyrektywę referencyjną jako pierwszy wiersz w kodzie aplikacji. js. Ścieżka użyta w tym miejscu wskazuje, że pliki JavaScript znajdują się w tym samym folderze.

    ```javascript
    /// <reference path="exampleLib.js" />

    ```

3. W kodzie aplikacji. js wpisz poniższy kod. Zostanie wyświetlona lista identyfikatorów zamiast IntelliSense, ponieważ funkcja opakowana nigdy nie jest wywoływana, co oznacza, że funkcja `throttled` nie zwraca żadnych wyników.

     ![Przykład przesłaniania wyników IntelliSense](../ide/media/js-intellisense-override.png "js_intellisense_override")

4. Dodaj następujący kod do exampleLib. IntelliSense. js. Spowoduje to zmianę zachowania w czasie projektowania, tak aby funkcja IntelliSense była wyświetlana dla funkcji opakowanej zgodnie z oczekiwaniami.

    ```javascript
    window.after = function (count, func) {
        // Just return func.
        return func;
    };
    ```

5. W kodzie aplikacji. js Przetestuj wyniki, wpisując ten sam kod, który został wpisany wcześniej. Tym razem technologia IntelliSense udostępnia wymagane informacje.

     ![Przykład przesłaniania wyników IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")

## <a name="see-also"></a>Zobacz też
 [](../ide/javascript-intellisense.md) [Uzupełnianie instrukcji języka JavaScript dla identyfikatorów](../ide/statement-completion-for-identifiers.md)
