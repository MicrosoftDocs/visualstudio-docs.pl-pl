---
title: Funkcja IntelliSense języka JavaScript | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript]
- <reference> JavaScript XML tag
- JavaScript Code Editor
- XML code comments, JavaScript IntelliSense
- reference JavaScript XML tag
- JavaScript, IntelliSense
- code comments, JavaScript IntelliSense
- JavaScript, reference groups
- JavaScript Editor
- reference directives [JavaScript]
- JavaScript, XML documentation comments
- reference groups [JavaScript]
- JavaScript, reference directives
- IntelliSense [JavaScript], about
- IntelliSense extensibility [JavaScript]
- XML documentation comments [JavaScript]
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 67
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 64da24c21ef40bd850e7fb91ed530df67bfe66b4
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54763287"
---
# <a name="javascript-intellisense"></a>JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Technologia IntelliSense pomaga napisać kod szybciej i z mniejszą liczbą błędów poprzez dostarczanie informacji w trakcie kodowania. Podczas pracy ze skryptem klienta w Edytorze kodu JavaScript, IntelliSense wyświetla listę obiektów, funkcji, właściwości i parametrów, które są dostępne w oparciu o bieżący kontekst. Można wybrać opcję kodowania z wyskakującej listy dostarczonej przez technologię IntelliSense, aby uzupełnić kod.

 Technologia IntelliSense sprawia, że łatwiej wykonać następujące zadania:

- Znajdowanie informacji o elemencie członkowskim.

- Wstawianie elementów języka bezpośrednio w kodzie.

- Obsługa kontekstu bez konieczności opuszczania Edytora kodu.

- Obsługa niestandardowej technologii IntelliSense z komentarzami dokumentacji XML i rozszerzalność JavaScript IntelliSense.

  Ten temat zawiera następujące sekcje:

- [Określanie kontekstu IntelliSense](#DeterminingIntelliSenseContext)

- [Przetwarzanie informacji IntelliSense](#ProcessingIntelliSenseInformation)

- [JavaScript IntelliSense Features](#Features)

- [Rozszerzalność JavaScript IntelliSense](#Extensibility)

- [Sprawdzanie poprawności języka JavaScript](#Validation)

  Aby uzyskać więcej informacji na temat funkcji IntelliSense [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], zobacz [za pomocą funkcji IntelliSense](../ide/using-intellisense.md).

##  <a name="DeterminingIntelliSenseContext"></a> Określanie kontekstu IntelliSense
 Technologia JavaScript IntelliSense zawiera opcje kodowania w zależności od całego skryptu, który odnosi się do bieżącego kontekstu skryptu. Obejmuje to elementy skryptu w bieżącym pliku. Obejmuje to również wszelki kod, który jest wywoływany bezpośrednio lub pośrednio ze skryptu, takie jak odwołania do pliku skryptu, odwołania do zestawów skryptów, odwołania do usługi i odwołania do strony skojarzonej.

 Bieżący kontekst skryptu jest utworzony w oparciu o następujące elementy:

-   Funkcje, które są zdefiniowane we wszystkich blokach skryptu w aktywnym dokumencie. Wbudowane bloki skryptu są obsługiwane w plikach, które mają rozszerzenia nazwy pliku aspx., ascx, .master, .html i .htm.

-   `script` elementy z `src` atrybuty, które wskazują do innego pliku skryptu. Docelowy plik skryptu musi mieć rozszerzenie nazwy pliku js.

-   Pliki JavaScript, które odwołują się inne pliki JavaScript za pomocą `reference` dyrektywy.

-   Grupy odniesienia dla obiektów globalnych, rozszerzenia IntelliSense lub pliki skryptów ładowane z opóźnieniem.

-   Odwołania do usług XML sieci Web.

-   <xref:System.Web.UI.ScriptManager> i <xref:System.Web.UI.ScriptManagerProxy> kontrolki, jeśli aplikacja sieci Web jest aplikacją ASP.NET z włączoną obsługą technologii AJAX.

-   [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)], Jeśli pracujesz w aplikacji internetowej ASP.NET z włączoną obsługą technologii AJAX.

    > [!NOTE]
    >  Funkcja IntelliSense nie jest obsługiwana dla skryptu w atrybutach programu obsługi zdarzeń dla elementów HTML, lub który jest zdefiniowany w `href` atrybutów.

##  <a name="ProcessingIntelliSenseInformation"></a> Przetwarzanie informacji IntelliSense
 Aby zapewnić JavaScript IntelliSense, usługa językowa wykonuje następujące operacje:

-   Tworzy listę plików zależnych JavaScript, które są oparte na odwołaniach w aktywnym dokumencie i oparte na rekursywnym rozpatrywaniu odwołań skryptu w plikach odwołania.

-   Przechodzi przez listę i gromadzi informacje o typie oraz inne odpowiednie dane z każdego pliku.

-   Agreguje dane i przekazuje je do usługi języka JavaScript, która udostępnia informacje o typie i danych technologii IntelliSense.

-   Monitoruje pliki pod kątem zmian, które mogą mieć wpływ na listę IntelliSense i aktualizuje listę, stosownie do potrzeb. Skrypty w lokalizacjach zdalnych (do których kod odwołuje się na przykład za pomocą protokołu HTTP) nie są monitorowane.

##  <a name="Features"></a> Funkcje JavaScript IntelliSense
 Technologia JavaScript IntelliSense obsługuje następujące obiekty:

- [Elementy Object Model (DOM) dokumentu](#HTMLDom)

- [Obiekty wewnętrzne](#IntrinsicObjects)

- [Zmienne zdefiniowane przez użytkownika, funkcje i obiekty](#UserDefined)

- Obiekty zdefiniowane w zewnętrznych plikach przy użyciu odwołań, takie jak [odwołania do skryptu](#Script), [odwołania dyrektywach](#ReferenceDirectives), i [odwoływać się do grup](#ReferenceGroups).

- Obiekty zdefiniowane w zdalnych plikach, które zostały pobrane przez program Visual Studio.

- Obiekty określone w [komentarze dokumentacji XML](#XMLDocComments), takich jak parametry i pola.

- Obiekty oznaczone przy użyciu standardowych znaczników komentarza JavaScript (//). Aby uzyskać więcej informacji, zobacz [rozszerzanie JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

- Obiekty obsługiwane za pomocą [rozszerzalność IntelliSense języka JavaScript](#Extensibility) mechanizm. Aby uzyskać więcej informacji, zobacz [rozszerzanie JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

- [Obiekty ASP.NET AJAX](#ASPNet)

  Gdy IntelliSense nie jest w stanie określić typu obiektu, udostępnia opcje uzupełniania instrukcji przy użyciu identyfikatorów w aktywnym dokumencie. Aby uzyskać więcej informacji, zobacz [uzupełnianie składni dla identyfikatorów](../ide/statement-completion-for-identifiers.md).

###  <a name="HTMLDom"></a> Elementy DOM HTML
 Technologia JavaScript IntelliSense zawiera odwołania programistyczne dla elementów DOM Dynamic HTML (DHTML), takie jak `body`, `form`, i `div`. Tylko elementy, które są zawarte w bieżącym dokumencie i na stronie głównej, są wyświetlane przez technologię IntelliSense. JavaScript IntelliSense obsługuje również `window` i `document` obiektów i ich elementów członkowskich.

###  <a name="IntrinsicObjects"></a> Obiekty wewnętrzne
 Technologia JavaScript IntelliSense zawiera odwołania programistyczne dla obiektów wewnętrznych takich jak `Array`, `String`, `Math`, `Date`, i `Number`. Aby uzyskać więcej informacji o obiektach wewnętrznych, zobacz [obiekty wewnętrzne](/visualstudio/scripting-docs/javascript/intrinsic-objects-javascript).

###  <a name="UserDefined"></a> Zmienne zdefiniowane przez użytkownika, funkcje i obiekty
 Po zmianie pliku JavaScript, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] skanuje otwarte i odnośne dokumenty, aby określić wszystkie dostępne zasoby kodu. Obejmuje to zmienne, funkcje i obiekty, które zostały utworzone. Te zasoby będą dostępne dla JavaScript IntelliSense.

 Aby uzyskać więcej informacji na temat zmiennych zdefiniowanych przez użytkownika, funkcje i obiekty, zobacz [tworzenie własnych obiektów](http://go.microsoft.com/fwlink/?LinkId=108671) w witrynie MSDN.

###  <a name="External"></a> Odwołania do pliku zewnętrznego
 Mogą zawierać różne typy odwołań do zewnętrznego pliku, aby uzyskać obsługę IntelliSense w kodzie. Odwołania do zewnętrznego pliku mogą być odwołaniami do skryptu, dyrektywami odwołań lub mogą być określone za pomocą grup odwołań.

####  <a name="Script"></a> Odwołania do skryptu
 Zamiast pisania całości skryptu klienckiego na stronie, można utworzyć zewnętrzne pliki odwołań, które zawierają kod skryptów. Ułatwia to ponowne użycie kodu przez różne strony oraz umożliwia buforowanie skryptu klienckiego przez przeglądarkę.

 Jeśli nie pracujesz na stronie sieci Web z włączoną obsługą technologii AJAX programu ASP.NET, można się odwołać do zewnętrznego pliku skryptu za pomocą `src` atrybutów w znaczniku otwierającym elementu `script` elementu. `src` Atrybut określa adres URL do zewnętrznego pliku, który zawiera kod źródłowy lub dane.

 W poniższym przykładzie pokazano oznaczenie, które używa `src` atrybutu w <`script`> tag, aby odwoływać się do pliku skryptu.

```html
<script type="text/javascript" src="~/Scripts/JavaScript.js">

</script>
```

 Jeśli pracujesz na stronie sieci Web z włączoną obsługą technologii AJAX programu ASP.NET można się odwołać plików skryptów za pomocą <xref:System.Web.UI.ScriptReference> obiektu <xref:System.Web.UI.ScriptManager> kontroli.

 W poniższym przykładzie pokazano oznaczenie, które używa <xref:System.Web.UI.ScriptReference> obiektu <xref:System.Web.UI.ScriptManager> formantu, aby odwoływać się do pliku skryptu.

```html
<asp:ScriptManager ID="ScriptManager1" runat="server">
  <Scripts>
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />
  </Scripts>
</asp:ScriptManager>
```

 Technologia IntelliSense obsługuje również pliki skryptów, które są osadzane jako zasoby w zestawie w aplikacjach internetowych ASP.NET AJAX. Aby uzyskać więcej informacji na temat zasobów osadzonych skryptów, zobacz [instruktażu: Embedding a JavaScript File jako zasób w zestawie](http://msdn.microsoft.com/library/d8cb78cd-95a9-4dc6-92df-391866817e89).

####  <a name="ReferenceDirectives"></a> Dyrektywy odwoławcze
 A `reference` włącza dyrektywą [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] do ustanawiania relacji między skryptu aktualnie edytowanym i innymi skryptami. `reference` Dyrektywy pozwala umieścić plik skryptu w kontekście skryptów bieżącego pliku skryptu. Dzięki temu IntelliSense może się odnosić do zewnętrznie zdefiniowanych funkcji, typów i pól w trakcie kodowania.

 Możesz utworzyć `reference` dyrektywy w formie komentarza XML. Dyrektywa musi być zadeklarowana w pliku wcześniej niż dowolny skrypt. A `reference` dyrektywy może zawierać odwołanie do skryptu opartego na dysku, odwołanie do skryptu opartego na zestawie, odwołanie do skryptu opartego na usługi lub odwołanie do skryptu opartego na stronie.

 Poniższy przykład pokazuje przykłady stosowania dyrektyw odniesienia opartych na dysku. W pierwszym przykładzie usługa języka szuka pliku w tym samym folderze, który zawiera plik projektu (na przykład .jsproj).

 `/// <reference path="ScriptFile1.js" />`

 `/// <reference path="Scripts/ScriptFile2.js" />`

 `/// <reference path="../ScriptFile3.js" />`

 `/// <reference path="~/Scripts/ScriptFile4.js" />`

 Poniższy przykład pokazuje, jak utworzyć odwołanie do skryptu opartego na zestawie.

 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`

 Poniższy przykład pokazuje, jak utworzyć odwołanie do skryptu opartego na usłudze:

 `/// <reference path="MyService.asmx" />`

 `/// <reference path="Services/MyService.asmx" />`

 `/// <reference path="../MyService.asmx" />`

 `/// <reference path="~/Services/MyService.asmx" />`

> [!NOTE]
>  JavaScript IntelliSense nie jest obsługiwana dla skryptu, który jest zawarty w plikach usługi internetowej (.asmx) w projektach aplikacji internetowej (WAP).

 Poniższy przykład pokazuje, jak utworzyć odwołanie do skryptu opartego na stronie.

 `/// <reference path="Default.aspx" />`

 `/// <reference path="Admin/Default.aspx" />`

 `/// <reference path="../Default.aspx" />`

 `/// <reference path="~/Admin/Default.aspx" />`

 Następujące reguły mają zastosowanie do `reference` dyrektywy.

-   `reference` Komentarza XML musi być zadeklarowany przed jakimkolwiek skryptem.

-   Należy użyć składni komentarzy XML z trzema ukośnikami. Odniesienia przy użyciu składni standardowych komentarzy (dwa ukośniki) są ignorowane.

-   Można określić tylko jeden plik lub zasób dla każdej dyrektywy.

-   Wiele odwołań do skryptów opartych na stronie nie jest dozwolone.

-   Jeśli jest określone odwołanie oparte na stronie, nie są dozwolone inne typy dyrektyw odwołania.

-   Nazwy plików używają ścieżek względnych. Można używać operatora tyldy (`~`) umożliwiają ścieżki względem katalogu głównego aplikacji.

-   Ścieżki bezwzględne są ignorowane.

-   Dyrektywy odwołania na stronach odwołania nie będą przetwarzane — to znaczy, że dyrektywy odwołania nie są rekursywnie rozwiązywane dla stron. Uwzględniany jest tylko skrypt wywoływany bezpośrednio przez stronę.

####  <a name="ReferenceGroups"></a> Grupy odwołań
 Można używać wstępnie zdefiniowanych grup odwołań w celu określania, że konkretne pliki .js IntelliSense znajdują się w zakresie dla różnych projektów JavaScript. Dostępne są następujące typy grup odwołań:

- Niejawna (Windows), aby uzyskać [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka JavaScript. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla projektu określonego typu.

- Niejawna (sieć Web) dla projektów HTML5. Pliki dołączone do tej grupy są w zakresie dla każdego pliku .js otwartego w Edytorze kodu dla tych typów projektu.

- Grupy odwołań wyspecjalizowanych funkcji roboczych, dla funkcji roboczych HTML5 sieci Web. Pliki określone w tej grupie są w zakresie plików .js, które mają wyraźne odniesienie do grupy odwołań wyspecjalizowanych funkcji roboczych.

- Ogólna dla innych typów projektów języka JavaScript.

  W większości scenariuszy nie trzeba modyfikować grup odwołań. Jednakże, jeśli chcesz wprowadzić zmiany,możesz użyć opcji konfiguracji dla Edytora kodu JavaScript w celu określenia plików znajdujących się w grupach odwołań. Aby uzyskać instrukcje na temat używania tej funkcji, zobacz [opcje, Edytor tekstu, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!TIP]
>  Odwołania IntelliSense są zazwyczaj używane do obsługi technologii IntelliSense dla obiektów globalnych i dla technologii IntelliSense [rozszerzenia](#Extensibility). Ta funkcja służy również dla skryptów, które muszą być ładowane w czasie wykonywania za pomocą programu ładującego skrypt.

### <a name="remote-file-references"></a>Odwołania do pliku zdalnego
 Można poinstruować Visual Studio, aby pobierał zdalne pliki JavaScript, do których istnieją odwołania w pliku JavaScript, w celu zapewnienia obsługi technologii IntelliSense dla zdalnego pliku lub biblioteki. Gdy korzystasz z tej funkcji, pliki zostaną pobrane po włączeniu ich jako odwołania w pliku JavaScript.

> [!NOTE]
>  Z wyjątkiem projektów sieci Web, funkcja ta działa tylko dla plików JavaScript, które są otwierane poza kontekstem projektu. Dla projektów sieci Web domyślnie pobierane są pliki zdalne, do których odwołuje się projekt.

 Aby uzyskać instrukcje na temat używania tej funkcji, zobacz [opcje, Edytor tekstu, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).

> [!WARNING]
>  Jeśli włączysz tę funkcję i obserwujesz mniejszą wydajność w Edytorze kodu, zalecamy jej wyłączenie.

###  <a name="XMLDocComments"></a> Komentarze dokumentacji XML
 Komentarze dokumentacji XML to opisy tekstowe elementów kodu, które można dodać do skryptu. Te opisy tekstowe są wyświetlane w IntelliSense podczas tworzenia odwołania do komentowanego skryptu. Na przykład można dostarczyć informacji na temat parametrów funkcji i wartości zwracanej. Komentarze dokumentacji XML są dostępne tylko z odnośnych plików, zestawów i usług. Aby uzyskać więcej informacji, zobacz [komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md) i [tworzyć komentarze dokumentacji XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

 Technologia IntelliSense można wyświetlić komentarze dokumentacji XML w następujących scenariuszach:

- Plik .js, który odwołuje się do innego pliku .js.

- Plik .js, który odwołuje się do pliku .aspx.

- Plik .aspx, który odwołuje się do pliku .js.

  Technologia IntelliSense nie jest dostępna, gdy jeden plik .aspx odwołuje się do innego pliku aspx.

###  <a name="ASPNet"></a> ASP.NET AJAX Objects
 ASP.NET AJAX również obsługuje technologię JavaScript IntelliSense. ASP.NET AJAX obejmuje strukturę klienta, która rozszerza standardowe typy, które są dostępne w języku ECMAScript (JavaScript). Aby umożliwić technologii JavaScript IntelliSense dostarczanie szczegółowych informacji o obiektach ASP.NET AJAX, komentarze dokumentacji XML zostały dodane w całej [!INCLUDE[atlaslib_current_ext](../includes/atlaslib-current-ext-md.md)]. Te komentarze dokumentacji XML są wyświetlane podczas korzystania z typów i elementów członkowskich, które są zawarte w bibliotece programu ASP.NET AJAX.

> [!NOTE]
>  Prywatne elementy członkowskie nie są wyświetlane przez JavaScript IntelliSense. Prywatne elementy członkowskie są oznaczone w technologii ASP.NET AJAX jako elementy członkowskie, które rozpoczynają się od znaku podkreślenia (_).

##  <a name="Extensibility"></a> Rozszerzalność JavaScript IntelliSense
 Usługa języka JavaScript zawiera obiekty i funkcje, które umożliwiają modyfikowanie doświadczenia IntelliSense dla programistów, którzy korzystają z bibliotek innych firm. Funkcje te są szczególnie przydatne, gdy usługa języka domyślnego nie jest w stanie dostarczyć wszystkich informacji, które chcesz dostarczać klientom. Aby uzyskać więcej informacji, zobacz [rozszerzanie JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).

##  <a name="Validation"></a> Sprawdzanie poprawności języka JavaScript
 Sprawdzanie poprawności skryptów JavaScript jest nieprzerwanie wykonywane w tle. Gdy [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] wykrywa błędy składni w kodzie JavaScript, informacje są przekazywane w następujący sposób:

-   Podkreślone elementy w edytorze. Czerwone faliste linie wskazują błędy. Jeśli przytrzymasz wskaźnik myszy nad błędem, wyświetla się etykieta zawierająca opis błędu.

-   **Lista błędów** okna. **Lista błędów** okno wyświetla opis błędu, plik, w którym wystąpił błąd, numer wiersza i kolumny i projektu. Do wyświetlenia **lista błędów** okna w **widoku** menu, kliknij przycisk **lista błędów**.

-   W oknie Dane wyjściowe wyświetlane odwołania, które nie zostały załadowane.

## <a name="see-also"></a>Zobacz też
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
- [Tworzenie komentarzy dokumentacji XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)
- [Rozszerzanie funkcji IntelliSense języka JavaScript](../ide/extending-javascript-intellisense.md)
- [Uzupełnianie instrukcji dla identyfikatorów](../ide/statement-completion-for-identifiers.md)
- [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)
- [Model obiektowy DHTML — informacje](http://go.microsoft.com/fwlink/?LinkID=92344)
- [Lista członków](http://msdn.microsoft.com/1b9cc469-9cd4-4d42-9999-1f9479635ff8)
- [Atrybut SRC &#124; src właściwości](http://go.microsoft.com/fwlink/?LinkId=92345)