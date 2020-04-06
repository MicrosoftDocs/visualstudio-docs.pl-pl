---
title: Pakiet SDK przeglądarki pomocy firmy Microsoft | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707152"
---
# <a name="microsoft-help-viewer-sdk"></a>Zestaw SDK Podglądu Pomocy firmy Microsoft

Ten artykuł zawiera następujące zadania dla integratorów programu Visual Studio Help Viewer:

- Tworzenie tematu (obsługa F1)

- Tworzenie pakietu znakowania zawartości podglądu pomocy

- Wdrażanie zestawu artykułów

- Dodawanie pomocy do powłoki programu Visual Studio (zintegrowanej lub izolowanej)

- Dodatkowe zasoby

## <a name="create-a-topic-f1-support"></a>Tworzenie tematu (obsługa F1)

Ta sekcja zawiera omówienie składników przedstawionego tematu, wymagania dotyczące tematu, krótki opis sposobu tworzenia tematu (w tym wymagania dotyczące obsługi F1) i wreszcie przykładowy temat z jego renderowanym wynikiem.

**Omówienie tematu przeglądarki Pomocy**

Gdy temat jest wywoływany do renderowania, Podgląd pomocy pobiera elementy pakietu znakowania, które są skojarzone z tematem w momencie instalacji lub ostatniej aktualizacji, wraz z tematem XHTML i łączy te dwa, aby spowodować wyświetlenie prezentowanej zawartości (dane znakowania + dane tematu).  Pakiet znakowania zawiera logo, obsługę zachowań treści i tekst marki (prawa autorskie itp.).  Zobacz "Tworzenie pakietu brandingowego" poniżej, aby uzyskać więcej informacji na temat elementów pakietu znakowania.  W przypadku, gdy nie ma pakietu znakowania skojarzonego z tematem, Podgląd pomocy użyje rezerwowego pakietu znakowania znajdującego się w katalogu głównym aplikacji Help Viewer (Branding_en-US.mshc).

**Wymagania dotyczące tematu przeglądarki pomocy**

Aby zawartość tematu nieprzetworzonego była poprawnie renderowana w przeglądarce pomocy, musi to być format W3C Basic 1.1 XHTML.

Temat zazwyczaj zawiera dwie sekcje:

- Metadane (zobacz Odwołanie do metadanych zawartości): dane dotyczące tematu, na przykład unikatowy identyfikator tematu, wartość słowa kluczowego, identyfikator toc tematu, identyfikator węzła nadrzędnego itp.

- Zawartość treści: zgodna z W3C Basic 1.1 XHTML, która obejmuje obsługiwane zachowania zawartości (składany obszar, fragment kodu itp. Pełna lista znajduje się poniżej).

Obsługiwane formanty pakietu znakowania programu Visual Studio:

- Linki

- KodWysłumia

- SkładanyObsza

- Dziedziczony element członkowski

- LanguageSpecificText (Język)

Obsługiwane ciągi językowe (bez rozróżniania wielkości liter):

- javascript

- csharp lub c #

- cplusplus lub visualc++ lub c++

- Jscript

- wizualne lub vb

- f# lub fsharp lub fs

- inne - ciąg reprezentujący nazwę języka

**Tworzenie tematu Podglądu pomocy**

Utwórz nowy dokument XHTML o nazwie ContosoTopic4.htm i dołącz tag tytułowy (poniżej).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Następnie dodaj dane, aby zdefiniować, jak temat ma być przedstawiony (markowe lub nie), jak odwoływać się do tego tematu dla F1, gdzie ten temat istnieje w toc, jego identyfikator (dla odwołania link przez inne tematy), itp. Pełna lista obsługiwanych metadanych znajduje się w poniższej tabeli "Metadane zawartości".

- W takim przypadku użyjemy naszego własnego pakietu znakowania, wariant pakietu znakowania programu Visual Studio Help Viewer.

- Dodaj nazwę i wartość meta F1 ("Microsoft.Help.F1" content=" ContosoTopic4"), która będzie zgodna z podaną wartością F1 w torbie właściwości IDE. (Więcej informacji można znaleźć w sekcji Obsługa F1). Jest to wartość, która jest dopasowywała się do wywołania F1 z poziomu IDE, aby wyświetlić ten temat, gdy F1 jest wybrany w IDE.

- Dodaj identyfikator tematu. Jest to ciąg, który jest używany przez inne tematy, aby połączyć się z tym tematem. Jest to identyfikator podglądu pomocy dla tego tematu.

- W przypadku toc dodaj węzeł nadrzędny tego tematu, aby zdefiniować, gdzie pojawi się węzeł TOC tego tematu.

- W przypadku toc dodaj kolejność węzłów tego tematu. Gdy węzeł nadrzędny ma `n` liczbę węzłów podrzędnych, zdefiniuj w kolejności węzłów podrzędnych lokalizację tego tematu. Na przykład ten temat jest numerem 4 z 4 tematów podrzędnych.

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

Treść (z wyłączeniem nagłówka i stopki) tematu będzie zawierać łącza do stron, sekcję notatek, obszar zwijany, fragment kodu i sekcję tekstu specyficznego dla języka.  Zobacz sekcję znakowania, aby uzyskać informacje na temat tych obszarów prezentowanego tematu.

1. Dodaj tag tytułu tematu:`<div class="title">Contoso Topic 4</div>`

2. Dodaj sekcję notatki:`<div class="alert"> add your table tag and text </div>`

3. Dodaj obszar składany:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Dodaj fragment kodu:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Dodaj tekst specyficzny dla `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` języka `devLangnu=` kodu: Uwaga, która umożliwia wprowadzanie innych języków. Na przykład `devLangnu="Fortran"` wyświetla Fortran, gdy fragment kodu DisplayLanguage = Fortran

