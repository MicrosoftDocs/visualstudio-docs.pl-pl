---
title: Rozszerzanie JavaScript IntelliSense | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eea71ffe2b449e0ee5aff893efd05e12e4ecae73
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824929"
---
# <a name="extending-javascript-intellisense"></a>Rozszerzanie JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja rozszerzalność JavaScript IntelliSense umożliwia dostosowywanie wyników funkcji IntelliSense w edytorze języka JavaScript dla bibliotek innych firm. Może to poprawić środowisko deweloperów, którzy korzystają z tych bibliotek.  
  
 Usługa języka JavaScript zawiera funkcje IntelliSense dla bibliotek JavaScript innych firm, które są dodawane do projektu. Większość bibliotek uzupełnianie instrukcji jest dostarczony automatycznie przez usługę języka. Na poniższej ilustracji przedstawiono przykład uzupełnianie instrukcji:  
  
 ![Przykład uzupełnianie instrukcji](../ide/media/js-intellisense-completion.png "js_intellisense_completion")  
  
 Jeśli Twoja biblioteka zawiera opisy zmienne, funkcje i obiekty w standardowych znaczników komentarza JavaScript (/ /), możesz automatycznie korzyści, od funkcji rozszerzalności IntelliSense, które dostarczają opisowe informacje w oknie podręcznym, które domyślnie pojawia się po prawej stronie elementy na liście uzupełniania lub po wpisaniu nawiasu otwierającego w wywołaniu funkcji. Komentarze w oknie podręcznym zawierają opis elementu członkowskiego. Poniższy przykład pokazuje wyskakujące okno na liście uzupełniania.  
  
 ![Przykład pop Quick Info&#45;okno](../ide/media/js-intellisense-quickinfo.png "js_intellisense_quickinfo")  
  
 Aby dodatkowo poprawić środowisko programistyczne, można dostarczyć informacji o typie dla deweloperów w oknie podręcznym. Możesz podać informacje o typie przy użyciu języka JavaScript [komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md) zamiast znaczników standardowych komentarzy. Możesz dodać komentarze dokumentacji XML przy użyciu znaczniki komentarza z trzema ukośnikami (/ / /) i określony zbiór elementów XML.  
  
 Alternatywnie możesz podać informacje o typie przy użyciu rozszerzalność JavaScript IntelliSense. Ta funkcja pozwala dostosować wyniki funkcji IntelliSense, Tworzenie rozszerzeń języka JavaScript i dodawane do kontekstu skryptu. W rozszerzeniu, czyli plik języka JavaScript, możesz zasubskrybować zdarzenia, które są dostępne w `intellisense` obiektu usługi języka. Rozszerzalność JavaScript IntelliSense jest preferowanym rozwiązaniem w przypadku bibliotek, jeśli wzorzec zachowania w bibliotece uniemożliwia dostarczanie żądany poziom obsługę funkcji IntelliSense usługa języka JavaScript, a zamiast deklaratywne XML Komentarze dokumentacji również jest wymagana. Dostosowując wyniki funkcji IntelliSense, możesz utworzyć najwyższej jakości środowisko IntelliSense, niezależnie od tego, wszystkie wzorce zachowania, które mogą wymagać ograniczenia możliwości domyślnej usługi językowej. Aby uzyskać więcej informacji, zobacz [uzupełnianie składni dla identyfikatorów](../ide/statement-completion-for-identifiers.md).  
  
## <a name="adding-an-extension-to-the-script-context"></a>Dodawanie rozszerzenia do kontekstu skryptu  
 Dla rozszerzenia IntelliSense do wykonania potrzebuje ona danych ma zostać dodany do bieżącego kontekstu skryptu. Rozszerzenia mogą być automatycznie dodawane do kontekstu skryptu za pomocą mechanizmu automatycznego odnajdowania lub można dodać rozszerzenia do kontekstu skryptu ręcznie przy użyciu grupy odwołania lub dyrektywy odwołania.  
  
 Mechanizmu automatycznego odnajdowania umożliwia usłudze języka automatycznie znaleźć rozszerzenia, które należy wykonać Konwencję nazewnictwa plików *libraryname*. intellisense.js i które znajdują się w tym samym katalogu co biblioteki w celu zastosowanie rozszerzenia. Na przykład prawidłowe rozszerzenie biblioteki jQuery będzie jQuery.intellisense.js. Dla bardziej restrykcyjne jQuery rozszerzeń można użyć nazwy plików, np. jQuery-1.7.1.intellisense.js (z rozszerzeniem specyficzny dla wersji) lub jQuery.ui.intellisense.js (rozszerzenie biblioteki jQuery o określonym zakresie). Najbardziej restrykcyjną wersję rozszerzenia jest używana, jeśli znaleziono więcej niż jedno rozszerzenie dla danej biblioteki.  
  
 Jeśli chcesz użyć rozszerzenia dla wszystkie pliki projektu JavaScript, można zamiast tego dodać rozszerzenie do grupy odwołań. Istnieją różne typy grup odwołań, albo takie, które zawierają odwołań niejawnych, które zawierają odwołania dedykowanych procesów roboczych. Aby dodać rozszerzenie, zazwyczaj należy dodać plik jako grupę niejawne odwołanie, albo **niejawna (Windows)** , **niejawna (sieć Web)** . Odwołań niejawnych znajdują się w zakresie dla każdego pliku .js otwartego w edytorze kodu. Korzystając z tej metody, należy dodać rozszerzenie i pliku który jest uzupełniające rozszerzenia.  
  
 Użyj **IntelliSense** strony **opcje** okno dialogowe, aby dodać rozszerzenie jako grupa odwołań. Możesz uzyskać dostęp **IntelliSense** strony, wybierając **narzędzia**, **opcje** na pasku menu, a następnie wybierając **edytora tekstów**, **JavaScript**, **IntelliSense**, **odwołania**. Aby uzyskać więcej informacji na temat grup odwołań, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md) i [opcje, Edytor tekstu, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
 Jeśli chcesz użyć rozszerzenia dla określonego zestawu plików, należy użyć dyrektywy odwołania. Przy użyciu tej metody należy odwoływać się do zarówno rozszerzenia, jak i plik, który jest uzupełniające rozszerzenia. Aby dowiedzieć się, jak za pomocą dyrektywy odwołań, zobacz [JavaScript IntelliSense](../ide/javascript-intellisense.md).  
  
## <a name="handling-intellisense-events"></a>Obsługa zdarzeń funkcji IntelliSense  
 Funkcja rozszerzalności umożliwia dostosowywanie wyników IntelliSense przez subskrybowanie zdarzeń, takich jak `statementcompletion` zdarzeń usługa językowa `intellisense` obiektu. Poniższy przykład przedstawia proste rozszerzenie, który jest używany przez usługę języka do ukrywania elementów członkowskich, które zaczynają się od znaku podkreślenia z uzupełniania instrukcji. Ten kod jest zawarta w underscorefilter.js i znajduje się w \\ \\ *ścieżka instalacji programu Visual Studio*\JavaScript\References folderu.  
  
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
  
 W poprzednim kodzie, rozszerzenie sprawdza [targetName właściwość](#TargetName) i [właściwość docelowa](#Target) właściwości `statementcompletion` obiektu zdarzenia, aby wykluczyć obiekty, takie jak `this` i `window`i upewnij się, można zidentyfikować liście uzupełniania prawidłową instrukcję. Lista uzupełniania można zidentyfikować, rozszerzenie aktualizuje uzupełniania instrukcji [elementów właściwości](#Items) kolekcji przez filtrowanie elementów członkowskich, które zaczynają się od znaku podkreślenia.  
  
 Dodatkowe przykłady można znaleźć \\ \\ *ścieżka instalacji programu Visual Studio*\JavaScript\References folderu. Plik showPlainComments.js, w tym folderze zawiera przykłady użycia innych zdarzeń, aby zapewnić obsługę funkcji IntelliSense domyślny dla standardowych znaczników komentarza JavaScript (/ /). Podobnie jak underscorefilter.js showPlainComments.js jest już dostępna jako rozszerzenie pracy, a widać wynikowy informacji IntelliSense, używając znaczników komentarzy w kodzie dla zmienne, funkcje i obiekty. Aby uzyskać więcej przykładów, zobacz [przykłady kodu](#CodeExamples).  
  
> [!WARNING]
> Jeśli zmodyfikujesz plików rozszerzeń dołączone do programu Visual Studio, można wyłączyć funkcji IntelliSense języka JavaScript lub funkcji obsługiwanej przez rozszerzenie.  
  
 W kodzie rozszerzenia można utworzyć procedury obsługi dla następujących typów zdarzeń za pomocą `addEventListener`:  
  
- `statementcompletion`, która dodaje program obsługi zdarzeń uzupełniania instrukcji. Dokańczanie instrukcji zawiera listę elementów członkowskich dla określonego typu, który pojawia się po wpisaniu znaki specjalne, takie jak kropka (.) lub listę identyfikatorów, która pojawia się podczas wpisywania lub po naciśnięciu klawisza CTRL + J. Program obsługi odbiera zdarzenia obiektu typu `CompletionEvent`, który obsługuje następujące elementy członkowskie: [elementów właściwości](#Items), [właściwość docelowa](#Target), [targetName właściwość](#TargetName), i [zakresu właściwości](#Scope).  
  
- `signaturehelp`, która dodaje program obsługi dla funkcji IntelliSense o parametrach. Informacje o parametrach zapewnia informacje dotyczące liczby, nazw i typów parametrów wymaganych przez funkcję. Program obsługi odbiera zdarzenia obiektu typu `SignatureHelpEvent`, który obsługuje następujące elementy członkowskie: [właściwość docelowa](#Target), [parentObject właściwość](#ParentObject), [functionComments właściwość](#FunctionComments), [functionHelp właściwość](#FunctionHelp).  
  
- `statementcompletionhint`, która dodaje program obsługi dla szybkie informacje technologii IntelliSense. Okno podręczne szybkie informacje przedstawia pełną deklarację dla identyfikatorów w kodzie. Program obsługi odbiera zdarzenia obiektu typu `CompletionHintEvent`, który obsługuje następujące elementy członkowskie: [completionItem właściwość](#CompletionItem), i [symbolHelp właściwość](#SymbolHelp).  
  
  Przykłady pokazujące, funkcje IntelliSense, takich jak uzupełnianie instrukcji i informacje o parametrach, szybkie informacje, zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).  
  
> [!NOTE]
> W języku JavaScript szybkie informacje odnosi się do wyskakujące okno, który pojawia się po prawej stronie listy uzupełniania. Nie można ręcznie wywołać Quick Info.  
  
## <a name="intellisenseObject"></a> Obiekt IntelliSense  
 W poniższej tabeli przedstawiono funkcje, które są dostępne dla `intellisense` obiektu. `intellisense` Obiekt jest dostępny tylko w czasie projektowania.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`addEventListener(type, handler);`|Dodaje program obsługi zdarzeń dla zdarzenia funkcji IntelliSense.<br /><br /> `type` jest to wartość ciągu. Prawidłowe wartości to `statementcompletion`, `signaturehelp`, i `statementcompletionhint`.<br /><br /> `handler` jest funkcji procedury obsługi zdarzeń, który odbiera obiektu zdarzenia w jednej z następujących typów:<br /><br /> -   `CompletionEvent`, umożliwiający `statementcompletion` zdarzeń.<br />-   `SignatureHelpEvent`, umożliwiający `signaturehelp` zdarzeń.<br />-   `CompletionHintEvent`, umożliwiający `statementcompletionhint` zdarzeń.<br /><br /> Aby uzyskać przykłady, które używają tej funkcji, zobacz [przykłady kodu](#CodeExamples).|  
|`annotate(obj, doc);`|Określa dokumentacji dla obiektu, kopiując komentarzy do dokumentacji z jednego obiektu do innego obiektu.<br /><br /> `obj` Określa obiekt, do którego zostaną skopiowane z dokumentacją.<br /><br /> `doc` Określa obiekt, z którego można skopiować z dokumentacją.<br /><br /> Na przykład, który pokazuje, jak użyć tej funkcji, zobacz [dodawania adnotacji IntelliSense](#Annotations).|  
|`getFunctionComments(func);`|Zwraca komentarzy do określonej funkcji.<br /><br /> `func` Określa funkcję, dla którego są zwracane komentarzy.<br /><br /> Możesz ustawić `func` parametru za pomocą `completionItem.value`.<br /><br /> Zwrócony `functionComments` obiekt zawiera następujące elementy członkowskie: `above`, `inside`, i `paramComment`. Aby uzyskać więcej informacji, zobacz [functionComments właściwość](#FunctionComments) właściwości.<br /><br /> `getFunctionComments` może być wywołana tylko z jednego z programów obsługi zdarzeń, które są zarejestrowane przez `addEventListener`.<br /><br /> Na przykład, który pokazuje, jak użyć tej funkcji, zobacz \\ \\ *ścieżka instalacji programu Visual Studio*\JavaScript\References\showPlainComments.js.|  
|`logMessage(msg);`|Wysyła komunikaty diagnostyczne w oknie danych wyjściowych.<br /><br /> `msg` to jest ciąg zawierający komunikat.<br /><br /> Na przykład, który pokazuje, jak użyć tej funkcji, zobacz [wysyłania wiadomości do okna danych wyjściowych](#Logging).|  
|`nullWithCompletionsOf(value);`|Zwraca specjalne wartość null, dla którego na liście uzupełniania jest określany przez obiekt przekazany w `value` parametru.<br /><br /> `value` Określa, na liście uzupełniania dla zwróconej wartości. `value` mogą być dowolnego typu.<br /><br /> Zwracana wartość null jest traktowana jako wartość null w czasie projektowania, ale na liście uzupełniania dla wartości zwracanej jest taki sam jak listy uzupełniania dla `value` parametru.<br /><br /> Jedno użycie tej funkcji jest zapewnienie technologii IntelliSense dla wartości zwracanej, typ zwracany jest przewidywalne w czasie wykonywania, kiedy wartość zwracana jest `null` w czasie projektowania.|  
|`redirectDefinition(func, definition);`|Intelisense, które umożliwiają za pomocą podanej definicji funkcji zamiast oryginalnej Funkcja func pomocy parametru powoduje, że lub **przejdź do definicji** żądania.<br /><br /> `func` Określa funkcję docelowego.<br /><br /> `definition` Określa funkcję, która ma być używana zamiast funkcji docelowej, aby uzyskać informacje o parametrach i **przejdź do definicji**.|  
|`setCallContext(func, thisArg);`|Ustawia Kontekst wywołania lub zakres dla określonej funkcji.<br /><br /> `func` Określa funkcję, dla której chcesz ustawić zakresu.<br /><br /> `thisArg` jest obiektem literału, do którego `this` — słowo kluczowe może odwoływać się do, która określa nowego zakresu dla elementu członkowskiego. Argumenty do przekazania w tym parametrze mogą obejmować na przykład `intellisense.setCallContext(func, { thisArg: "", args: [23,2] });`<br /><br /> `setCallContext` zapewnia zachowanie podobne do `Function.prototype.bind`, z tą różnicą, że użyta tylko w przypadku obsługi technologii IntelliSense w czasie projektowania. Możesz użyć `setCallContext` Aby ustawić zakres funkcji, jeśli chcesz symulować wywołanie do kodu, który jest w przeciwnym razie nieosiągalny, dzięki czemu podczas wywoływania funkcji, wywołanie funkcji będzie zawierać poprawny zakres i argumenty.|  
|`undefinedWithCompletionsOf(value);`|Zwraca specjalne niezdefiniowaną wartość, dla którego na liście uzupełniania jest określany przez obiekt przekazany w `value` parametru.<br /><br /> `value` Określa, na liście uzupełniania dla zwróconej wartości. `value` mogą być dowolnego typu.<br /><br /> Niezdefiniowane zwraca wartość jest traktowana jako niezdefiniowane w czasie projektowania, ale zakończenia listy dla wartości zwracanej jest taki sam jak listy uzupełniania dla `value` parametru.<br /><br /> Jedno użycie tej funkcji jest zapewnienie technologii IntelliSense dla wartości zwracanej, typ zwracany jest przewidywalne w czasie wykonywania, kiedy wartość zwracana jest niezdefiniowana w czasie projektowania.|  
|`version()`|Zwraca informacje o wersji programu Visual Studio.|  
  
## <a name="event-members"></a>Elementy członkowskie zdarzenia  
 W poniższych sekcjach opisano elementy członkowskie, które są widoczne w obiekcie zdarzenia dla następujących zdarzeń: `statementcompletion`, `signaturehelp`, i `statementcompletionhint`.  
  
### <a name="CompletionItem"></a> completionItem właściwości  
 Zwraca identyfikator, znane jako elementu ukończenia, dla którego żądana jest wyskakującym szybkie informacje. Ta właściwość jest dostępna dla `statementcompletionhint` obiektu zdarzenia i [elementów właściwości](#Items) właściwość `statementcompletion` obiektem zdarzenia.  
  
 Wartość zwracana: `completionItem` obiektu  
  
 Poniżej przedstawiono elementy członkowskie `completionItem` obiektu:  
  
- `name`. Odczyt/zapis, gdy są używane w `items` kolekcji; w przeciwnym razie tylko do odczytu. Zwraca ciąg, który identyfikuje elementu ukończenia.  
  
- `kind`. Odczyt/zapis, gdy są używane w `items` kolekcji; w przeciwnym razie tylko do odczytu. Zwraca ciąg, który reprezentuje typ elementu ukończenia. Możliwe wartości to metody, pola, właściwość, parametru, zmienna i zastrzeżone.  
  
- `glyph`. Odczyt/zapis, gdy są używane w `items` kolekcji; w przeciwnym razie tylko do odczytu. Zwraca ciąg, który reprezentuje ikonę która jest wyświetlana na liście uzupełniania. Możliwe wartości parametru `glyph` , użyj następującego formatu: vs:*glyphType*, gdzie *glyphType* odnosi się do elementów członkowskich niezależny od języka w <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup> wyliczenia. Na przykład `vs:GlyphGroupMethod` to jedna z wartości dla `glyph`. Gdy `glyph` nie jest ustawiona, `kind` właściwość określa domyślną ikonę.  
  
- `parentObject`. Tylko do odczytu. Zwraca obiekt nadrzędny.  
  
- `value`. Tylko do odczytu. Zwraca obiekt reprezentujący wartość elementu ukończenia.  
  
- `comments`. Tylko do odczytu. Zwraca ciąg, który zawiera komentarze, które znajdują się powyżej pola lub zmiennej.  
  
- `scope`. Tylko do odczytu. Zwraca zakres elementu ukończenia. Możliwe wartości są lokalne, globalne, a parametr i elementu członkowskiego.  
  
### <a name="Items"></a> Właściwości elementów  
 Pobiera lub ustawia tablicę instrukcji elementy uzupełniania. Każdy element w tablicy jest [completionItem właściwość](#CompletionItem) obiektu. `items` Właściwość jest dostępna dla `statementcompletion` obiektem zdarzenia.  
  
 Wartość zwracana: tablica  
  
### <a name="FunctionComments"></a> functionComments właściwości  
 Zwraca komentarze dla tej funkcji. Ta właściwość jest dostępna dla `signaturehelp` obiektem zdarzenia.  
  
 Wartość zwracana: `comments` obiektu  
  
 Poniżej przedstawiono elementy członkowskie `comments` obiektu:  
  
- `above`. Zwraca komentarze powyżej funkcji.  
  
- `inside`. Zwraca komentarze wewnątrz funkcji, zazwyczaj w formacie VSDoc.  
  
- `paramComments`. Zwraca tablicę reprezentujący komentarzy dla każdego parametru w funkcji. Elementy członkowskie tablicy obejmują:  
  
  - `name`. Zwraca ciąg reprezentujący nazwę parametru.  

  - `comment`. Zwraca ciąg, który zawiera komentarz parametru.  
  
### <a name="FunctionHelp"></a> functionHelp właściwości  
 Zwraca pomocy dla tej funkcji. Ta właściwość jest dostępna dla `signaturehelp` obiektem zdarzenia.  
  
 Wartość zwracana: `functionHelp` obiektu  
  
 Poniżej przedstawiono elementy członkowskie `functionHelp` obiektu:  
  
- `functionName`. Odczyt/zapis. Zwraca ciąg zawierający nazwę funkcji.  
  
- `signatures`. Odczyt/zapis. Pobiera lub ustawia tablicę sygnatur funkcji. Każdy element w tablicy jest `signature` obiektu. Niektóre `signature` właściwości, takie jak `locid`, odpowiadają na typowe [komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md) atrybutów.  
  
  Elementy członkowskie `signature` obiektu obejmują:  

  - `description`. Odczyt/zapis. Zwraca ciąg, który opisuje funkcji.  

  - `locid`. Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje na temat funkcji lokalizacji.  

  - `helpKeyword`. Odczyt/zapis. Zwraca ciąg, który zawiera słowo kluczowe pomocy.  

  - `externalFile`. Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.  

  - `externalid`. Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego funkcji.  

  - `params`. Odczyt/zapis. Pobiera lub ustawia tablicę parametrów funkcji. Każdy element w tablicy parametrów jest `parameter` obiekt, który ma właściwości, które odpowiadają na następujące atrybuty [ \<param >](../ide/param-javascript.md) elementu:  

    - `name`. Odczyt/zapis. Zwraca ciąg reprezentujący nazwę parametru.  

    - `type`. Odczyt/zapis. Zwraca ciąg, który reprezentuje typ parametru.  

    - `elementType`. Odczyt/zapis. Jeśli typ jest `Array`, zwraca wartość typu ciąg, który reprezentuje typ elementów w tablicy.  

    - `description`. Odczyt/zapis. Zwraca ciąg, który opisuje parametr.  

    - `locid`. Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje na temat funkcji lokalizacji.  

    - `optional`. Odczyt/zapis. Zwraca ciąg, który wskazuje, czy parametr jest opcjonalny. `true` Wskazuje, że parametr jest opcjonalny; `false` wskazuje, że nie jest.  

  - `returnValue`. Odczyt/zapis. Pobiera lub ustawia obiekt o zwracanej wartości właściwości, które odpowiadają na następujące atrybuty [ \<zwraca >](../ide/returns-javascript.md) elementu:  

    - `type`. Odczyt/zapis. Zwraca ciąg, który reprezentuje typ zwracany.  

    - `elementType`. Odczyt/zapis. Jeśli typ jest `Array`, zwraca wartość typu ciąg, który reprezentuje typ elementów w tablicy.  

    - `description`. Odczyt/zapis. Zwraca ciąg, który opisuje wartość zwracaną.  

    - `locid`. Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje na temat funkcji lokalizacji.  

    - `helpKeyword`. Odczyt/zapis. Zwraca ciąg, który zawiera słowo kluczowe pomocy.  

    - `externalFile`. Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.  

    - `externalid`. Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego funkcji.  
  
### <a name="ParentObject"></a> parentObject właściwości  
 Zwraca wartość obiektu nadrzędnego dla funkcji członkowskiej. Na przykład w przypadku `document.getElementByID`, `parentObject` zwraca `document` obiektu. Ta właściwość jest dostępna dla `signaturehelp` obiektem zdarzenia.  
  
 Wartość zwracana: obiekt  
  
### <a name="Target"></a> Właściwość docelowa  
 Zwraca obiekt, który reprezentuje element po lewej stronie znaku wyzwalacza, który jest znak kropki (.). W przypadku funkcji `target` zwraca funkcję, dla którego wnioskuje się o parametrach. Ta właściwość jest dostępna dla `statementcompletion` i `signaturehelp` obiekty zdarzeń.  
  
 Wartość zwracana: obiekt  
  
### <a name="TargetName"></a> targetName właściwości  
 Zwraca ciąg, który reprezentuje element docelowy. Na przykład "this." `targetName` zwraca "this". Aby uzyskać "A.B" (gdy kursor znajduje się po "B") `targetName` zwraca "B". Ta właściwość jest dostępna dla `statementcompletion` obiektem zdarzenia.  
  
 Wartość zwracana: ciąg  
  
### <a name="SymbolHelp"></a> symbolHelp właściwości  
 Zwraca element zakończenia, dla którego żądana jest wyskakującym Quick Info. Ta właściwość jest dostępna dla `statementcompletionhint` obiektem zdarzenia.  
  
 Wartość zwracana: `symbolHelp` obiektu.  
  
 Niektóre właściwości `symbolHelp` obiektów, takich jak `locid`, odpowiadają na typowe [komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md) atrybutów.  
  
 Poniżej przedstawiono elementy członkowskie `symbolHelp` obiektu:  
  
- `name`. Odczyt/zapis. Zwraca ciąg zawierający nazwę identyfikatora.  
  
- `symbolType`. Odczyt/zapis. Zwraca ciąg, który reprezentuje typ symbolu. Możliwe wartości to nieznany, atrybut typu wartość logiczna, numer, ciąg, obiekt, funkcji, tablicy, Data i wyrażeń regularnych.  
  
- `symbolDisplayType`. Odczyt/zapis. Zwraca ciąg zawierający nazwę typu do wyświetlenia. Jeśli `symbolDisplayType` nie ustawiono `symbolType` jest używany.  
  
- `elementType`. Odczyt/zapis. Jeśli `symbolType` jest `Array`, zwraca wartość typu ciąg, który reprezentuje typ elementów w tablicy.  
  
- `scope`. Odczyt/zapis. Zwraca ciąg, który reprezentuje zakres symbolu. Możliwe wartości to globalnego, lokalnych, parametrów i elementu członkowskiego.  
  
- `description`. Odczyt/zapis. Zwraca ciąg, który zawiera opis symbolu.  
  
- `locid`. Odczyt/zapis. Zwraca identyfikator ciągu, który zawiera informacje o lokalizacji o symbolu.  
  
- `helpKeyword`. Odczyt/zapis. Zwraca ciąg, który zawiera słowo kluczowe pomocy.  
  
- `externalFile`. Odczyt/zapis. Zwraca ciąg reprezentujący plik, który zawiera identyfikator elementu członkowskiego.  
  
- `externalid`. Odczyt/zapis. Zwraca ciąg, który reprezentuje identyfikator elementu członkowskiego symbolu.  
  
- `functionHelp`. Odczyt/zapis. Zwraca [functionHelp właściwość](#FunctionHelp), które mogą zawierać informacje podczas `symbolType` jest funkcją.  
  
### <a name="Scope"></a> Określanie zakresu właściwości  
 Zwraca wartość zakresu zakończenia zdarzenia. Możliwe wartości zakończenia zakresu są globalne i elementów członkowskich. Ta właściwość jest dostępna dla `statementcompletion` obiektem zdarzenia.  
  
 Wartość zwracana: ciąg  
  
## <a name="debugging-intellisense-extensions"></a>Debugowanie rozszerzeń IntelliSense  
 Nie można debugować rozszerzenia, ale można użyć [intellisense obiektu ](#intellisenseObject) /funkcja do wysyłania informacji do okna programu Visual Studio danych wyjściowych. Na przykład, który pokazuje, jak użyć tej funkcji, zobacz [wysyłania wiadomości do okna danych wyjściowych](#Logging) w dalszej części tego tematu. Aby uzyskać `logMessage` do pracy, co najmniej jedna procedura obsługi zdarzeń musi być zarejestrowana w rozszerzeniu.  
  
## <a name="CodeExamples"></a> Przykłady kodu  
 Ta sekcja zawiera przykłady kodu, które pokazują, jak używać interfejsów API rozszerzania funkcji IntelliSense. Istnieją również inne sposoby korzystania z tych interfejsów API. Aby uzyskać dodatkowe przykłady, zobacz następujące pliki w \\ \\ *ścieżka instalacji programu Visual Studio*\JavaScript\References folderu. Działają one przykłady używane przez usługę języka JavaScript.  
  
- underscoreFilter.js. Ten kod powoduje ukrycie opcji prywatnych elementów członkowskich z technologii IntelliSense. Obejmuje programy obsługi zdarzeń dla `statementcompletion` zdarzeń.  
  
- showPlainComments.js. Ten kod zapewnia obsługę technologii IntelliSense dla standardowych komentarzy. Obejmuje programy obsługi zdarzeń dla `signaturehelp` i `statementcompletionhint` zdarzenia.  
  
### <a name="Annotations"></a> Dodawanie adnotacji IntelliSense  
 Poniższa procedura pokazuje, jak do obsługi technologii IntelliSense dokumentacji biblioteki innej firmy bez konieczności wprowadzania zmian bezpośrednio w bibliotece. Aby to zrobić, można użyć `intellisense.annotate` w rozszerzeniu.  
  
 W tym przykładzie do pracy potrzebne są następujące pliki JavaScript w projekcie:  
  
- demoLib.js, czyli pliku projektu, który reprezentuje biblioteki innej firmy.  
  
- demoLib.intellisense.js, która jest rozszerzeniem IntelliSense. Ten plik nie musi być zawarty w projekcie, ale musi on znajdować się w tym samym folderze co exampleLib.js.  
  
- appCode.js, czyli pliku projektu, który reprezentuje kod aplikacji.  
  
##### <a name="to-add-an-intellisense-annotation"></a>Dodawanie adnotacji IntelliSense  
  
1. Dodaj następujący kod do demoLib.js.  
  
    ```javascript  
    function someFunc(a) { };  
    var rectangle;  
  
    ```  
  
2. Dodaj następujący kod do demoLib.intellisense.js.  
  
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
  
3. Dodaj następujące dyrektywy odwołania jako pierwszy wiersz w appCode.js. Ścieżka, w tym miejscu użyć wskazuje, czy pliki JavaScript, w tym samym folderze.  
  
    ```javascript  
    /// <reference path="demoLib.js" />  
  
    ```  
  
4. W appCode.js wpisz następujący kod. Zobaczysz komentarze dokumentacji XML w rozszerzeniu wyświetlane jako informacje o parametrach funkcji IntelliSense.  
  
     ![Przykład przedstawiający zastosowanie intellisense.annotate](../ide/media/js-intellisense-annotate-paraminfo.png "js_intellisense_annotate_paraminfo")  
  
5. W appCode.js wpisz następujący kod. Podczas wpisywania, zobaczysz standardowych komentarzy w rozszerzeniu wyświetlane jako szybkie informacje technologii IntelliSense.  
  
     ![Przykład przedstawiający zastosowanie intellisense.annotate](../ide/media/js-intellisense-annotations.png "js_intellisense_annotations")  
  
### <a name="Logging"></a> Wysyłanie komunikatów do okna danych wyjściowych  
 Poniższa procedura pokazuje, jak wysyłać komunikaty do okna danych wyjściowych. Może wysyłać wiadomości, aby pomóc w debugowaniu rozszerzeń IntelliSense.  
  
 W tym przykładzie do pracy potrzebne są następujące pliki JavaScript w projekcie:  
  
- exampleLib.js, czyli pliku projektu, który reprezentuje biblioteki innej firmy.  
  
- exampleLib.intellisense.js, która jest rozszerzeniem IntelliSense. Ten plik nie musi być zawarty w projekcie, ale musi on znajdować się w tym samym folderze co exampleLib.js.  
  
- appCode.js, czyli pliku projektu, który reprezentuje kod aplikacji.  
  
##### <a name="to-send-a-message-to-the-output-window"></a>Aby wysłać komunikat w oknie danych wyjściowych  
  
1. Dodaj następujący kod do exampleLib.js.  
  
    ```javascript  
    var someVar = {  
        a: 1,  
        b: 'hello'  
    };  
    ```  
  
2. Dodaj następujący kod do exampleLib.intellisense.js.  
  
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
  
3. Dodaj następujące dyrektywy odwołania jako pierwszy wiersz w appCode.js. Ścieżka, w tym miejscu użyć wskazuje, czy pliki JavaScript, w tym samym folderze.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. W oknie danych wyjściowych wybierz **usługę językową JavaScript** w **Pokaż dane wyjściowe z** listy. (Zaznacz, aby wyświetlić okno danych wyjściowych **dane wyjściowe** z menu Widok.)  
  
5. W appCode.js wpisz następujący kod. Podczas wpisywania, w oknie danych wyjściowych zawiera komunikaty z usługi języka. Pierwszy komunikat w oknie danych wyjściowych wskazuje zażądano uzupełniania instrukcji dla bieżącego zakresu.  
  
    ```javascript  
    some  
    ```  
  
     Oto widok częściowy wynik, który powinien zostać wyświetlony.  
  
    ```scr  
    03:16:14.3113: statement completion for current scope requested  
    03:16:14.3113: [completion item] break, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] case, kind:reserved, scope:undefined, value:undefined  
    03:16:14.3113: [completion item] catch, kind:reserved, scope:undefined, value:undefined  
  
    …  
    ```  
  
6. Wybierz **Wyczyść wszystko** przycisku w oknie danych wyjściowych.  
  
7. Wpisz następujący kod. Pierwszy komunikat w oknie dane wyjściowe wskazuje zażądano listy członków.  
  
    ```javascript  
    someVar.  
    ```  
  
     Oto widok częściowy wynik, który powinien zostać wyświetlony:  
  
    ```scr  
    03:17:43.4032: member list requested, target: someVar  
    03:17:43.4032: [completion item] a, kind:field, scope:member, value:1  
    03:17:43.4032: [completion item] b, kind:field, scope:member, value:hello  
    03:17:43.4032: [completion item] constructor, kind:method, scope:member, value:  
  
    …  
    ```  
  
### <a name="Icons"></a> Zmiana ikony IntelliSense  
 Poniższa procedura pokazuje, jak zmienić ikony domyślnie wyświetlane przez technologię IntelliSense. Może to być przydatne, gdy zawierają IntelliSense informacji na temat pojęć specyficznych dla biblioteki, takich jak przestrzenie nazw, klasy, interfejsy i wyliczenia.  
  
 Ikona dostępne wartości, zobacz <xref:Microsoft.VisualStudio.Language.Intellisense.StandardGlyphGroup>.  
  
 W tym przykładzie do pracy potrzebne są następujące pliki JavaScript w projekcie:  
  
- exampleLib.js, czyli projektu pliku biblioteki represens innych firm.  
  
- exampleLib.intellisense.js, która jest rozszerzeniem IntelliSense. Ten plik nie musi być zawarty w projekcie, ale musi on znajdować się w tym samym folderze co exampleLib.js.  
  
- appCode.js, czyli pliku projektu, który reprezentuje kod aplikacji.  
  
##### <a name="to-change-the-icons"></a>Aby zmienić ikony  
  
1. Dodaj następujący kod do exampleLib.js.  
  
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
  
2. Dodaj następujący kod do exampleLib.intellisense.js.  
  
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
  
3. Dodaj następujące dyrektywy odwołania jako pierwszy wiersz w appCode.js. Ścieżka, w tym miejscu użyć wskazuje, czy pliki JavaScript, w tym samym folderze.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
4. W appCode.js wpisz następujący kod. Podczas wpisywania, zobaczysz, że ikona przestrzeń nazw została zmieniona na "{}", ponieważ jest używany w języku C#.  
  
     ![Przykład: użycie właściwości symbol](../ide/media/js-intellisense-glyph-namespace.png "js_intellisense_glyph_namespace")  
  
5. W appCode.js wpisz następujący kod. Podczas wpisywania pojawi się nowa ikona wyliczenie dla elementu członkowskiego Enum1 i nową ikonę klasy dla elementu członkowskiego SomeClass1.  
  
     ![Przykład: użycie właściwości symbol](../ide/media/js-intellisense-glyph-class-enum.png "js_intellisense_glyph_class_enum")  
  
### <a name="Overriding"></a> Unikanie środowiska wykonawczego wpływ na wyniki funkcji IntelliSense  
 Usługa języka JavaScript działa kod w celu dynamicznego udostępniania informacji IntelliSense. W rezultacie zachowania w czasie wykonywania od czasu do czasu może zakłócać zakładanych wyników. Poniższa procedura przedstawia sposób przesłonięcia wyniki funkcji IntelliSense, gdy IntelliSense niepoprawne powoduje zachowanie w czasie wykonywania.  
  
 W tym przykładzie do pracy potrzebne są następujące pliki JavaScript w projekcie:  
  
- exampleLib.js, czyli pliku projektu, który reprezentuje biblioteki innej firmy.  
  
- exampleLib.intellisense.js, która jest rozszerzeniem IntelliSense. Ten plik nie musi być zawarty w projekcie, ale musi on znajdować się w tym samym folderze co exampleLib.js.  
  
- appCode.js, czyli pliku projektu, który reprezentuje kod aplikacji.  
  
##### <a name="to-avoid-run-time-effects-on-intellisense-results"></a>Aby uniknąć środowiska wykonawczego wpływ na wyniki funkcji IntelliSense  
  
1. Dodaj następujący kod do exampleLib.js.  
  
    ```javascript  
    function after(count, func) {  
        return function () {  
            if (--times < 1) {  
                return func.apply(this, arguments);  
            }  
        };  
    };  
    ```  
  
     W poprzednim kodzie opakowana Funkcja ignoruje początkowego połączenia, na podstawie wartości z `count`, a nie zwracają wartości.  
  
2. Dodaj następujące dyrektywy odwołania jako pierwszy wiersz w appCode.js. Ścieżka, w tym miejscu użyć wskazuje, czy pliki JavaScript, w tym samym folderze.  
  
    ```javascript  
    /// <reference path="exampleLib.js" />  
  
    ```  
  
3. W appCode.js wpisz następujący kod. Lista identyfikatorów pojawia się zamiast funkcji IntelliSense, ponieważ opakowana funkcja nigdy nie jest wywoływana, co oznacza, że `throttled` funkcja nie zwraca żadnych wyników.  
  
     ![Przykład zastępowanie wyniki intellisense](../ide/media/js-intellisense-override.png "js_intellisense_override")  
  
4. Dodaj następujący kod do exampleLib.intellisense.js. Spowoduje to zmianę zachowania w czasie projektowania, aby opakowana funkcja IntelliSense przedstawiono zgodnie z oczekiwaniami.  
  
    ```javascript  
    window.after = function (count, func) {  
        // Just return func.   
        return func;  
    };  
    ```  
  
5. W appCode.js wyniki testów, wpisując ten sam kod, który wcześniej wpisane. Tym razem IntelliSense zawiera żądane informacje.  
  
     ![Przykład zastępowanie wyniki IntelliSense](../ide/media/js-intellisense-override-fixed.png "js_intellisense_override_fixed")  
  
## <a name="see-also"></a>Zobacz też  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)   
 [Uzupełnianie instrukcji dla identyfikatorów](../ide/statement-completion-for-identifiers.md)
