---
title: Podgląd Pomocy firmy Microsoft SDK | Microsoft Docs
description: Dowiedz się Visual Studio zadań podglądu pomocy, takich jak tworzenie artykułu, tworzenie pakietu brandowania zawartości Podglądu Pomocy i wdrażanie zestawu artykułów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8bc2ed473e25dc75d0155bc864aa02c157e3482f
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448327"
---
# <a name="microsoft-help-viewer-sdk"></a>Zestaw SDK Podglądu Pomocy firmy Microsoft

Ten artykuł zawiera następujące zadania dla Visual Studio podglądu Pomocy:

- Tworzenie tematu (obsługa klawisza F1)

- Tworzenie pakietu brandowania zawartości Podglądu Pomocy

- Wdrażanie zestawu artykułów

- Dodawanie pomocy do powłoki Visual Studio (zintegrowane lub izolowane)

- Dodatkowe zasoby

## <a name="create-a-topic-f1-support"></a>Tworzenie tematu (obsługa klawisza F1)

Ta sekcja zawiera omówienie składników przedstawionego tematu, wymagań tematu, krótkiego opisu sposobu tworzenia tematu (w tym wymagań dotyczących pomocy technicznej F1) oraz przykładowego tematu z renderowanym wynikiem.

**Przegląd tematu Podglądu Pomocy**

Gdy temat jest wywoływany w celu renderowania, Podgląd Pomocy pobiera elementy pakietu brandingu skojarzone z tematem w czasie instalacji lub ostatniej aktualizacji wraz z tematem XHTML i łączy te dwa elementy w celu wyświetlenia widoku zawartości (dane brandingu i dane tematu).  Pakiet brandingu zawiera logo, obsługę zachowań zawartości i tekst brandingu (prawa autorskich itp.).  Aby uzyskać więcej informacji na temat elementów pakietu brandingu, zobacz "Creating Branding Package" (Tworzenie pakietu brandingu) poniżej.  W przypadku, gdy z tematem nie jest skojarzony żaden pakiet brandingu, Podgląd Pomocy będzie używać rezerwowego pakietu brandingu znajdującego się w katalogu głównym aplikacji Podgląd Pomocy (Branding_en-US.ms nie).

**Wymagania dotyczące tematu Podglądu Pomocy**

Aby można było poprawnie renderować w Podglądzie Pomocy, nieprzetworzona zawartość tematu musi być W3C Basic 1.1 XHTML.

Temat zazwyczaj zawiera dwie sekcje:

- Metadane (zobacz odwołanie do metadanych zawartości): dane dotyczące tematu, na przykład unikatowy identyfikator tematu, wartość słowa kluczowego, identyfikator toc toc tematu, identyfikator węzła nadrzędnego itp.

- Zawartość treści: zgodna z W3C Basic 1.1 XHTML, która obejmuje obsługiwane zachowania zawartości (zwijany obszar, fragment kodu itp. Poniżej przedstawiono pełną listę).

Visual Studio obsługiwane kontrolki pakietu brandingu:

- Linki

- CodeSnippet

- CollapsibleArea

- Dziedziczony członek

- LanguageSpecificText

Obsługiwane ciągi języka (bez wielkości liter):

- javascript

- csharp lub c #

- cplusplus, visualc++ lub c++

- Jscript

- visualbasic lub vb

- f# lub fsharp lub fs

- other — ciąg reprezentujący nazwę języka

**Tworzenie tematu Podglądu Pomocy**