6. Dodaj łącza do stron:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Uwaga: dla nieobjętego nową kolorystykę kodu "Display Language" (np.

**Przykładowy temat podglądu pomocy** Kod ilustruje sposób definiowania metadanych, fragment kodu, zwijany obszar i tekst specyficzny dla języka.

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

**Wsparcie F1**

W programie Visual Studio wybranie F1 generuje wartości dostarczone z rozmieszczenia kursora w IDE i wypełnia "worka właściwości" z podanych wartości (na podstawie lokalizacji kursora. Gdy kursor jest ponad funkcję x, funkcja x jest aktywny/w fokusie i wypełnia worka właściwości z wartościami.  Po wybraniu F1 torba właściwości jest wypełniona, a kod Visual Studio F1 sprawdza, czy domyślne źródło Pomocy klientów jest lokalne lub online (w trybie online jest ustawieniem domyślnym), a następnie tworzy odpowiedni ciąg na podstawie ustawienia użytkowników (online jest ustawieniem domyślnym) - wykonanie powłoki (patrz Przewodnik administratora pomocy dla parametrów uruchamiania exe) z parametrami dla lokalnej przeglądarki pomocy + słowa kluczowego z worka właściwości, jeśli pomoc lokalna jest domyślna lub adres URL MSDN ze słowem kluczowym na liście parametrów.

Jeśli trzy ciągi są zwracane dla F1, określane jako ciąg wielowartowiowy, weź pierwszy termin, poszukaj trafienia, a jeśli zostanie znaleziony, skończymy; jeśli nie, przejdź do następnego ciągu.  Porządek ma znaczenie. Prezentacja wielowartościowych słów kluczowych powinna być najdłuższym ciągiem do najkrótszego ciągu.  Aby to sprawdzić w przypadku słów kluczowych o wielu wartościach, przyjrzyj się ciągowi adresu URL online F1, który będzie zawierał wybrane słowo kluczowe.

W programie Visual Studio 2012 celowo dokonaliśmy silniejszego podziału między trybem online i offline, dzięki czemu jeśli ustawienie użytkownika było dla trybu online, po prostu przekazaliśmy żądanie F1 bezpośrednio do naszej usługi zapytań online w usłudze MSDN, zamiast routingu za pośrednictwem agenta biblioteki pomocy, który mieliśmy w programie Visual Studio 2010. Następnie polegamy na stanie "zawartość dostawcy zainstalowana = true", aby ustalić, czy zrobić coś innego w tym kontekście. Jeśli true, następnie wykonać tę logikę analizowania i routingu w zależności od tego, co chcesz obsługiwać dla klientów. Jeśli false, to po prostu przejść do MSDN. Jeśli ustawienie użytkownika jest lokalne, a następnie wszystkie wywołania przejdź do lokalnego aparatu pomocy.

Schemat przepływu F1:

![Przepływ F1](../../extensibility/internals/media/f1flow.png "Przepływ F1")

Gdy domyślne źródło zawartości pomocy Podglądu Pomocy jest ustawione w trybie online (Uruchom w przeglądarce):

- Funkcje programu Visual Studio Partner (VSP) emitują wartość do worka właściwości F1 (prefiksu worka właściwości.keyword i internetowego adresu URL dla prefiksu znajdującego się w rejestrze): F1 wysyła parametry adresu URL+ vsp do przeglądarki.

- Funkcje programu Visual Studio (edytor języka, elementy menu specyficzne dla programu Visual Studio itp.): F1 wysyła adres URL programu Visual Studio do przeglądarki.

Gdy domyślne źródło zawartości pomocy Podglądu Pomocy jest ustawione na Pomoc lokalną (Uruchom w Przeglądarce pomocy):

- Vsp funkcje, gdzie słowo kluczowe pasuje między F1 bag właściwości i indeksu magazynu lokalnego (czyli prefiks worka właściwości.keyword = wartość znaleziona w indeksie magazynu lokalnego): F1 renderuje temat w Podglądzie pomocy.

- Visual Studio funkcje (nie ma opcji dla VSP zastąpić worek właściwości emitowanych z funkcji programu Visual Studio): F1 renderuje visual studio temat w Podglądzie pomocy.

Ustaw następujące wartości rejestru, aby włączyć zawartość Pomocy dostawcy F1. F1 Rezerwa oznacza, że Podgląd pomocy jest ustawiony na poszukiwanie zawartości Pomocy F1 w trybie online, a zawartość dostawcy jest instalowana lokalnie na dysku twardym użytkowników. Podgląd pomocy powinien sprawdzić lokalną Pomoc dotyczącą zawartości, nawet jeśli domyślnym ustawieniem jest pomoc online.

1. Ustaw wartość **Dostawcy w** kluczu rejestru Pomocy 2.3:

   - W przypadku 32-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Katalogi\VisualStudio15

        "DostawcaContent"=dword:00000001

   - W przypadku 64-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogi\VisualStudio15

        "DostawcaContent"=dword:00000001

2. Zarejestruj obszar nazw partnera pod kluczem rejestru Pomocy 2.3:

   - W przypadku 32-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Obszar<em> \\ nazw<partnerów\></em>

      "lokalizacja"="offline"

   - W przypadku 64-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Obszar nazw<em> \\<partnerów\></em>

      "lokalizacja"="offline"

**Analizowanie natywnego obszaru nazw bazowego**

Aby włączyć analizowanie macierzystego obszaru nazw bazy, w rejestrze dodaj nowy DWORD o nazwie: BaseNativeNamespaces i ustaw jego wartość na 1 (w ramach klucza katalogu, który mają obsługiwać).  Na przykład jeśli chcesz użyć katalogu programu Visual Studio, można dodać klucz do ścieżki:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogi\VisualStudio15

Po napotkaniu słowa kluczowego F1 w formacie NAGŁÓWEK/METODA znak '/' zostanie przeanalizowany, co spowoduje następującą konstrukcję:

- NAGŁÓWEK: będzie przestrzenią nazw, która może służyć do rejestracji w rejestrze

- METODA: stanie się to słowem kluczowym, które zostanie przekazane.

Na przykład, biorąc pod uwagę bibliotekę niestandardową o nazwie CustomLibrary i metodę o nazwie MyTestMethod, gdy pojawi się żądanie F1, zostanie sformatowany jako `CustomLibrary/MyTestMethod`.

Użytkownik może następnie zarejestrować CustomLibrary jako obszar nazw w obszarze hive partnerów i podać dowolny klucz lokalizacji, które pragną, a słowo kluczowe przekazane do kwerendy będzie MyTestMethod.

**Włącz narzędzie do debugowania pomocy w idei**

Dodaj następujący klucz i wartość rejestru:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\15.0\Pomoc dynamiczna**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER\Oprogramowanie\Microsoft\VisualStudio\16.0\Pomoc dynamiczna**

::: moniker-end

Wartość: Wyświetlanie danych wyjściowych debugowania w danych detalicznych: TAK

W obszarze IDE w obszarze menu Pomoc wybierz pozycję **Debugować kontekst pomocy**.

**Metadane zawartości**

W poniższej tabeli dowolny ciąg, który pojawia się między nawiasami jest symbolem zastępczym, który musi zostać zastąpiony przez rozpoznaną wartość. Na przykład \<w meta name="Microsoft.Help.Locale" content="[language code]" />,"[kod języka]" musi zostać zastąpiony przez wartość, taką jak "en-us".

| Właściwość (reprezentacja HTML) | Opis |
| - | - |
| \<meta name="Microsoft.Help.Locale" content="[language-code]" /> | Ustawia ustawienia regionalne dla tego tematu. Jeśli ten tag jest używany w temacie, musi być używany tylko raz i musi być wstawiony nad innymi tagami Pomocy Firmy Microsoft. Jeśli ten tag nie jest używany, tekst podstawowy tematu jest indeksowany przy użyciu funkcji podziału wyrazów skojarzonej z ustawieniami lokalnymi produktu, jeśli jest określony; w przeciwnym razie używany jest wyłącznik wyrazów en-us. Ten tag jest zgodny z normą ISOC RFC 4646. Aby upewnić się, że Pomoc firmy Microsoft działa poprawnie, użyj tej właściwości zamiast ogólnego atrybutu Language. |
| \<meta name="Microsoft.Help.TopicLocale" content="[language-code]" /> | Ustawia ustawienia regionalne dla tego tematu, gdy używane są również inne ustawienia regionalne. Jeśli ten tag jest używany w temacie, musi być użyty tylko raz. Użyj tego tagu, gdy katalog zawiera zawartość w więcej niż jednym języku. Wiele tematów w katalogu może mieć ten sam identyfikator, ale każdy musi określić unikatowy TopicLocale. Temat, który określa TopicLocale, który pasuje do ustawień regionalnych katalogu jest temat, który jest wyświetlany w spisie treści. Jednak wszystkie wersje językowe tematu są wyświetlane w wynikach wyszukiwania. |
| \<tytuł>[Tytuł]\</tytuł> | Określa tytuł tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Jeśli treść tematu nie zawiera \<sekcji> tytuł, ten tytuł jest wyświetlany w temacie i w spisie treści. |
| \<meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Określa tekst łącza wyświetlanego w okienku indeksu Podglądu pomocy. Po kliknięciu łącza zostanie wyświetlony temat. Można określić wiele słów kluczowych indeksu dla tematu lub można pominąć ten tag, jeśli nie chcesz, aby łącza do tego tematu były wyświetlane w indeksie. Słowa kluczowe "K" z wcześniejszych wersji Pomocy można przekonwertować na tę właściwość. |
| \<meta name="Microsoft.Help.Id" content="[TopicID]"/> | Ustawia identyfikator dla tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Identyfikator musi być unikatowy wśród tematów w katalogu, które mają takie same ustawienia regionalne. W innym temacie można utworzyć łącze do tego tematu przy użyciu tego identyfikatora. |
| \<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Określa słowo kluczowe F1 dla tego tematu. Można określić wiele słów kluczowych F1 dla tematu lub można pominąć ten tag, jeśli nie chcesz, aby ten temat był wyświetlany, gdy użytkownik aplikacji naciska F1. Zazwyczaj tylko jedno słowo kluczowe F1 jest określony dla tematu. Słowa kluczowe "F" z wcześniejszych wersji Pomocy można przekonwertować na tę właściwość. |
| \<meta name="Opis" content="[opis tematu]" /> | Zawiera krótkie podsumowanie zawartości w tym temacie. Jeśli ten tag jest używany w temacie, musi być użyty tylko raz. Ta właściwość jest dostępna bezpośrednio przez bibliotekę zapytań; nie jest przechowywany w pliku indeksu. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Określa temat nadrzędny tego tematu w spisie treści. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest Microsoft.Help.Id nadrzędnego. Temat może mieć tylko jedną lokalizację w spisie treści. "-1" jest uważany za identyfikator tematu dla katalogu głównego TOC. W [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]tej stronie znajduje się strona główna programu Help Viewer. Jest to ten sam powód, dla którego specjalnie dodamy TocParent=-1 do niektórych tematów, aby upewnić się, że pojawiają się na najwyższym poziomie. Strona główna Programu Help Viewer jest stroną systemową, która nie jest wymienna. Jeśli vsp próbuje dodać stronę o identyfikatorze -1, może zostać dodany do zestawu zawartości, ale Podgląd pomocy zawsze będzie korzystać ze strony systemowej — Help Viewer Home |
| \<meta name="Microsoft.Help.TocOrder" content="[dodatnia wartość całkowita]"/> | Określa, gdzie w spisie treści ten temat pojawia się względem jego tematów równorzędnych. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest całkowitej liczby. Temat określający liczbę całkowitą o niższej wartości pojawia się nad tematem określającym liczbę całkowitą o wyższej wartości. |
| \<meta name="Microsoft.Help.Product" content="[kod produktu]"/> | Określa produkt, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi być użyty tylko raz. Te informacje mogą być również dostarczane jako parametr, który jest przekazywany do indeksatora Pomocy. |
| \<meta name="Microsoft.Help.ProductVersion" content="[numer wersji]"/> | Określa wersję produktu, którą opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi być użyty tylko raz. Te informacje mogą być również dostarczane jako parametr, który jest przekazywany do indeksatora Pomocy. |
| \<meta name="Microsoft.Help.Category" content="[string]"/> | Używane przez produkty do identyfikacji podsekcji treści. Można zidentyfikować wiele podsekcji dla tematu lub pominąć ten tag, jeśli nie chcesz, aby łącza identyfikować podsekcje. Ten tag jest używany do przechowywania atrybutów targetos i TargetFrameworkMoniker, gdy temat jest konwertowany z wcześniejszej wersji Pomocy. Formatem zawartości jest AttributeName:AttributeValue. |
| \<meta name="Microsoft.Help.TopicVersion content="[numer wersji tematu]"/> | Określa tę wersję tematu, gdy w katalogu istnieje wiele wersji. Ponieważ Microsoft.Help.Id nie jest gwarantowana jest unikatowa, ten tag jest wymagany, gdy w katalogu istnieje więcej niż jedna wersja tematu, na przykład gdy katalog zawiera temat dla programu .NET Framework 3.5 i temat dla programu .NET Framework 4 i oba mają ten sam Microsoft.Help.Id. |
| \<meta name="SelfBranded" content="[PRAWDA lub FAŁSZ]"/> | Określa, czy w tym temacie jest używany pakiet znakowania startowego Menedżera bibliotek pomocy, czy pakiet znakowania, który jest specyficzny dla danego tematu. Ten tag musi być prawda lub fałsz. Jeśli jest to prawda, pakiet znakowania dla skojarzonego tematu zastępuje pakiet znakowania, który jest ustawiany podczas uruchamiania Menedżera biblioteki pomocy, dzięki czemu temat jest renderowany zgodnie z przeznaczeniem, nawet jeśli różni się od renderowania innej zawartości. Jeśli jest false, bieżący temat jest renderowany zgodnie z pakietem znakowania, który jest ustawiany po uruchomieniu Menedżera biblioteki pomocy. Domyślnie Menedżer bibliotek pomocy zakłada, że samomarkowanie jest fałszywe, chyba że zmienna SelfBranded jest zadeklarowana jako PRAWDA; w związku z tym nie \<trzeba deklarować meta name="SelfBranded" content="FALSE"/>. |

## <a name="create-a-branding-package"></a>Tworzenie pakietu znakowania

Wydanie programu Visual Studio obejmuje wiele różnych produktów programu Visual Studio, w tym izolowane i zintegrowane powłoki dla partnerów programu Visual Studio.  Każdy z tych produktów wymaga pewnego stopnia obsługi znakowania zawartości pomocy opartej na temacie, unikalnej dla produktu.  Na przykład tematy programu Visual Studio muszą mieć spójną prezentację marki, podczas gdy program SQL Studio, który otacza powłokę ISO, wymaga własnego unikatowego znakowania zawartości Pomocy dla każdego tematu.  Zintegrowany partner powłoki może chcieć, aby ich tematy Pomocy znajdują się w nadrzędnej zawartości pomocy produktu programu Visual Studio przy zachowaniu ich własnych tematów.

Pakiety znakowania są instalowane przez produkt zawierający Podgląd pomocy.  W przypadku produktów programu Visual Studio:

- Rezerwowy pakiet znakowania (Branding_\<ustawieniami regionalnymi>.mshc) jest zainstalowany w katalogu głównym aplikacji Help Viewer 2.3 (przykład: C:\Program Files (x86)\Microsoft Help Viewer\v2.3) w pakiecie językowym Podgląd pomocy.  Jest to używane w przypadkach, gdy pakiet znakowania produktu nie jest zainstalowany (nie zainstalowano zawartości) lub gdy zainstalowany pakiet znakowania jest uszkodzony.  Elementy programu Visual Studio (logo i opinie) są ignorowane, gdy używany jest pakiet znakowania rezerwowego katalogu głównego aplikacji.

- Gdy zawartość programu Visual Studio jest instalowana z usługi pakietu zawartości, pakiet znakowania jest również zainstalowany (w scenariuszu instalacji zawartości po raz pierwszy).  Jeśli istnieje aktualizacja pakietu znakowania, aktualizacja jest instalowana, gdy nastąpi następna aktualizacja zawartości lub akcja instalacji dodatkowego pakietu.

Przeglądarka Pomocy firmy Microsoft obsługuje znakowanie tematów na podstawie metadanych tematów.

- Gdzie metadane tematu definiuje self branded = true, renderuj temat tak, jak jest, nie rób nic (jeśli chodzi o znakowanie).

- Gdzie metadane tematu definiuje self branded = false, należy użyć pakietu znakowania skojarzonego z topicvendor wartości metadanych.

- Gdzie metadane tematu definiuje name="Microsoft.Help.TopicVendor" content=\< nazwa pakietu znakowania w> dostawcy MSHA, należy użyć pakietu znakowania zdefiniowanego w wartości zawartości.

- W katalogu programu Visual Studio istnieje priorytet aplikacji pakietów znakowania.  Najpierw jest stosowana domyślna znakowanie programu Visual Studio, a następnie, jeśli jest zdefiniowana w metadanych tematu i obsługiwana za pomocą skojarzonego pakietu znakowania (zgodnie z definicją w instalacyjnym msha), znakowanie zdefiniowane przez dostawcę jest stosowane jako zastąpienie.

Elementy brandingu zazwyczaj dzielą się na trzy główne kategorie:

- Elementy nagłówka (przykłady obejmują link do opinii, tekst zastrzeżenia warunkowego, logo)

- Zachowania zawartości (przykłady obejmują rozwijanie/zwijanie elementów tekstu kontrolnego i elementy fragmentu kodu)

- Elementy stopki (przykład Prawa autorskie)

Elementy uważane za elementy markowe obejmują (wyszczególnione w tej specyfikacji):

- Logo katalogu/produktu (np. visual studio)

- Łącze opinii i elementy wiadomości e-mail

- Tekst zastrzeżenia

- Tekst praw autorskich

Pliki pomocnicze w pakiecie znakowania programu Visual Studio Help Viewer obejmują:

- Grafika (logo, ikony itp.)

- Branding.js - pliki skryptów obsługujące zachowania zawartości

- Branding.xml - ciągi, które są konsekwentnie używane w całej zawartości katalogu.  Uwaga: w przypadku elementów tekstowych lokalizacji programu Visual Studio w pliku\<branding.xml dołącz _locID=" unikatową wartość>"

- Branding.css - definicje stylów dla spójności prezentacji

- Printing.css - definicje stylów dla spójnej prezentacji drukowanej

Jak wspomniano powyżej, pakiety brandingowe są skojarzone z tematem:

- Gdy SelfBranded = false jest zdefiniowany w metadanych, temat dziedziczy pakiet znakowania katalogu

- Lub gdy SelfBranded = false i istnieje unikalny pakiet znakowania zdefiniowane w MSHA i dostępne po zainstalowaniu zawartości

W przypadku pakietów marki niestandardowych (zawartość VSP, SelfBranded=True) jednym ze sposobów, aby kontynuować, jest rozpoczęcie od rezerwowego pakietu znakowania (zainstalowanego za pomocą Podglądu pomocy) i zmiana nazwy pliku.  Branding_\<>.mshc plik jest plik zip z rozszerzeniem pliku zmienionego na .mshc, więc po prostu zmień rozszerzenie z .mshc na .zip i wyodrębnij zawartość.  Poniżej znajdują się elementy pakietu znakowania i modyfikuj odpowiednio (na przykład zmień logo na logo VSP i odwołanie do logo w pliku Branding.xml, zaktualizuj plik Branding.xml na specyfikę VSP itp.).

Po zakończeniu wszystkich modyfikacji utwórz plik zip zawierający żądane elementy znakowania i zmień rozszerzenie na .mshc.

Aby skojarzyć niestandardowy pakiet znakowania, utwórz MSHA, który zawiera odwołanie do pliku mshc znakowania wraz z zawartością mshc (zawierającą tematy).  Poniżej znajduje się "MSHA", aby dowiedzieć się, jak utworzyć podstawowe MSHA.

Plik Branding.xml zawiera listę elementów używanych do spójnego renderowania określonych \<elementów w temacie, gdy temat zawiera meta name="Microsoft.Help.SelfBranded" content="false"/>.  Lista elementów programu Visual Studio w pliku Branding.xml jest wymieniona poniżej.  Ta lista jest przeznaczona do użycia jako szablon dla użytkowników powłoki ISO, gdzie modyfikują te elementy (na przykład logo, opinie i prawa autorskie) w celu zaspokojenia własnych potrzeb związanych z znakowaniem produktów.

Uwaga: zmienne wymienione przez "{n}" mają zależności kodu - usunięcie lub zmiana tych wartości spowoduje błędy i ewentualnie awarię aplikacji. Identyfikatory lokalizacji (przykład _locID="codesnippet.n") są zawarte w pakiecie znakowania programu Visual Studio.

**Znakowanie.xml**

| | |
| - | - |
| Funkcji: | **SkładanyObsza** |
| Używać: | Rozwiń zwija tekst formantu zawartości |
| **Element** | **Wartość** |
| Rozwijaj tekst | Rozwiń |
| Zwiń Tekst | Zwiń |
| Funkcji: | **KodWysłumia** |
| Używać: | Tekst sterujący fragmentem kodu.  Uwaga: Zawartość fragmentu kodu z miejscem "Non-Breaking" zostanie zmieniona na miejsce. |
| **Element** | **Wartość** |
| Płyta copytoclipboard | Kopiuj do schowka |
| ViewColorizedText (Tekst kolorowy) | Wyświetl pokolorowane |
| PołączenieVBTabDisplayLanguage | Visual Basic (przykład) |
| Deklaracja VB | Deklaracji |
| VbUsage (vbusage) | Sposób użycia |
| Funkcji: | **Opinie, stopka i logo** |
| Używać: | Przekaż kontrolę opinii dla klienta, aby przekazać opinię na temat bieżącego tematu za pośrednictwem poczty e-mail.  Tekst praw autorskich do treści.  Definicja logo. |
| **Element** | **Wartość (Te ciągi mogą być modyfikowane w celu zaspokojenia potrzeb przysposabiacza zawartości).** |
| Prawa autorskie | © 2013 microsoft corporation. Wszelkie prawa zastrzeżone. |
| Wyślij zwrotny | \<a{0}href=" {1} " ">\<Wyślij opinię /a> na ten temat do firmy Microsoft. |
| FeedbackLink (Link opinii) | |
| Tytuł logo | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Funkcji: | **Disclaimer** |
| Używać: | Zestaw zastrzeżenia do poszczególnych przypadków dla zawartości przetłumaczonej maszynowo. |
| **Element** | **Wartość** |
| MT_Editable | Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_NonEditable | Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_QualityEditable | Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_QualityNonEditable | Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_BetaContents | Ten artykuł został przetłumaczony na maszynę do wstępnego wydania. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| MT_BetaRecycledContents | Ten artykuł został przetłumaczony ręcznie dla wstępnego wydania. Jeśli masz połączenie z Internetem, wybierz opcję "Wyświetl ten temat w trybie online", aby wyświetlić tę stronę w trybie edytowalnym z oryginalną zawartością w języku angielskim w tym samym czasie. |
| Funkcji: | **Tabela łączy** |
| Używać: | Obsługa linków do tematów online |
| **Element** | **Wartość** |
| LinkTableTitle (Tabela powiązań) | Tabela łączy |
| TopicEnuLinkText (TopicEnuLinkText) | Zobacz angielską\<wersję /a> tego tematu, który jest dostępny na komputerze. |
| TopicOnlineLinkText (TopicOnlineLinkText) | Zobacz ten \<temat a{0} {1} href=" "\<>online /a> |
| Tekst online | Online |
| Funkcji: | **Sterowanie dźwiękiem wideo** |
| Używać: | Wyświetlanie elementów i tekstu dla zawartości wideo |
| **Element** | **Wartość** |
| MultiMediaNotSupportowane | Do obsługi {0} zawartości należy zainstalować program Internet Explorer 9 lub noc. |
| Tekst wideo | wyświetlanie wideo |
| Tekst audio | strumieniowe przesyłanie dźwięku |
| OnlineVideoLinkText | \<p>Aby wyświetlić film skojarzony z {0} \<tym tematem,{1}kliknij href=" ">{2}tutaj\</a>. \</p> |
| OnlineAudioLinkText | \<p>Aby nasłuchać dźwięku związanego z {0} \<tym tematem,{1}kliknij href=" ">{2}tutaj\</a>. \</p> |
| Funkcji: | **Formant Zawartość nie zainstalowana** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania contentnotinstalled.htm |
| **Element** | **Wartość** |
| ContentNotInstalledTitle (Nieobrajanie zawartości) | Na komputerze nie znaleziono zawartości. |
| ContentNotInstalledDownloadContentText | \<p>Aby pobrać zawartość na \<komputer, a{0} {1} href=" ">\<kliknij kartę Zarządzaj /a>. \</p> |
| Tekst Nieininstalowany Tekst | \<p>Na komputerze nie jest zainstalowana żadna zawartość. Aby uzyskać pomoc dotyczącą instalacji lokalnej pomocy, skontaktuj się z administratorem. \</p> |
| Funkcji: | **Nie znaleziono formantu tematu** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania topicnotfound.htm |
| **Element** | **Wartość** |
| TopicNotFoundTitle (TopicNotFoundTitle) | Nie można odnaleźć żądanego tematu na komputerze. |
| TopicNotFoundViewOnlineText | \<p>Żądany temat nie został znaleziony na twoim komputerze, ale \<możesz a href="{0}" {1}>wyświetlić temat online\</a>. \</p> |
| TopicNotFoundDownloadContentText | \<p>Zobacz okienko nawigacji, aby uzyskać \<łącza do{0}podobnych {1} tematów, lub href=" ">kliknij kartę\<Zarządzaj /a>, aby pobrać zawartość na komputer. \</p> |
| TopicNotFoundText (TopicNotFoundText) | \<p>W żądanym temacie nie znaleziono na twoim komputerze. \</p> |
| Funkcji: | **Sterowanie uszkodzonym tematem** |
| Używać: | Elementy tekstowe (ciągi) używane do renderowania topiccorrupted.htm |
| **Element** | **Wartość** |
| TopicCorruptedTitle (Napisy tematyczne) | Nie można wyświetlić żądanego tematu. |
| TopicCorruptedViewOnlineText | \<p>Help Viewer nie może wyświetlić żądanego tematu. Może wystąpić błąd w treści tematu lub podstawowej zależności systemu. \</p> |
| Funkcji: | **Kontrolka strony głównej** |
| Używać: | Tekst obsługujący wyświetlanie zawartości węzła najwyższego poziomu Podglądu pomocy. |
| **Element** | **Wartość** |
| Strona głównaTitle | Strona główna przeglądarki Pomocy |
| Strona głównaIntrodukcja | \<p>Witamy w przeglądarce Pomocy Firmy Microsoft, która jest podstawowym źródłem informacji dla wszystkich osób korzystających z narzędzi, produktów, technologii i usług firmy Microsoft. Podgląd pomocy daje dostęp do informacji in jak i referencyjnych, przykładowego kodu, artykułów technicznych i innych. Aby znaleźć potrzebną zawartość, przejrzyj spis treści, użyj wyszukiwania pełnotekstowego lub przejdź do zawartości za pomocą indeksu słów kluczowych. \</p> |
| Strona głównaContentInstallText | \<p>\<br />Użyj karty \<href="{0} {1} ">Zarządzaj\<zawartością /a>, aby\<wykonać następujące czynności: ul>\<li>Dodaj zawartość do komputera. \</li>\<li>Sprawdź dostępność aktualizacji zawartości lokalnej. \</li>\<li>Usuń zawartość z komputera. \</li>\</ul>\</p> |
| Strona głównaZainstalowane książki | Zainstalowane książki |
| Strona głównaNoBooksZainstalowany | Na komputerze nie znaleziono zawartości. |
| Strona głównaPomowanie | Ustawienia zawartości Pomocy |
| Strona głównaHelpSettingsText | \<p>Bieżące ustawienie to pomoc lokalna. Podgląd pomocy wyświetla zawartość zainstalowaną na komputerze. \<br />Aby zmienić źródło zawartości Pomocy, na pasku \<menu programu{0}Visual Studio wybierz opcję span\<style=" ">Help, Set Help Preference /span>. \<br />\</p> |
| Megabajt | MB |

**branding.js**

Plik branding.js zawiera język JavaScript używany przez elementy znakowania programu Visual Studio Help Viewer.  Poniżej znajduje się lista elementów marki i obsługujących funkcji JavaScript.  Wszystkie ciągi, które mają być zlokalizowane dla tego pliku są zdefiniowane w sekcji "Localizable Strings" w górnej części tego pliku.  Plik ICL został utworzony dla ciągów loc w pliku branding.js.

||||
|-|-|-|
|**Funkcja znakowania**|**Funkcja JavaScript**|**Opis**|
|Var...||Definiowanie zmiennych|
|Pobierz język kodu użytkownika|setUserPreferenceLang|mapuje indeks # na język kodu|
|Ustawianie i ponajmuj wartości plików cookie|getCookie, setCookie||
|Dziedziczony element członkowski|changeMembersLabel|Rozwijanie/zwijanie dziedziczonego elementu członkowskiego|
|Kiedy SelfBranded = False|Onload|Przeczytaj ciąg zapytania, aby sprawdzić, czy jest to żądanie drukowania.  Ustaw wszystkie kody, aby skupić się na karcie preferowanej przez użytkownika.  Jeśli jest to żądanie drukowania, a następnie ustawić jestPrinterFriendly do true. Sprawdź, czy w trybie wysokiego kontrastu nie ma trybu wysokiego kontrastu.|
|Fragment kodu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Zmień przytażal||
||setCodesnippetLang||
||zestawObszewając||
||Płyta copytoclipboard||
|SkładanyObsza|zestaw dodawaniadocollapsibleControlSet|zapisz cały zwijany obiekt kontrolny na liście.|
||CA_Click|w oparciu o stan zwijanego obszaru, określa, który obraz i tekst|
|Obsługa kontrastu logo|isBlackBackground()|Wywoływany, aby ustalić, czy tło jest czarne.  Tylko dokładne, gdy w trybie wysokiego kontrastu.|
||isHighContrast()|użyj kolorowego zakresu, aby wykryć tryb wysokiego kontrastu|
||onHighContrast(czarny)|Wywoływana po wykryciu wysokiego kontrastu|
|Funkcjonalność LST|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funkcja MultiMedia|caption(begin, end, text, style)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSekundy(t)||
||getAllComments(węzeł)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||napisy(id)||

**PLIKI HTM**

Pakiet znakowania zawiera zestaw plików HTM, które obsługują scenariusze przekazywania kluczowych informacji użytkownikom zawartości, na przykład stronę główną zawierającą sekcję opisującą zainstalowane zestawy zawartości i strony informujące użytkownika, gdy nie można znaleźć tematów w lokalnym zestawie tematów. Te pliki HTM mogą być modyfikowane na produkt.  Dostawcy powłoki ISO są w stanie wziąć domyślny pakiet znakowania i zmienić zachowanie i zawartość tych stron, aby uwzględnić ich potrzeby.  Pliki te odnoszą się do ich odpowiedniego pakietu znakowania w celu tagów znakowania, aby uzyskać odpowiednią zawartość z pliku branding.xml.

||||
|-|-|-|
|**Plik**|**Użycie**|**Wyświetlane źródło zawartości**|
|strona główna.htm|Jest to strona, która wyświetla aktualnie zainstalowaną zawartość i wszelkie inne wiadomości odpowiednie do przedstawienia użytkownikowi o ich zawartości.  Ten plik ma dodatkowy atrybut meta data "Microsoft.Help.Id" content="-1", który umieszcza tę zawartość w górnej części lokalnego toc zawartości.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<tag HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<tag Strona głównaIntrodukcja>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<tag Strona głównaContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Sekcja nagłówka Tag Branding.xml\<HomePageInstalledBooks>, dane \<generowane z aplikacji, Strona GłównaNoBooksZainstalowany>, gdy nie są zainstalowane książki.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Sekcja nagłówka Tag brandingu.xml \<HomePageHelpSettings \<>, tekst sekcji Strona głównaPomocowanie tekstu>.|
|topiccorrupted.htm|Jeśli temat istnieje w zestawie lokalnym, ale z jakiegoś powodu nie można wyświetlić (uszkodzona zawartość).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Jeśli temat nie zostanie znaleziony w lokalnym zestawie zawartości ani nie jest dostępny w trybie online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<tag TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<tag TopicNotFoundViewOnlineText> \<+ TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<tag TopicNotFoundText>|
|contentnotinstalled.htm|Jeśli dla produktu nie zainstalowano zawartości lokalnej.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<tag ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<tag ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<tag ContentNotInstalledText>|

**Pliki CSS**

Pakiet znakowania programu Visual Studio Help Viewer zawiera dwa pliki css do obsługi spójnej prezentacji zawartości Pomocy programu Visual Studio:

- Branding.css - zawiera elementy css do renderowania gdzie SelfBranded = false

- Printer.css - zawiera elementy css do renderowania gdzie SelfBranded = false

Pliki branding.css zawierają definicje prezentacji tematu programu Visual Studio (zastrzeżenie jest takie,\<że plik branding.css zawarty w Branding_ ustawień regionalnych>.mshc z usługi pakietów może ulec zmianie).

**Pliki graficzne**

Zawartość programu Visual Studio wyświetla logo programu Visual Studio, a także inne grafiki.  Pełna lista plików graficznych w pakiecie znakowania programu Visual Studio Help Viewer jest przedstawiona poniżej.

||||
|-|-|-|
|**Plik**|**Użycie**|**Przykłady**|
|clear.gif (wyjętego z|Służy do renderowania obszaru składanego||
|footer_slice.gif|Prezentacja stopki||
|info_icon.gif|Używane podczas wyświetlania informacji|Disclaimer|
|online_icon.gif|Ta ikona ma być powiązana z linkami online||
|tabLeftBD.gif|Służy do renderowania kontenera fragmentu kodu||
|tabRightBD.gif|Służy do renderowania kontenera fragmentu kodu||
|vs_logo_bk.gif|Używane do odniesień do logo normalnego kontrastu \<zgodnie z definicją w tagu Branding.xml LogoFileName>.  W przypadku produktów programu Visual Studio nazwa logo to vs_logo_bk.gif.||
|vs_logo_wh.gif|Używane do normalnych odniesień do logo wysokiego, zgodnie z definicją w tagu \<Branding.xml LogoFileNameHC>.  W przypadku produktów programu Visual Studio nazwa logo to vs_logo_wh.gif.||
|ccOff.png|Grafika podpisów||
|ccOn.png|Grafika podpisów||
|ImageSprite.png|Służy do renderowania obszaru składanego|grafika rozwinięta lub zwijanie|

## <a name="deploy-a-set-of-topics"></a>Wdrażanie zestawu tematów

Jest to prosty i szybki samouczek do tworzenia zestawu wdrażania zawartości programu Help Viewer składającego się z pliku MSHA i zestawu kabin lub kontrolerów MSHC zawierających te tematy. MSHA to plik XML opisujący zestaw kabin lub plików MSHC. Podgląd pomocy może odczytać MSHA, aby uzyskać listę zawartości (. CAB lub . MSHC) dostępne do instalacji lokalnej.

Jest to tylko podkład opisujący bardzo podstawowy schemat XML dla MSHA Podglądu pomocy.  Istnieje przykład implementacji poniżej tego krótkiego przeglądu i przykładu HelpContentSetup.msha.

Nazwa MSHA, na potrzeby tego podkładu, to HelpContentSetup.msha (nazwa pliku może być wszystkim, z rozszerzeniem . MSHA). HelpContentSetup.msha (przykład poniżej) powinien zawierać listę dostępnych kabin lub MSHC.  Typ pliku musi być spójny w ramach MSHA (nie obsługuje kombinacji typów plików MSHA i CAB). Dla każdej kabiny lub MSHC \<powinna istnieć klasa div="pakiet">... \</div> (patrz przykład poniżej).

Uwaga: w poniższym przykładzie implementacji uwzględniliśmy pakiet znakowania. Jest to niezbędne do uwzględnienia w celu uzyskania potrzebnych elementów renderowania zawartości programu Visual Studio i zachowań zawartości.

Przykładowy plik HelpContentSetup.msha: (Zamień nazwy plików "nazwa zestawu zawartości 1" i "nazwa zestawu zawartości 2" itp.)

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

1. Tworzenie folderu lokalnego w stylu "C:\SampleContent"

2. W tym przykładzie użyjemy plików MSHC, aby zawierać tematy.  MSHC to zip z rozszerzeniem pliku zmienionym z .zip na . MSHC.

3. Utwórz poniższy Plik HelpContentSetup.msha jako plik tekstowy (notatnik został użyty do utworzenia pliku) i zapisz go w wyżej opisanym folderze (patrz krok 1).

Klasa "Branding" istnieje i jest wyjątkowa. Branding mshc jest zawarty w tym podkład, dzięki czemu zainstalowana zawartość będzie miała znakowanie, a zachowania zawartości zawarte w MSHC będą miały odpowiednie elementy wsparcia zawarte w pakiecie znakowania. Bez tego błędy będą skutkować, gdy system szuka elementów pomocy technicznej, które nie są częścią zgranej (zainstalowanej) zawartości.

Aby uzyskać pakiet znakowania programu Visual Studio, skopiuj plik Branding_en-US.mshc w pliku C:\Program Files (x86)\Microsoft Help Viewer\v2.3\ do folderu roboczego.

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

Korzystanie i rozszerzanie powyższych kroków umożliwi vsps wdrożyć swoje zestawy zawartości dla Programu Visual Studio Help Viewer.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Dodawanie pomocy do powłoki programu Visual Studio (zintegrowane i odizolowane)

**Wprowadzenie**

W tym przewodniku pokazano, jak włączyć zawartość Pomocy do aplikacji powłoki programu Visual Studio, a następnie wdrożyć ją.

**Wymagania**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Izolowana powłoka Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Omówienie**

Powłoka [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] jest wersją [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE, na której można oprzeć aplikację. Takie aplikacje zawierają izolowane powłoki wraz z rozszerzeniami, które można utworzyć. Użyj szablonów projektu izolowanej powłoki, które są zawarte w zestawie [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, do tworzenia rozszerzeń.

Podstawowe kroki tworzenia aplikacji opartej na izolowanej skorupie i jej Pomocy:

1. Uzyskaj [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] redystrybucj iso shell (pobieranie microsoft).

2. W programie Visual Studio utwórz rozszerzenie Pomocy, które jest oparte na izolowanej powłoki, na przykład rozszerzenie Pomocy Contoso, które jest opisane w dalszej części tego przewodnika.

3. Zawiń rozszerzenie i powłoki ISO redystrybucji do wdrożenia MSI (konfiguracja aplikacji). Niniejsza instruktaż nie zawiera kroku konfiguracji.

Tworzenie magazynu zawartości programu Visual Studio. W scenariuszu powłoki zintegrowanej zmień program Visual Studio12 na nazwę katalogu produktów w następujący sposób:

- Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Katalogi\VisualStudio15.

- Utwórz plik o nazwie CatalogType.xml i dodaj go do folderu. Plik powinien zawierać następujące wiersze kodu:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Zdefiniuj magazyn zawartości w rejestrze. W przypadku powłoki zintegrowanej zmień visualstudio15 na nazwę katalogu produktów:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogi\VisualStudio15

   Klucz: Wartość ciągu ścieżki lokalizacji: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Katalogi\VisualStudio15\en-US

   Klucz: Nazwa ciągu catalogname wartość: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentacja

**Tworzenie projektu**

Aby utworzyć rozszerzenie izolowanej powłoki:

1. W programie Visual Studio w obszarze **Plik**wybierz pozycję **Nowy projekt**w obszarze **Inne typy projektów** wybierz pozycję **Rozszerzalność**, a następnie wybierz pozycję **Izolowana powłoka programu Visual Studio**. Nazwij `ContosoHelpShell`projekt ), aby utworzyć projekt rozszerzalności na podstawie szablonu powłoki izolowanej programu Visual Studio.

2. W Eksploratorze rozwiązań w projekcie ContosoHelpShellUI w folderze Pliki zasobów otwórz plik ApplicationCommands.vsct. Upewnij się, że ta linia jest komentowana (wyszukaj "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Wybierz klawisz F5 do skompilowania i uruchom **debugowanie**. W eksperymentalnym wystąpieniu ide izolowanej powłoki wybierz menu **Pomoc.** Upewnij się, że są wyświetlane polecenia **Wyświetl Pomoc**, Dodaj i Usuń **zawartość Pomocy**i **Ustaw preferencje Pomocy.**

4. W Eksploratorze rozwiązań w projekcie ContosHelpShell w folderze Dostosowywanie powłoki otwórz plik ContosoHelpShell.pkgdef. Aby zdefiniować katalog Pomocy Contoso, dodaj następujące wiersze:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. W Eksploratorze rozwiązań w projekcie ContosHelpShell w folderze Dostosowywanie powłoki otwórz plik ContosoHelpShell.Application.pkgdef. Aby włączyć Pomoc F1, dodaj następujące wiersze:

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

6. W Eksploratorze rozwiązań w menu kontekstowym rozwiązania ContosoHelpShell wybierz pozycję menu **Właściwości.** W obszarze **Właściwości konfiguracji**wybierz pozycję **Menedżer konfiguracji**. W **konfiguracji** kolumny zmień każdą wartość "Debug" na "Release".

7. Skompiluj rozwiązanie. Spowoduje to utworzenie zestawu plików w folderze wydania, który będzie używany w następnej sekcji.

Aby przetestować to tak, jakby wdrożony:

1. Na komputerze, na który wdrażasz program Contoso, zainstaluj pobraną (z góry) powłokę ISO.

2. Utwórz folder \\w folderze \Program\\Files (x86) i nadaj jego `Contoso`nazwę .

3. Skopiuj zawartość z folderu wydania \\ContosoHelpShell do folderu \Program Files (x86)\Contoso\.

4. Uruchom Edytor rejestru, wybierając **polecenie Uruchom** `Regedit`w menu **Start** i wprowadzając . W edytorze rejestru wybierz pozycję **Plik**, a następnie **pozycję Importuj**. Przejdź do folderu projektu ContosoHelpShell. W podfolderze ContosoHelpShell wybierz contosoHelpShell.reg.

5. Tworzenie magazynu zawartości:

    Dla powłoki ISO — utwórz magazyn zawartości Contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

    W [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] przypadku powłoki zintegrowanej utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Utwórz plik CatalogType.xml i dodaj go do magazynu zawartości (poprzedni krok) zawierającego:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Dodaj następujące klucze rejestru:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath String value:

    Dla powłoki ISO:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Zintegrowana powłoka:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Klucz: Nazwa ciągu catalogname wartość: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentacja. W przypadku powłoki ISO jest to nazwa katalogu.

8. Skopiuj zawartość (kabiny lub MSHC i MSHA) do folderu lokalnego.

9. Przykład wiersza polecenia Zintegrowana powłoka do testowania magazynu zawartości. W przypadku powłoki ISO zmień katalog i uruchamianieWartości aplikacji odpowiednio, aby dopasować go do produktu.

     "C:\Program Files (x86)\Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery method="page&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Uruchom aplikację Contoso (z katalogu głównego aplikacji Contoso). W shellu ISO wybierz pozycję menu **Pomoc** i zmień **preferencje Ustawiania Pomocy** na **Pomoc lokalną**.

11. W obrębie powłoki wybierz pozycję menu **Pomoc,** a następnie **pozycję Wyświetl Pomoc**. Lokalna przeglądarka Pomocy powinna zostać uruchomiona. Wybierz kartę **Zarządzanie zawartością.** W obszarze **Źródło instalacji**wybierz przycisk opcji **Dysk.** Wybierz przycisk **...** i przejdź do folderu lokalnego zawierającego zawartość Contoso (skopiowanego do folderu lokalnego w powyższym kroku). Wybierz pomocKontentSetup.msha. Contoso powinien teraz pojawiać się jako książka w wybranych książkach. Wybierz **pozycję Dodaj**, a następnie wybierz przycisk **Aktualizuj** (prawy dolny róg).

12. W ramach contoso IDE wybierz klawisz F1, aby przetestować funkcje F1.

## <a name="additional-resources"></a>Zasoby dodatkowe

Aby zapoznać się z interfejsem API środowiska wykonawczego, zobacz [Interfejs API Pomocy systemu Windows](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Aby uzyskać więcej informacji na temat sposobu wykorzystania interfejsu API Pomocy, zobacz [przykłady kodów Podglądu pomocy](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Sugestie dotyczące funkcji można przesyłać w [witrynie Społeczność deweloperów](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