Utwórz nowy dokument XHTML o nazwie ContosoTopic4.htm i dołącz tag tytułu (poniżej).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Następnie dodaj dane, aby zdefiniować sposób prezentowana tematu (bez względu na to, jak ma być prezentowany temat (bez względu na to, jak odwoływać się do tego tematu dla klawisza F1), gdzie ten temat istnieje w tokcie, jego identyfikator (w celu odwołania się do linku w innych tematach) itp. Pełną listę obsługiwanych metadanych można znaleźć w poniższej tabeli "Metadane zawartości".

- W tym przypadku użyjemy naszego własnego pakietu brandingu, wariantu pakietu Visual Studio podglądu pomocy.

- Dodaj metana nazwę i wartość F1 ("Microsoft.Help.F1" content=" ContosoTopic4"), która będzie odpowiadać podanej wartości F1 w zestawie właściwości środowiska IDE. (Aby uzyskać więcej informacji, zobacz sekcję Obsługa klawisza F1). Jest to wartość, która jest dorównana wywołaniu F1 z poziomu środowiska IDE w celu wyświetlenia tego tematu, gdy w idee ide zostanie wybrany klawisz F1.

- Dodaj identyfikator tematu. Jest to ciąg używany przez inne tematy do łączenia się z tym tematem. Jest to identyfikator Podglądu Pomocy dla tego tematu.

- W przypadku tego tematu dodaj węzeł nadrzędny tego tematu, aby zdefiniować miejsce, w którym pojawi się ten węzeł.

- W treści tego tematu dodaj kolejność węzłów. Jeśli węzeł nadrzędny ma `n` liczbę węzłów podrzędnych, zdefiniuj w kolejności węzłów podrzędnych lokalizację tego tematu. Na przykład ten temat to liczba 4 z 4 tematów podrzędnych.

Przykładowa sekcja metadanych:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**Treść tematu**

Treść tematu (bez nagłówka i stopki) będzie zawierać linki do stron, sekcję notatki, zwijany obszar, fragment kodu i sekcję tekstu specyficznego dla języka.  Zobacz sekcję brandingu, aby uzyskać informacje o tych obszarach przedstawionego tematu.

1. Dodaj tag tytułu tematu:  `<div class="title">Contoso Topic 4</div>`

2. Dodaj sekcję uwaga: `<div class="alert"> add your table tag and text </div>`

3. Dodaj zwijany obszar:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Dodaj fragment kodu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Dodaj tekst specyficzny dla języka:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Uwaga, `devLangnu=` która umożliwia wprowadzanie innych języków. Na przykład wyświetla `devLangnu="Fortran"` Ekranran, gdy fragment kodu DisplayLanguage = Analyticsran

6. Dodaj linki do stron: `<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Uwaga: w przypadku braku obsługiwanej nowej kolorowania kodu "Języka wyświetlania" (na przykład F#, Cobol, Analyticsran) we fragmencie kodu będzie monochromatyczna.

**Przykładowy temat Podgląd pomocy** Kod ilustruje sposób definiowania metadanych, fragmentu kodu, zwijanego obszaru i tekstu specyficznego dla języka.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**Obsługa klawisza F1**

W Visual Studio klawisz F1 generuje wartości podane z położenia kursora w idee i wypełnia "zestaw właściwości" dostarczonymi wartościami (na podstawie lokalizacji kursora). Gdy kursor znajduje się nad funkcją x, funkcja x jest aktywna/w trybie koncentracji uwagi i wypełnia zestaw właściwości wartościami.  Po wybraniu klawisza F1 pakiet właściwości jest wypełniany i kod F1 usługi Visual Studio wyszukuje, czy domyślne źródło pomocy klienta jest lokalne lub online (domyślnie jest to online), a następnie tworzy odpowiedni ciąg na podstawie ustawienia użytkownika (online jest ustawieniem domyślnym) — wykonanie powłoki (zobacz Przewodnik administratora pomocy dotyczący parametrów uruchamiania programu exe) z parametrami dla lokalnej przeglądarki pomocy i słów kluczowych z grupy właściwości, jeśli pomoc lokalna jest wartością domyślną lub adres URL MSDN ze słowem kluczowym na liście parametrów.

Jeśli dla klawisza F1 są zwracane trzy ciągi, nazywane ciągiem z wieloma wartościami, weź pierwszy termin, poszukaj trafienia, a jeśli zostanie znaleziony, wszystko jest gotowe. Jeśli nie, przejdź do następnego ciągu.  Kolejność ma znaczenie. Prezentacja słów kluczowych z wieloma wartościami powinna być najdłuższym ciągiem do najkrótszego ciągu.  Aby to sprawdzić w przypadku słów kluczowych o wielu wartościach, przyjrzyj się ciągowi adresu URL F1 w trybie online, który będzie zawierać wybrane słowo kluczowe.

W Visual Studio 2012 r. celowo nawiązliśmy silniejszy podział między trybem online i offline, dlatego jeśli ustawienie użytkownika miało wartość Online, po prostu przekazaliśmy żądanie F1 bezpośrednio do naszej usługi zapytań online w witrynie MSDN, a nie za pośrednictwem agenta biblioteki pomocy, który mieliśmy w programie Visual Studio 2010. Następnie opieramy się na stanie "zainstalowana zawartość dostawcy = true", aby określić, czy w tym kontekście ma być coś innego. W przypadku wartości true wykonamy tę logikę analizy i routingu w zależności od tego, co chcesz obsługiwać dla klientów. Jeśli ma wartość false, wystarczy przejść do msdn. Jeśli ustawienie użytkownika ma ustawienie Lokalne, wszystkie wywołania są przejdź do lokalnego aparatu pomocy.

Diagram przepływu F1:

![Przepływ F1](../../extensibility/internals/media/f1flow.png "F1flow")

Gdy domyślne źródło zawartości Pomocy Podglądu Pomocy jest ustawione na wartość Online (uruchom w przeglądarce):

- Visual Studio Partner (VSP) emitują wartość do worka właściwości F1 (prefiks.słowo kluczowe worka właściwości i adres URL online prefiksu znalezionego w rejestrze): klawisz F1 wysyła parametry adresu URL+ programu VSP do przeglądarki.

- Visual Studio (edytor języka, Visual Studio menu itp.): klawisz F1 wysyła Visual Studio URL do przeglądarki.

Gdy domyślne źródło zawartości Pomocy Podglądu Pomocy jest ustawione na pomoc lokalną (uruchom w Podglądzie Pomocy):

- Funkcje programu VSP, w których słowa kluczowe są zgodne między workiem właściwości F1 i indeksem magazynu lokalnego (czyli prefiks.słowo kluczowe w pępce właściwości = wartość znaleziona w indeksie magazynu lokalnego): F1 renderuje temat w Podglądzie Pomocy.

- Visual Studio funkcji (brak opcji, aby program VSP przesłonił bag właściwości emitowany przez funkcje Visual Studio): F1 renderuje Visual Studio tematu w Podglądzie Pomocy.

Ustaw następujące wartości rejestru, aby włączyć rezerwowy klawisz F1 dla zawartości pomocy dostawcy. Wartość F1 w trybie rezerwowym oznacza, że Przeglądarka Pomocy jest ustawiona do wyszukiwania zawartości Pomocy F1 w trybie online, a zawartość dostawcy jest instalowana lokalnie na dysku twardym użytkowników. Podgląd Pomocy powinien szukać zawartości w lokalnej Pomocy, mimo że ustawieniem domyślnym jest pomoc online.

1. Ustaw wartość **VendorContent** w kluczu rejestru Help 2.3:

   - W przypadku 32-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - W przypadku 64-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

2. Zarejestruj przestrzeń nazw partnera w kluczu rejestru Help 2.3:

   - W przypadku 32-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<<em> \\ nazw \> </em>

      "location"="offline"

   - W przypadku 64-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<<em> \\ nazw \> </em>

      "location"="offline"

**Analizowanie podstawowej natywnej przestrzeni nazw**

Aby włączyć analizę podstawowej natywnej przestrzeni nazw, w rejestrze dodaj nowy dword o nazwie: BaseNativeNamespaces i ustaw jego wartość na 1 (w obszarze klucza katalogu, który mają być obsługiwać).  Jeśli na przykład chcesz użyć katalogu Visual Studio, możesz dodać klucz do ścieżki:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Po napotkaniu słowa kluczowego F1 w formacie HEADER/METHOD znak "/" zostanie analizowany, co spowoduje następującą konstrukcję:

- HEADER: będzie przestrzenią nazw, która może służyć do rejestrowania w rejestrze

- METODA: stanie się to słowem kluczowym, które jest przekazywane.

Na przykład, mając niestandardową bibliotekę o nazwie CustomLibrary i metodę o nazwie MyTestMethod, gdy pojawi się żądanie F1, zostanie ono sformatowane jako `CustomLibrary/MyTestMethod` .

Użytkownik może następnie zarejestrować element CustomLibrary jako przestrzeń nazw w gałęzi Partnerzy i podać dowolny klucz lokalizacji, a słowo kluczowe przekazane do zapytania to MyTestMethod.

**Włączanie narzędzia do debugowania Pomocy w idee**

Dodaj następujący klucz rejestru i wartość:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic Help**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Dynamic Help**

::: moniker-end

Wartość: Wyświetl dane wyjściowe debugowania w danych sprzedaży detalicznej: TAK

W idee w obszarze menu Pomoc wybierz pozycję **Debuguj kontekst pomocy**.

**Metadane zawartości**

W poniższej tabeli każdy ciąg wyświetlany między nawiasami kwadratowymi jest symbolem zastępczym, który musi zostać zastąpiony rozpoznaną wartością. Na przykład w języku "[kod języka]" należy zastąpić wartością taką \<meta name="Microsoft.Help.Locale" content="[language code]" /> jak "en-us".

| Właściwość (reprezentacja HTML) | Opis |
| - | - |
| \< meta name="Microsoft.Help.Locale" content="[language-code]" /> | Ustawia ustawienie lokalne dla tego tematu. Jeśli ten tag jest używany w temacie, musi być używany tylko raz i należy go wstawić powyżej innych tagów pomocy firmy Microsoft. Jeśli ten tag nie jest używany, tekst treści tematu jest indeksowany przy użyciu wyłącznika wyrazów skojarzonego z wartościami regionalnymi produktu, jeśli jest określony; w przeciwnym razie używany jest wyłącznik wyrazów en-us. Ten tag jest zgodny ze specyfikacją ISOC RFC 4646. Aby upewnić się, że pomoc firmy Microsoft działa prawidłowo, użyj tej właściwości zamiast ogólnego atrybutu Język. |
| \< meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Ustawia ustawienie lokalne dla tego tematu, gdy używane są również inne ustawienie lokalne. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Użyj tego tagu, jeśli katalog zawiera zawartość w więcej niż jednym języku. Wiele tematów w katalogu może mieć ten sam identyfikator, ale każdy z nich musi określać unikatowy tematLokal. Temat określający wartość TopicLocale, która odpowiada ustawieniem lokalnym katalogu, jest tematem wyświetlanym w spisie treści. Jednak wszystkie wersje językowe tematu są wyświetlane w wynikach wyszukiwania. |
| \< title>[Tytuł]\</title> | Określa tytuł tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Jeśli treść tematu nie zawiera sekcji tytułu, ten tytuł jest wyświetlany w temacie i \<div> w spisie treści. |
| \< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Określa tekst linku, który jest wyświetlany w okienku indeksu w Podglądzie Pomocy. Po kliknięciu linku zostanie wyświetlony temat. Możesz określić wiele słów kluczowych indeksu dla tematu lub pominąć ten tag, jeśli nie chcesz, aby linki do tego tematu były wyświetlane w indeksie. Słowa kluczowe "K" ze starszych wersji pomocy można przekonwertować na tę właściwość. |
| \< meta name="Microsoft.Help.Id" content="[TopicID]"/> | Ustawia identyfikator dla tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Identyfikator musi być unikatowy wśród tematów w katalogu, które mają to samo ustawienie ustawień regionalnych. W innym temacie możesz utworzyć link do tego tematu przy użyciu tego identyfikatora. |
| \< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Określa słowo kluczowe F1 dla tego tematu. Możesz określić wiele słów kluczowych F1 dla tematu lub pominąć ten tag, jeśli nie chcesz, aby ten temat był wyświetlany po naciśnięciu klawisza F1 przez użytkownika aplikacji. Zazwyczaj dla tematu jest określone tylko jedno słowo kluczowe F1. Słowa kluczowe "F" ze starszych wersji pomocy można przekonwertować na tę właściwość. |
| \< meta name="Description" content="[topic description]" /> | Zawiera krótkie podsumowanie zawartości tego tematu. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Dostęp do tej właściwości jest uzyskiwany bezpośrednio przez bibliotekę zapytań; Nie jest on przechowywany w pliku indeksu. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Określa temat nadrzędny tego tematu w spisie treści. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest Microsoft.Help.Id nadrzędnego. Temat może mieć tylko jedną lokalizację w spisie treści. "-1" jest traktowany jako identyfikator tematu katalogu głównego toc. W [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] programie ta strona to Strona główna Podglądu Pomocy. Jest to ten sam powód, dla którego dodajemy wartość TocParent=-1 do niektórych tematów, aby upewnić się, że są one wyświetlane na najwyższym poziomie. Strona główna Podglądu Pomocy jest stroną systemową i dlatego nie można jej zastąpić. Jeśli program VSP spróbuje dodać stronę o identyfikatorze -1, może zostać dodana do zestawu zawartości, ale Podgląd Pomocy zawsze będzie używać strony systemowej — Strona główna Podglądu Pomocy |
| \< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/> | Określa miejsce w spisie treści tego tematu względem jego tematów równorzędnych. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest liczbą całkowitą. Temat określający liczbę całkowitą o mniejszej wartości pojawia się nad tematem określającym liczbę całkowitą o większej wartości. |
| \< meta name="Microsoft.Help.Product" content="[product code]"/> | Określa produkt, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Te informacje mogą być również podane jako parametr przekazywany do indeksatora pomocy. |
| \< meta name="Microsoft.Help.ProductVersion" content="[version number]"/> | Określa wersję produktu, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Te informacje mogą być również podane jako parametr przekazywany do indeksatora pomocy. |
| \< meta name="Microsoft.Help.Category" content="[string]"/> | Używane przez produkty do identyfikowania podsekcji zawartości. Można zidentyfikować wiele podsekcji dla tematu lub pominąć ten tag, jeśli nie chcesz, aby linki identyfikowała jakiekolwiek podsekcji. Ten tag służy do przechowywania atrybutów targetOS i TargetFrameworkMoniker podczas konwertowania tematu ze starszej wersji pomocy. Format zawartości to AttributeName:AttributeValue. |
| \< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/> | Określa tę wersję tematu, gdy w katalogu istnieje wiele wersji. Ponieważ Microsoft.Help.Id nie musi być unikatowy, ten tag jest wymagany, gdy w katalogu istnieje więcej niż jedna wersja tematu, na przykład gdy katalog zawiera temat dla programu .NET Framework 3.5 i temat dla programu .NET Framework 4 i oba mają takie same Microsoft.Help.Id. |
| \< meta name="SelfBranded" content="[TRUE or FALSE]"/> | Określa, czy w tym temacie jest używany pakiet brandingu startowego Menedżera biblioteki pomocy, czy pakiet brandingu specyficzny dla danego tematu. Ten tag musi mieć wartość TRUE lub FALSE. Jeśli ma wartość TRUE, pakiet brandingu dla skojarzonego tematu zastępuje pakiet brandingu ustawiony podczas uruchamiania Menedżera biblioteki pomocy, tak aby temat był renderowany zgodnie z zamierzoną wartością, nawet jeśli różni się od renderowania innej zawartości. Jeśli ma wartość FALSE, bieżący temat jest renderowany zgodnie z pakietem znakowania ustawionym podczas uruchamiania Menedżera biblioteki pomocy. Domyślnie Menedżer biblioteki pomocy zakłada, że znakowanie własne jest fałszywe, chyba że zmienna SelfBranded jest zadeklarowana jako TRUE; W związku z tym nie trzeba deklarować \<meta name="SelfBranded" content="FALSE"/> . |

## <a name="create-a-branding-package"></a>Tworzenie pakietu brandingu

Wersja Visual Studio obejmuje wiele różnych produktów Visual Studio, w tym izolowane i zintegrowane powłoki dla Visual Studio Partnerów.  Każdy z tych produktów wymaga pewnego stopnia obsługi brandowania zawartości Pomocy opartej na temat, unikatowej dla produktu.  Na przykład Visual Studio muszą mieć spójną prezentację marki, natomiast program SQL Studio, który opakowywuje powłokę ISO, wymaga własnego unikatowego brandowania zawartości Pomocy dla każdego tematu.  Partner programu Integrated Shell może chcieć, aby jego tematy pomocy Visual Studio nadrzędnej zawartości pomocy produktu przy zachowaniu własnego brandowania tematu.

Pakiety brandowania są instalowane przez produkt zawierający Podgląd Pomocy.  W Visual Studio produktów:

- Rezerwowy pakiet brandingu (Branding_ .msprawna) jest instalowany w katalogu głównym aplikacji Podglądu Pomocy \<locale> 2.3 (na przykład: C:\Program Files (x86)\Podgląd Pomocy firmy Microsoft\v2.3) przez pakiet językowy Podgląd pomocy.  Jest to używane w przypadkach, gdy nie zainstalowano pakietu brandingu produktu (nie zainstalowano żadnej zawartości) lub gdy zainstalowany pakiet brandingu jest uszkodzony.  Elementy Visual Studio (logo i opinie) są ignorowane, gdy jest używany główny pakiet brandingu rezerwowego aplikacji.

- Po Visual Studio zawartości z usługi pakietu zawartości instalowany jest również pakiet brandingu (w przypadku pierwszego scenariusza instalacji zawartości).  W przypadku aktualizacji pakietu brandingu aktualizacja jest instalowana po następnej aktualizacji zawartości lub kolejnej akcji instalacji pakietu.

Ten Podgląd Pomocy firmy Microsoft obsługuje znakowanie tematów na podstawie metadanych tematu.

- Tam, gdzie metadane tematu definiują znakowanie własne = true, renderuj temat w sposób, w jaki jest, nic nie robisz (o ile znakowanie).

- Gdzie metadane tematu definiują znakowanie własne = false, użyj pakietu brandingu skojarzonego z wartością metadanych TopicVendor.

- Gdzie metadane tematu definiują nazwę name="Microsoft.Help.TopicVendor" content= , użyj pakietu brandingu zdefiniowanego \< branding package name in vendor MSHA> w wartości zawartości.

- W katalogu Visual Studio znajduje się priorytetowa aplikacja pakietów brandingu.  Najpierw Visual Studio domyślne znakowanie, a następnie, jeśli jest zdefiniowane w metadanych tematu i obsługiwane za pomocą skojarzonego pakietu brandingu (zgodnie z definicją w pliku msha instalacji), znakowanie zdefiniowane przez dostawcę jest stosowane jako przesłonięcie.

Elementy brandingu zazwyczaj należą do trzech głównych kategorii:

- Elementy nagłówka (przykłady obejmują link opinii, tekst warunkowego zastrzeżenia, logo)

- Zachowania zawartości (przykłady obejmują rozwijanie/zwijanie kontrolek elementów tekstowych i elementy fragmentu kodu)

- Elementy stopki (na przykład Prawa o prawach autorskich)

Elementy uznawane za elementy markowe obejmują (szczegóły w tej specyfikacji):

- Logo katalogu/produktu (na przykład Visual Studio)

- Link do opinii i elementy wiadomości e-mail

- Tekst zastrzeżenia

- Tekst praw autorskich

Pliki obsługi w pakiecie brandingu Podgląd pomocy Visual Studio obejmują:

- Grafika (logo, ikony itp.)

- Branding.js — pliki skryptów, które obsługują zachowania zawartości

- Branding.xml — ciągi, które są stale używane w całej zawartości katalogu.  Uwaga: w Visual Studio tekstu lokalizacji w branding.xml uwzględnij _locID=" \<unique value> "

- Branding.css — definicje stylów w celu zachowania spójności prezentacji

- Printing.css — definicje stylów dla spójnej prezentacji drukowanej

Jak wspomniano powyżej, pakiety brandingu są skojarzone z tematem:

- Gdy w metadanych zdefiniowano wartość SelfBranded = false, temat dziedziczy pakiet znakowania wykazu

- Lub gdy SelfBranded = false i istnieje unikatowy pakiet znakowania zdefiniowany w języku MSHA i dostępny po zainstalowaniu zawartości

W przypadku pakietów VSPs implementowania niestandardowych pakietów brandingu (zawartość programu VSP, SelfBranded=True) jednym ze sposobów kontynuowania jest rozpoczęcie od pakietu brandingu rezerwowego (zainstalowanego z Podglądem Pomocy) i zmiana nazwy pliku zgodnie z potrzebami.  Plik Branding_ ms w pliku zip z rozszerzeniem pliku zmienionym na ms przesłonił, więc wystarczy zmienić rozszerzenie z ms chrome na .zip i wyodrębnić \<locale> zawartość.  Poniżej przedstawiono elementy pakietu brandingu i odpowiednio je zmodyfikuj (na przykład zmień logo na logo programu VSP i odwołanie do logo w pliku Branding.xml, zaktualizuj Branding.xml zgodnie ze specyficznymi dla programu VSP itp.).

Gdy wszystkie modyfikacje zostaną wprowadzone, utwórz plik zip zawierający żądane elementy brandingu i zmień rozszerzenie na .ms z rozszerzeniem.

Aby skojarzyć pakiet niestandardowych brandingów, utwórz pakiet MSHA, który zawiera odwołanie do pliku ms po znakowania wraz z zawartością msblock (zawierającą tematy).  Poniżej przedstawiono "MSHA", aby dowiedzieć się, jak utworzyć podstawową platformę MSHA.

Plik Branding.xml zawiera listę elementów używanych do spójnego renderowania określonych elementów w temacie, gdy temat zawiera element \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Poniżej Visual Studio lista elementów w Branding.xml pliku.  Ta lista ma być używana jako szablon dla użytkowników powłoki ISO, którzy modyfikują te elementy (na przykład logo, opinie i prawa własności do praw autorskich) w celu spełnienia własnych potrzeb w zakresie brandowania produktu.

Uwaga: zmienne zanotowany przez element "{n}" mają zależności kodu — usunięcie lub zmiana tych wartości spowoduje błędy i prawdopodobnie awarię aplikacji. Identyfikatory lokalizacji (na przykład _locID="codesnippet.n") są zawarte w pakiecie Visual Studio znakowania.

**Branding.xml**

| Element | Opis |
| - | - |
| Funkcji: | **CollapsibleArea** |
| Używać: | Rozwinięcie zwija tekst kontrolki zawartości |
| **Element** | **Wartość** |
| ExpandText | Rozwiń |
| CollapseText | Zwiń |
| Funkcji: | **CodeSnippet** |
| Używać: | Tekst kontrolki fragmentu kodu.  Uwaga: Zawartość fragmentu kodu ze spacją "Niepowiązywająca" zostanie zmieniona na spację. |
| **Element** | **Wartość** |
| CopyToClipboard | Kopiuj do schowka |
| ViewColorizedText | Widok pokolorowany |
| CombinedVBTabDisplayLanguage | Visual Basic (przykład) |
| Deklaracja VB | Deklaracji |
| VBUsage | Użycie |
| Funkcji: | **Opinie, stopka i logo** |
| Używać: | Udostępnij kontrolkę Opinia dla klienta, aby przekazać opinię na temat bieżącego tematu za pośrednictwem poczty e-mail.  Tekst o prawach autorskich do zawartości.  Definicja logo. |
| **Element** | **Wartość (Te ciągi można modyfikować, aby spełnić wymagania użytkowników zawartości).** |
| Prawa autorskie | © 2013 Microsoft Corporation. All rights reserved. |
| SendFeedback | \<a href="{0}" {1}>Prześlij \</a> opinię na ten temat do firmy Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName (Nazwa pliku logo) | vs_logo_bk.gif |
| LogoFileName (NazwaPliku Logo) | vs_logo_wh.gif |
| Funkcji: | **Zrzeczenie odpowiedzialności** |
| Używać: | Zestaw zastrzeżeń specyficznych dla przypadku dla zawartości przetłumaczonej maszynowo. |
| **Element** | **Wartość** |
| MT_Editable | Ten artykuł został przetłumaczony maszynnie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_NonEditable | Ten artykuł został przetłumaczony maszynnie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_QualityEditable | Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_QualityNonEditable | Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_BetaContents | Ten artykuł został przetłumaczony maszynnie do wersji wstępnej. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_BetaRecycledContents | Ten artykuł został przetłumaczony ręcznie na wersję wstępną. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| Funkcji: | **LinkTable** |
| Używać: | Obsługa linków tematu online |
| **Element** | **Wartość** |
| LinkTableTitle | Tabela linków |
| TopicEnuLinkText | Wyświetl wersję tego tematu w języku \</a> angielskim, która jest dostępna na Twoim komputerze. |
| TopicOnlineLinkText | Wyświetl ten temat \<a href="{0}" {1}> w trybie online\</a> |
| Tekst online | Tryb online |
| Funkcji: | **Kontrolka Audio wideo** |
| Używać: | Wyświetlanie elementów i tekstu dla zawartości wideo |
| **Element** | **Wartość** |
| MultiMediaNotSupported | Internet Explorer co najmniej 9 muszą być zainstalowane w celu obsługi {0} zawartości. |
| Tekst wideo | wyświetlanie wideo |
| Tekst audio | przesyłanie strumieniowe dźwięku |
| OnlineVideoLinkText | \<p>Aby wyświetlić film wideo skojarzony z tym tematem, kliknij {0} \<a href="{1}"> {2} tutaj \</a> .\</p> |
| OnlineAudioLinkText | \<p>Aby nasłuchiwać dźwięku skojarzonego z tym tematem, kliknij {0} \<a href="{1}"> {2} tutaj \</a> .\</p> |
| Funkcji: | **Kontrolka Nie zainstalowano zawartości** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania contentnotinstalled.htm |
| **Element** | **Wartość** |
| ContentNotInstalledTitle | Nie znaleziono zawartości na komputerze. |
| ContentNotInstalledDownloadContentText | \<p>Aby pobrać zawartość na komputer, \<a href="{0}" {1}> kliknij kartę \</a> Zarządzanie.\</p> |
| ContentNotInstalledText | \<p>Na komputerze nie jest zainstalowana żadna zawartość. Aby uzyskać informacje na temat lokalnej instalacji zawartości Pomocy, zobacz administratora.\</p> |
| Funkcji: | **Kontrolka Nie znaleziono tematu** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania topicnotfound.htm |
| **Element** | **Wartość** |
| TopicNotFoundTitle | Nie można odnaleźć żądanego tematu na komputerze. |
| TopicNotFoundViewOnlineText | \<p>Żądany temat nie został znaleziony na komputerze, ale można \<a href="{0}" {1}> go wyświetlić w trybie \</a> online.\</p> |
| TopicNotFoundDownloadContentText | \<p>Zobacz okienko nawigacji, aby uzyskać linki do podobnych tematów, lub kliknij \<a href="{0}" {1}> kartę Zarządzanie, \</a> aby pobrać zawartość na komputer.\</p> |
| TopicNotFoundText | \<p>Żądany temat nie został znaleziony na komputerze.\</p> |
| Funkcji: | **Uszkodzona kontrolka tematu** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania topiccorrupted.htm |
| **Element** | **Wartość** |
| TopicCorruptedTitle | Nie można wyświetlić żądanego tematu. |
| TopicCorruptedViewOnlineText | \<p>Podgląd Pomocy nie może wyświetlić żądanego tematu. W zawartości tematu lub w podstawowej zależności systemu może wystąpić błąd.\</p> |
| Funkcji: | **Kontrolka Strona główna** |
| Używać: | Tekst obsługujący wyświetlanie zawartości węzła najwyższego poziomu w Podglądzie Pomocy. |
| **Element** | **Wartość** |
| HomePageTitle | Strona główna Podglądu Pomocy |
| Strona głównaWprowadzenie | \<p>Witamy w Podgląd Pomocy firmy Microsoft, podstawowym źródle informacji dla wszystkich użytkowników narzędzi, produktów, technologii i usług firmy Microsoft. Podgląd Pomocy zapewnia dostęp do informacji z how-to i reference, przykładowego kodu, artykułów technicznych i innych informacji. Aby znaleźć potrzebną zawartość, przejrzyj spis treści, użyj wyszukiwania pełno tekstowego lub nawiguj po zawartości przy użyciu indeksu słów kluczowych.\</p> |
| HomePageContentInstallText | \<p>\<br />Na karcie \<a href="{0}" {1}> Zarządzanie zawartością wykonaj następujące \</a> czynności: Dodaj zawartość do \<ul> \<li> komputera. \</li> \<li> Sprawdź aktualizacje zawartości lokalnej. \</li> \<li> Usuń zawartość z komputera.\</li>\</ul>\</p> |
| HomePageInstalledBooks | Zainstalowane książki |
| Strona głównaNoBooksInstalowane | Nie znaleziono zawartości na komputerze. |
| HomePageHelpSettings | Ustawienia zawartości Pomocy |
| HomePageHelpSettingsText | \<p>Bieżące ustawienie to pomoc lokalna. W Podglądzie Pomocy wyświetlana jest zawartość zainstalowana na komputerze. \<br /> Aby zmienić źródło zawartości Pomocy, na pasku menu Visual Studio pomoc wybierz pozycję Pomoc, ustaw \<span style="{0}"> preferencję \</span> Pomocy.\<br />\</p> |
| Megabajt | MB |

**branding.js**

Plik branding.js zawiera kod JavaScript używany przez elementy Visual Studio podglądu pomocy.  Poniżej znajduje się lista elementów brandingu i funkcji obsługi języka JavaScript.  Wszystkie ciągi, które mają być zlokalizowane dla tego pliku, są zdefiniowane w sekcji "Ciągi zlokalizowane" w górnej części tego pliku.  Plik ICL został utworzony dla ciągów lokalizowych w branding.js pliku.

|**Funkcja brandowania**|**JavaScript, funkcja**|**Opis**|
|-|-|-|
|Var...||Definiowanie zmiennych|
|Uzyskiwanie języka kodu użytkownika|setUserPreferenceLang|mapuje indeks # na język kodu|
|Ustawianie i uzyskiwanie wartości plików cookie|getCookie, setCookie||
|Dziedziczony członek|changeMembersLabel|Rozwijanie/zwijanie dziedziczonego członka|
|When SelfBranded=False|Onload|Odczytaj ciąg zapytania, aby sprawdzić, czy jest to żądanie drukowania.  Ustaw wszystkie zestawy kodów, aby ustawić fokus na karcie preferowanej przez użytkownika.  Jeśli jest to żądanie drukowania, ustaw wartość true dla wartości isPrinterFriendly. Sprawdź tryb wysokiego kontrastu.|
|Fragment kodu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Zmień kartę||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Zapisz wszystkie zwijane obiekty sterujące na liście.|
||CA_Click|na podstawie stanu zwijanego obszaru definiuje obraz i tekst do przedstawienia|
|Obsługa kontrastu dla logo|isBlackBackground()|Wywoływana w celu określenia, czy tło jest czarne.  Dokładność tylko w trybie wysokiego kontrastu.|
||isHighContrast()|wykrywanie trybu wysokiego kontrastu przy użyciu kolorowego zakresu|
||onHighContrast(czarny)|Wywoływane po wykryciu wysokiego kontrastu|
|Funkcja LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funkcja MultiMedia|caption(begin, end, text, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||subtitle(id)||

**PLIKI HTM**

Pakiet brandingu zawiera zestaw plików HTM, które obsługują scenariusze przekazywania kluczowych informacji użytkownikom zawartości, na przykład stronę główną zawierającą sekcję opisową, które zestawy zawartości są zainstalowane, oraz strony informujące użytkownika o tym, kiedy nie można znaleźć tematów w lokalnym zestawie tematów. Te pliki HTM można modyfikować dla każdego produktu.  Dostawcy powłoki ISO mogą korzystać z domyślnego pakietu brandingu i zmieniać zachowanie i zawartość tych stron w celu ich zaadeksowania.  Te pliki odwołują się do odpowiedniego pakietu brandingu, aby tagi brandowania pozysły odpowiednią zawartość z branding.xml pliku.

|**Plik**|**Zastosowanie**|**Wyświetlane źródło zawartości**|
|-|-|-|
|homepage.htm|Jest to strona, na którym jest wyświetlana aktualnie zainstalowana zawartość oraz wszelkie inne wiadomości, które mogą być wyświetlane użytkownikowi w związku z zawartością.  Ten plik ma dodatkowy atrybut metadanych "Microsoft.Help.Id" content="-1", który umieszcza tę zawartość w górnej części toc zawartości lokalnej.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, tag \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, tag \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, tag \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Sekcja Heading Branding.xml \<HomePageInstalledBooks> tagu , dane wygenerowane z aplikacji,  \<HomePageNoBooksInstalled> gdy nie zainstalowano żadnych książek.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sekcja nagłówka Branding.xml \<HomePageHelpSettings> tagu , tekst sekcji \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Jeśli temat istnieje w zestawie lokalnym, ale z jakiegoś powodu nie można go wyświetlić (uszkodzona zawartość).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, tag \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Jeśli temat nie zostanie znaleziony w lokalnym zestawie zawartości ani nie będzie dostępny w trybie online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, tag \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, tag \<TopicNotFoundText>|
|contentnotinstalled.htm|Jeśli dla produktu nie jest zainstalowana żadna lokalna zawartość.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, tag \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, tag \<ContentNotInstalledText>|

**Pliki CSS**

Pakiet Visual Studio podglądu pomocy zawiera dwa pliki CSS do obsługi spójnej Visual Studio prezentacji zawartości Pomocy:

- Branding.css — zawiera elementy css do renderowania, gdzie SelfBranded=false

- Printer.css — zawiera elementy css do renderowania, gdzie SelfBranded=false

Pliki Branding.css zawierają definicje prezentacji tematu Visual Studio (należy pamiętać, że plik branding.css zawarty w pliku Branding_ .ms między usługą pakietu a usługą pakietów \<locale> może ulec zmianie).

**Pliki graficzne**

Visual Studio zawartości jest wyświetlane Visual Studio logo, a także inne grafiki.  Poniżej przedstawiono pełną listę plików graficznych w pakiecie Visual Studio Podgląd pomocy.

|**Plik**|**Zastosowanie**|**Przykłady**|
|-|-|-|
|clear.gif|Służy do renderowania zwijanego obszaru||
|footer_slice.gif|Prezentacja stopki||
|info_icon.gif|Używane podczas wyświetlania informacji|Disclaimer|
|online_icon.gif|Ta ikona ma być skojarzona z linkami online||
|tabLeftBD.gif|Służy do renderowania kontenera fragmentów kodu||
|tabRightBD.gif|Służy do renderowania kontenera fragmentów kodu||
|vs_logo_bk.gif|Używany do odwołań do logo o normalnym kontraście zgodnie z definicją w Branding.xml tagu \<LogoFileName> .  W Visual Studio produktów nazwa logo jest vs_logo_bk.gif.||
|vs_logo_wh.gif|Służy do odwołań do logo o dużym kontraście zgodnie z definicją w Branding.xml tagu \<LogoFileNameHC> .  W Visual Studio produktów nazwa logo jest vs_logo_wh.gif.||
|ccOff.png|Grafika napisów||
|ccOn.png|Grafika napisów||
|ImageSprite.png|Służy do renderowania zwijanego obszaru|rozwinięta lub zwiniętą grafikę|

## <a name="deploy-a-set-of-topics"></a>Wdrażanie zestawu tematów

Jest to prosty i szybki samouczek dotyczący tworzenia zestawu wdrażania zawartości Podglądu Pomocy, który składa się z pliku MSHA oraz zestawu plików cab lub MSHC zawierających tematy. MSHA jest plik XML, który opisuje zestaw plików cabs lub MS JEGO. Przeglądarka Pomocy może odczytywać zawartość MSHA w celu uzyskania listy zawartości (.CAB lub . pliki MSINSTAL) dostępne do instalacji lokalnej.

Jest to tylko elementarz opisujący bardzo podstawowy schemat XML dla przeglądarki pomocy MSHA.  Poniżej tego krótkiego przeglądu i przykładowej aplikacji HelpContentSetup.msha znajduje się przykładowa implementacja.

Nazwa MSHA na potrzeby tego tematu to HelpContentSetup.msha (nazwa pliku może być nazwą wszystkiego z rozszerzeniem . MSHA). HelpContentSetup.msha (przykład poniżej) powinien zawierać listę dostępnych cabs lub MSHCs.  Typ pliku musi być spójny w obrębie MSHA (nie obsługuje kombinacji typów plików MSHA i CAB). Dla każdego pliku CAB lub MSDZ powinien być \<div class="package"> ... \</div> (zobacz przykład poniżej).

Uwaga: w poniższym przykładzie implementacji dodano pakiet brandingu. Jest to niezwykle ważne, aby umożliwić uzyskiwanie potrzebnych Visual Studio elementów renderowania zawartości i zachowań zawartości.

Przykładowy plik HelpContentSetup.msha: (zastąp "content set name 1" i "content set name 2" itd. nazwami plików).

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. Utwórz folder lokalny, na przykład "C:\SampleContent"

2. W tym przykładzie użyjemy plików MS ZAIM, aby zawierać tematy.  PLIK MSDPOWIEDZIALNOŚCI to plik zip z rozszerzeniem pliku zmienionym z .zip na . MSRZĄDZ.

3. Utwórz poniższy plik HelpContentSetup.msha jako plik tekstowy (do utworzenia pliku został użyty Notatnik) i zapisz go w powyższym zanotowany folderze (zobacz krok 1).

Klasa "Znakowanie" istnieje i jest unikatowa. W tym zestawiearzu znajduje się znakowanie, dzięki czemu zainstalowana zawartość będzie mieć znakowanie, a zachowania zawartości zawarte w kartach MSHC będą mieć odpowiednie elementy obsługi zawarte w pakiecie brandingu. Bez tego błędy będą wynikowe, gdy system szuka elementów pomocy technicznej, które nie są częścią zgrywaną (zainstalowaną) zawartość.

Aby uzyskać pakiet Visual Studio, skopiuj plik Branding_en-US.mskov w folderze C:\Program Files (x86)\Podgląd Pomocy firmy Microsoft\v2.3\ do folderu roboczego.

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**Podsumowanie**

Użycie i rozszerzenie powyższych kroków umożliwi programom VSPs wdrażanie zestawów zawartości dla przeglądarki Visual Studio Pomocy.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Dodawanie pomocy do powłoki Visual Studio (zintegrowane i izolowane)

**Wprowadzenie**

W tym przewodniku pokazano, jak dołączyć zawartość pomocy do aplikacji Visual Studio Shell, a następnie wdrożyć ją.

**Wymagania**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Redist izolowanej powłoki](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Omówienie**

Powłoka to wersja środowiska IDE, na [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] którym można utworzyć bazę [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] aplikacji. Takie aplikacje zawierają program Isolated Shell wraz z rozszerzeniami, które tworzysz. Użyj szablonów projektów programu Isolated Shell, które są zawarte w zestawie [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, aby tworzyć rozszerzenia.

Podstawowe kroki tworzenia aplikacji opartej na programie Isolated Shell i jej pomocy:

1. Uzyskaj pakiet [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] redystrybucyjne powłoki ISO (do pobrania przez firmę Microsoft).

2. W Visual Studio pomocy, które jest oparte na programie Isolated Shell, na przykład rozszerzenia Pomocy firmy Contoso opisanego w dalszej części tego przewodnika.

3. Opakowanie rozszerzenia i pakietu redystrybucyjnego powłoki ISO do pliku MSI wdrożenia (konfiguracji aplikacji). Ten przewodnik nie zawiera kroku instalacji.

Utwórz magazyn Visual Studio zawartości. W przypadku scenariusza zintegrowanej powłoki zmień program Visual Studio12 na nazwę katalogu produktów w następujący sposób:

- Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

- Utwórz plik o nazwie CatalogType.xml i dodaj go do folderu . Plik powinien zawierać następujące wiersze kodu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Zdefiniuj magazyn zawartości w rejestrze. W przypadku programu Integrated Shell zmień program VisualStudio15 na nazwę katalogu produktów:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Klucz: Wartość ciągu LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Klucz: CatalogName String value: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation

**Tworzenie projektu**

Aby utworzyć rozszerzenie programu Isolated Shell:

1. W Visual Studio w obszarze **File**(Plik) wybierz pozycję **New Project**(Nowy projekt), w obszarze **Other Project Types** (Inne typy projektów) wybierz pozycję **Extensibility**(Rozszerzalność), a Visual Studio Shell Isolated (Izolowana **powłoka).** Nadaj projektowi nazwę ), aby utworzyć projekt rozszerzalności na podstawie szablonu `ContosoHelpShell` Visual Studio Shell.

2. W Eksplorator rozwiązań w projekcie ContosoHelpShellUI w folderze Pliki zasobów otwórz plik ApplicationCommands.vsct. Upewnij się, że ten wiersz jest w komentarzu (wyszukaj "No_Help"): `<!-- <define name="No_HelpMenuCommands"/> -->`

3. Wybierz klawisz F5, aby skompilować i uruchomić polecenie **Debuguj.** W eksperymentalnym wystąpieniu środowiska IDE isolated Shell wybierz menu **Pomoc.** Upewnij się, że wyświetlane są polecenia Wyświetl **Pomoc,** **Dodaj i Usuń zawartość** pomocy oraz Ustaw **preferencje** pomocy.

4. W Eksplorator rozwiązań projektu ContosHelpShell w folderze Dostosowywanie powłoki otwórz plik ContosoHelpShell.pkgdef. Aby zdefiniować katalog Pomocy firmy Contoso, dodaj następujące wiersze:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. W Eksplorator rozwiązań projektu ContosHelpShell w folderze Dostosowywanie powłoki otwórz plik ContosoHelpShell.Application.pkgdef. Aby włączyć Pomoc F1, dodaj następujące wiersze:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. W Eksplorator rozwiązań menu kontekstowym rozwiązania ContosoHelpShell wybierz element **menu** Właściwości. W **obszarze Właściwości konfiguracji** wybierz pozycję **Menedżer konfiguracji**. W kolumnie **Konfiguracja** zmień każdą wartość "Debuguj" na "Wydanie".

7. Skompiluj rozwiązanie. Spowoduje to utworzenie zestawu plików w folderze wydania, który będzie używany w następnej sekcji.

Aby przetestować to tak, jakby zostały wdrożone:

1. Na komputerze, na który wdrażasz firmę Contoso, zainstaluj pobraną (z powyższego) powłokę ISO.

2. Utwórz folder w \\ folderze \Program Files (x86) \\ i nadaj temu folderowi nazwę `Contoso` .

3. Skopiuj zawartość z folderu wydania ContosoHelpShell do \\ folderu \Program Files (x86)\Contoso\.

4. Uruchom Edytor rejestru, wybierając polecenie  **Uruchom** w menu **Start** i wprowadzając polecenie `Regedit` . W edytorze rejestru wybierz pozycję **Plik**, a następnie pozycję **Importuj**. Przejdź do folderu projektu ContosoHelpShell. W podfolderze ContosoHelpShell wybierz pozycję ContosoHelpShell.reg.

5. Tworzenie magazynu zawartości:

    Dla powłoki ISO — utwórz magazyn zawartości firmy Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    W [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] przypadku programu Integrated Shell utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Utwórz CatalogType.xml i dodaj do magazynu zawartości (poprzedni krok) zawierający:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Dodaj następujące klucze rejestru:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: Wartość ciągu LocationPath:

    Dla powłoki ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Zintegrowana powłoka:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Klucz: CatalogName String value: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Documentation. W przypadku powłoki ISO jest to nazwa katalogu.

8. Skopiuj zawartość (cabs lub MSUJESZ i MSHA) do folderu lokalnego.

9. Przykład wiersza polecenia zintegrowanej powłoki do testowania magazynu zawartości. W przypadku powłoki ISO zmień katalog i uruchamiaj wartości aplikacji zgodnie z potrzebami, aby dopasować je do produktu.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Uruchom aplikację firmy Contoso (z katalogu głównego aplikacji firmy Contoso). W obrębie powłoki ISO wybierz element **menu** Pomoc i zmień wartość pozycji Ustaw preferencję **pomocy** na Użyj **pomocy lokalnej.**

11. W obrębie powłoki wybierz element menu **Pomoc,** a następnie **pozycję Wyświetl pomoc.** Powinna zostać uruchomina lokalna przeglądarka Pomocy. Wybierz **kartę Zarządzanie zawartością.** W **obszarze Źródło instalacji** wybierz przycisk Dysk.  Wybierz przycisk **...** i przejdź do folderu lokalnego zawierającego zawartość firmy Contoso (skopiowaną do folderu lokalnego w powyższym kroku). Wybierz pozycję HelpContentSetup.msha. Firma Contoso powinna teraz być pokazywana jako książka w wybranych książkach. Wybierz **pozycję** Dodaj, a następnie wybierz przycisk **Aktualizuj** (prawy dolny róg).

12. W ramach środowiska IDE firmy Contoso wybierz klawisz F1, aby przetestować funkcjonalność F1.

## <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać informacje na temat interfejsu API środowiska uruchomieniowego, zobacz [Interfejs API pomocy systemu Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Aby uzyskać więcej informacji na temat sposobu wykorzystania interfejsu API pomocy, zobacz [Przykłady kodu Podglądu Pomocy.](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples)

Sugestie dotyczące funkcji można przesyłać na [Developer Community](https://aka.ms/feedback/suggest?space=8).
