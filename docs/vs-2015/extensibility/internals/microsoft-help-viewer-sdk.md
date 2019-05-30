---
title: Zestaw SDK podglądu pomocy firmy Microsoft | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 226762ef355a83a2539fa1402a4369398f9f52a4
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263153"
---
# <a name="microsoft-help-viewer-sdk"></a>Zestaw SDK Podglądu Pomocy firmy Microsoft
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten artykuł zawiera następujące zadania integratorzy Visual Studio podglądu pomocy:

- Tworzenie tematu (Obsługa F1)

- Tworzenie pakietu zawartości, znakowania podglądu pomocy

- Wdrażanie zestawu artykułów

- Dodawanie Pomocy Visual Studio shell (integrated lub isolated)

- Dodatkowe zasoby

### <a name="creating-a-topic-f1-support"></a>Tworzenie tematu (Obsługa F1)
 Ta sekcja zawiera omówienie składników prezentowane tematu, temat wymagania, krótki opis sposobu tworzenia tematu (w tym wymagania w zakresie obsługi F1), a na końcu tematu na jej wynik renderowany.

 **Omówienie tematu podglądu pomocy**

 Wywołanego tematu do renderowania w Podglądzie pomocy pobiera znakowania elementy pakietu, które są skojarzone z tematu w czasie instalacji lub ich ostatniej aktualizacji wraz z tematu XHTML i łączy dwa spowodować prezentowane widok zawartości (znakowanie danych + dane tematu).  Pakiet ze znakowaniem zawiera logo, obsługa zachowania zawartości i tekst znakowania (prawa autorskie, itp.).  Aby uzyskać więcej informacji dotyczących znakowaniu elementów pakietu, zobacz "Tworzenie znakowania pakiet" poniżej.  W przypadku, gdy nie ma żadnych pakietów znakowania związanych z tematem, w Podglądzie pomocy będzie używać rezerwowej oznaczonego pakietu znajduje się w katalogu głównym aplikacji Help Viewer (Branding_en US.mshc).

 **Wymagania temat Podglądu pomocy**

 Mógł być renderowany prawidłowo w Podglądzie pomocy pierwotne tematu zawartość musi być podstawowy XHTML 1.1 W3C.

 Temat zwykle zawiera dwie sekcje:

- Metadane (zobacz odwołanie do metadanych zawartości): dane dotyczące tematu, na przykład, unikatowego Identyfikatora tematu, wartość — słowo kluczowe, identyfikator spisu treści, tematu nadrzędny identyfikator węzła, itp.

- Zawartość treści: zgodne z podstawowych XHTML 1.1 W3C, która obejmuje obsługiwane zachowania zawartości (zwijany obszaru, fragment kodu itp. Pełną listę znajdują się poniżej).

  Znakowanie pakiet rozszerzeń Visual Studio obsługiwane kontrolki:

- Łącza

- CodeSnippet

- CollapsibleArea

- Dziedziczonego elementu członkowskiego

- LanguageSpecificText

  Obsługiwanych ciągów języka (bez uwzględniania wielkości liter):

- javascript

- CSharp lub c#

- cplusplus or visualc++ or c++

- Język JScript

- języka Visual Basic lub VB.

- f # lub języka fsharp lub fs

- drugi — ciąg reprezentujący nazwę języka

  **Tworzenie tematu w Podglądzie pomocy**

  Tworzenie nowego dokumentu XHTML o nazwie ContosoTopic4.htm i dołączyć tytuł tag (poniżej).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 Następnie dodaj dane, aby zdefiniować sposób jak temat jest przedstawiane (własne ani nie), aby odwołać się w tym temacie F1, w której istnieje w tym temacie w spisie treści, jego identyfikator (w przypadku odwołania do linku przez inne tematy), itp.  Zobacz tabelę "Metadane zawartości" poniżej, aby uzyskać pełną listę obsługiwanych metadanych.

- W tym przypadku użyjemy naszego znakowania pakietu wariant oznaczonego pakietu Visual Studio podglądu pomocy.

- Dodaj F1 meta nazwę i wartość ("Microsoft.Help.F1" zawartość = "ContosoTopic4"), będą zgodne podana wartość F1 w zbiorze właściwości środowiska IDE.  (Zobacz sekcji pomocy F1, aby uzyskać więcej informacji).   Jest to wartość, która pasuje do F1 wywoływać z poziomu środowiska IDE, aby wyświetlić ten temat, po wybraniu F1 w środowisku IDE.

- Dodaj identyfikator tematu. Jest to ciąg, który jest używany przez innych tematów, aby utworzyć łącze do tego tematu.  Jest to identyfikator podglądu pomocy, w tym temacie.

- W przypadku spisu treści należy dodać węzła nadrzędnego w tym temacie do definiowania, gdzie pojawią się tego węzła spisu treści tematu.

- Spis treści można dodać w kolejności węzła w tym temacie. Gdy węzeł nadrzędny ma n liczbę węzłów podrzędnych, zgodnie z kolejnością węzły podrzędne definiują lokalizacji w tym temacie. Adapterem, w tym temacie jest numer 4 4 tematy podrzędne.)

  Przykład sekcji metadanych:

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

 Treść (nie w tym nagłówku i stopce) tematu będzie zawierać łączy strony, sekcji Uwaga, zwijany obszaru, fragment kodu i fragment tekstu określonego języka.  Zobacz sekcję znakowania, aby uzyskać informacje dotyczące tych obszarów prezentowane tematu.

1. Dodaj znacznik tytułu tematu:  `<div class="title">Contoso Topic 4</div>`

2. Dodaj sekcję Uwaga: `<div class="alert"> add your table tag and text </div>`

3. Dodawanie obszaru zwijana:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Dodaj fragment kodu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Dodaj kod języka określonego tekstu:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Należy pamiętać, że devLangnu = umożliwia wprowadzenie innych języków. Na przykład devLangnu = "Fortran" spowoduje wyświetlenie Fortran po fragmencie kodu DisplayLanguage = Fortran

6. Dodawanie łączy strony: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Uwaga: dla nieobsługiwanych nowe "Język" (przykład F#, Cobol, Pascal) kolorowania kodu we fragmencie kodu jest monochromatyczny.

 **Temat Podglądu pomocy przykład** kod ilustruje sposób definiowania metadanych, fragment kodu, obszar zwijany i język określony tekst.

```
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
<li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li>
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
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>

```

 **Obsługa F1**

 W programie Visual Studio wybierając F1 generuje wartości dostarczone z położenia kursora w środowisku IDE i wypełnienie klasy "zbiór właściwości" przy użyciu podanej wartości (oparte na lokalizacji kursora. Gdy kursor znajduje się za pośrednictwem funkcji x, funkcja x jest aktywny/w fokus i wypełnia zbiór właściwości z wartościami.  Po wybraniu F1 jest wypełniana zbiór właściwości, jak i Visual Studio F1 kod sprawdza, czy klienci domyślne źródło pomocy lokalnej lub w trybie online (online jest wartość domyślna), następnie tworzy odpowiedni ciąg na podstawie użytkowników, ustawiając (online to wartość domyślna) — wykonanie powłoki (zobacz pomoc administratora przewodnika dotyczącego exe Uruchom parametrów) z parametrami Podgląd pomocy lokalnej + słowa kluczowe ze zbioru właściwości, jeśli pomocy lokalnej jest domyślny lub adres URL MSDN za pomocą słowa kluczowego na liście parametrów.

 Jeśli nie zostały zwrócone trzy ciągi F1, określonych jako ciąg wielowartościowych potrwać pierwszy termin Szukaj trafień, i jeśli znaleziono, gotowe; Jeśli nie, należy przejść do następnego ciągu.  Kolejność ma znaczenie. Przedstawienie słowa kluczowe wielowartościowych powinno być najdłuższy ciąg najkrótszej ciąg.  Aby to sprawdzić, w przypadku wielu wartościach słów kluczowych, Przyjrzyj się online ciągu adresu URL F1, który będzie zawierać wybrany — słowo kluczowe.

 W programie Visual Studio 2012 celowo wprowadziliśmy silniejsze dzielenia między online i offline, więc, że jeśli ustawienia użytkownika dla usługi Online, następnie możemy po prostu przekazywane żądania F1 bezpośrednio do naszej usługi online zapytania MSDN, zamiast routingu za pomocą agenta biblioteki Pomocy czy mieliśmy w programie Visual Studio 2010. Następnie Polegamy na stan "zainstalowano zawartość dostawcy = true" do ustalenia, czy należy zrobić coś inaczej w tym kontekście. W przypadku opcji true następnie wykonamy tę logikę analizy i routingu, w zależności od tego, co chcesz obsługiwać dla swoich klientów. W przypadku wartości FAŁSZ następnie możemy po prostu przejdź do sieci MSDN. Jeśli ustawienia użytkownika lokalnego, wszystkie wywołania przejdź do aparatu pomocy lokalnej.

 F1 Diagram przepływu:

 ![Przepływ F1](../../extensibility/internals/media/f1flow.png "F1flow")

 Gdy Podgląd pomocy domyślne źródło zawartości pomocy jest równa online (uruchamianie w przeglądarce):

- Funkcje programu Visual Studio Partner (VSP) Dodaj wartość do zbioru właściwości F1 (prefix.keyword zbiór właściwości oraz online adres URL dla prefiksu znaleziony w rejestrze): F1 wysyła adres URL pliku VSP + parametrów w przeglądarce.

- Funkcje programu Visual Studio (Edytor języka, elementy określonego menu programu Visual Studio, itp.):  F1 wysyła Visual Studio adresu URL w przeglądarce.

  Gdy Podgląd pomocy domyślne źródło zawartości pomocy jest równa pomocy lokalnej (Uruchom w Podglądzie pomocy):

- VSP funkcji, jeśli słowo kluczowe są takie same między F1 zbiór właściwości, a indeksu magazynu lokalnego (czyli prefix.keyword zbioru właściwości = wartość znajdującą się w indeksie magazynu lokalnego):  F1 powoduje wyświetlenie tematu w Podglądzie pomocy.

- Funkcje programu Visual Studio (bez opcji VSP zastąpić zbioru właściwości emitowane przez funkcje programu Visual Studio): F1 powoduje wyświetlenie tematu w Podglądzie Pomocy programu Visual Studio.

  Ustaw następujące wartości rejestru, aby włączyć F1 rezerwowych dla zawartości pomocy dostawcy. Rezerwowe F1 oznacza, że w Podglądzie pomocy jest równa szukać pomocy F1 zawartości online i zawartości dostawcy jest instalowana lokalnie na dysku twardym użytkowników. Podgląd pomocy powinna wyglądać przy pomocy lokalnej na zawartość, nawet jeśli ustawienie domyślne to pomocy online.

1. Ustaw **VendorContent** pomocy 2.1 z klucza rejestru:

   - Dla 32-bitowych systemach operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

   - Dla 64-bitowych systemach operacyjnych:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = dword: 00000001

2. Zarejestruj się przestrzeń nazw partnera w kluczu rejestru pomocy 2.1:

   - Dla 32-bitowych systemach operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.1\Partner<em>\\<namespace\></em>

      "Lokalizacja"="offline"

   - Dla 64-bitowych systemach operacyjnych:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em>\\<namespace\></em>

      "Lokalizacja"="offline"

   **Podstawowa analiza kodu natywnego Namespace**

   Aby włączyć w podstawowej przestrzeni nazw natywnych, analizy, w rejestrze Dodaj nową wartość typu DWORD o nazwie: BaseNativeNamespaces i ustawić jej wartość na 1 (klucz katalogu, który chce obsługiwać).  Na przykład jeśli chcesz używać katalogu programu Visual Studio, można dodać klucza do ścieżki:

   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Gdy F1 — słowo kluczowe w formacie, który występuje nagłówek/metody, znak "/", zostanie przetworzona, wynikiem konstrukcji następujące:

- Nagłówek: będzie przestrzeni nazw, który może służyć do zarejestrowania w rejestrze

- Metoda: będzie to słowo kluczowe, które zostanie przekazane.

  Na przykład, biorąc pod uwagę niestandardową biblioteką o nazwie CustomLibrary i metodę o nazwie MyTestMethod, gdy F1 żądanie pochodzi w nim będą formatowane jako `CustomLibrary/MyTestMethod`.

  Użytkownik może następnie zarejestruj CustomLibrary jako przestrzeni nazw, w ramach gałęzi partnerów i podaj klucz niezależnie od lokalizacji, potrzebna jest i słów kluczowych, przekazana do zapytania będą MyTestMethod.

  **Włączanie pomocy narzędzia w środowisku IDE debugowania**

  Dodaj następujący klucz rejestru i wartości:

  HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\Dynamic Help key: Wyświetlanie danych wyjściowych debugowania w sprzedaży detalicznej wartości: TAK

  W środowisku IDE, w menu Pomoc wybierz pozycję "Debuguj kontekst pomocy"

  **Metadane zawartości**

  W poniższej tabeli dowolny ciąg, który pojawia się między nawiasami jest symbolem zastępczym, które muszą zostać zastąpione rozpoznawaną wartością. Na przykład w \<meta name="Microsoft.Help.Locale" zawartość = "[kod języka]" / >, "[kod języka]" musi zostać zastąpiona wartością taką jak "en-us".

|Właściwości (reprezentacja HTML)|Opis|
|--------------------------------------|-----------------|
|\< meta name="Microsoft.Help.Locale" content="[language-code]" />|Ustawia ustawienia regionalne w tym temacie. Jeśli ten tag jest używany w temacie, należy go używać tylko raz i muszą zostać wstawione powyżej innych tagów Microsoft Help. Jeśli ten tag nie jest używany, treść tego tematu jest indeksowana przy użyciu modułu dzielenia wyrazów, który jest skojarzony z ustawienia regionalne produktu, jeśli jest określona; w przeciwnym razie en-us jest używany moduł dzielenia wyrazów. Ten tag jest zgodna z ISOC RFC 4646. Aby upewnić się, że Microsoft Help działa prawidłowo, należy użyć tej właściwości zamiast ogólnego atrybut Language.|
|\< meta name="Microsoft.Help.TopicLocale" content="[language-code]" />|Ustawia ustawienia regionalne w tym temacie, gdy są używane również innych ustawień regionalnych. Jeśli ten tag jest używany w temacie, należy można użyć tylko raz. Użyj tego znacznika, jeśli katalog zawiera zawartość w więcej niż jednym języku. Wiele tematów w katalogu mogą mieć tego samego Identyfikatora, ale każdy należy określić unikatowy TopicLocale. Temat, który określa TopicLocale, zgodnym z ustawieniami regionalnymi wykazu jest temat, który jest wyświetlany w spisie treści. Jednak wszystkich wersji językowych tematu są wyświetlane w wynikach wyszukiwania.|
|\< tytuł > [Title] \< /title >|Określa tytuł w tym temacie. Ten tag jest wymagany i może być używane tylko raz w temacie. Jeśli treść tego tematu nie zawiera tytuł \<div > sekcji, ten tytuł jest wyświetlany w tym temacie oraz w spisie treści.|
|\< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/>|Określa tekst łącza, które będą wyświetlane w okienku indeksu podglądu pomocy. Po kliknięciu łącza, zostanie on wyświetlony. Można określić wiele indeksu słów kluczowych, tematu lub ten znacznik można pominąć, jeśli nie chcesz, aby łącza do tego tematu, aby pojawiają się w indeksie. Słowa kluczowe "K", z wcześniejszych wersji Pomocy mogą być konwertowane do tej właściwości.|
|\< meta name="Microsoft.Help.Id" content="[TopicID]"/>|Ustawia identyfikator dla tego tematu. Ten tag jest wymagany i może być używane tylko raz w temacie. Identyfikator musi być unikatowa wśród tematów w katalogu, które mają tych samych ustawień regionalnych. W innym temacie może utworzyć łącze do tego tematu przy użyciu tego identyfikatora.|
|\< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/>|Określa słów kluczowych F1 w tym temacie. Można określić wiele kluczowych F1 dla tematu lub ten znacznik można pominąć, jeśli nie chcesz, aby w tym temacie, która będzie wyświetlana po użytkownik aplikacji naciśnie klawisz F1. Zwykle tylko jeden słów kluczowych F1 określono dla tematu. Słowa kluczowe "F", z wcześniejszych wersji Pomocy mogą być konwertowane do tej właściwości.|
|\< meta-name = "Description" content = "[opis tematu]" / >|Zawiera krótkie podsumowanie dotyczące zawartości w tym temacie. Jeśli ten tag jest używany w temacie, należy można użyć tylko raz. Ta właściwość jest dostępny bezpośrednio przez bibliotekę zapytań; nie są przechowywane w pliku indeksu.|
 meta name="Microsoft.Help.TocParent" content="[parent_Id]"/>|Określa temacie nadrzędnym względem tego tematu w spisie treści. Ten tag jest wymagany i może być używane tylko raz w temacie. Wartość jest Microsoft.Help.Id elementu nadrzędnego. Temat może mieć tylko jedną lokalizację w tabeli treści. "-1" jest traktowany jako identyfikator tematu dla głównego spisu treści. W [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)], że strona jest strona główna podglądu pomocy. Jest to z tego samego powodu, które możemy dodać specjalnie TocParent =-1 do niektóre tematy, aby upewnić się, że są one wyświetlane u góry poziomu. Strona główna podglądu pomocy jest stroną systemu i dlatego niewymienne. Jeśli VSP próbuje dodać stronę o identyfikatorze-1, mogą uzyskać dodawane do zestawu zawartości, ale podglądu pomocy, zawsze będzie korzystać na stronie system — strona główna podglądu pomocy|
|\< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/>|Określa, gdzie w spisie treści w tym temacie jest wyświetlana względem jego elementów równorzędnych tematów. Ten tag jest wymagany i może być używane tylko raz w temacie. Wartość jest liczbą całkowitą. Temat, który określa całkowitoliczbowy niższej wartości pojawia się powyżej temat, który określa całkowitoliczbowy wyższa wartość.|
|\< meta name="Microsoft.Help.Product" content="[product code]"/>|Określa produktu, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, należy można użyć tylko raz. Te informacje można również podać jako parametr, który jest przekazywany do indeksowania pomocy.|
|\< meta name="Microsoft.Help.ProductVersion" content="[version number]"/>|Określa wersję produktu, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, należy można użyć tylko raz. Te informacje można również podać jako parametr, który jest przekazywany do indeksowania pomocy.|
|\< meta name="Microsoft.Help.Category" content="[string]"/>|Używane przez produkty do identyfikowania podsekcje zawartości. Można określić wiele podsekcje, tematu lub ten znacznik można pominąć, jeśli nie chcesz, aby linki, aby zidentyfikować wszystkie podsekcje. Ten tag jest używany do przechowywania atrybutów TargetOS i TargetFrameworkMoniker po przekonwertowaniu tematu z wcześniejszej wersji Pomocy. Format zawartości jest AttributeName:AttributeValue.|
|\< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/>|Określa tą wersją tego tematu, gdy istnieje wiele wersji, w wykazie. Ponieważ Microsoft.Help.Id nie musi być unikatowa, ten tag jest wymagany, gdy więcej niż jedna wersja tematu istnieje w katalogu, na przykład, gdy wykaz zawiera temat dla programu .NET Framework 3.5 i temat dla programu .NET Framework 4 i mają ten sam Micro słabe. Help.Id.|
|\< meta name="SelfBranded" content="[TRUE or FALSE]"/>|Określa, czy w tym temacie używany pakiet znakowania uruchamiania Help Library Manager lub znakowania pakietu, które są specyficzne dla tematu. Ten tag musi mieć wartość PRAWDA lub FAŁSZ. Jeśli wartość TRUE, a następnie znakowania pakiet dla skojarzonego tematu zastępuje znakowania pakiet, który jest ustawiony, po uruchomieniu Help Library Manager, tak aby tematu jest renderowana zgodnie z oczekiwaniami, nawet jeśli różni się od renderowania zawartości innego. Jeśli jest to wartość FALSE, bieżącego tematu jest renderowana zgodnie z znakowania pakiet, który jest ustawiony, po uruchomieniu Help Library Manager. Domyślnie Help Library Manager zakłada własnym znakowania mieć wartość false, chyba że SelfBranded zmienna jest zadeklarowana jako PRAWDA. w związku z tym, nie trzeba deklarować \<meta-name = "SelfBranded" content = "FALSE" / >.|

### <a name="creating-a-branding-package"></a>Tworzenie pakietu znakowania
 Wersję programu Visual Studio obejmuje szereg różnych produktów Visual Studio, w tym izolowany i zintegrowane powłoki dla partnerów Visual Studio.  Każda z tych produktów wymaga pewien stopień oparte na temat zawartości pomocy znakowania pomocy technicznej, unikatowe dla produktu.  Na przykład tematów programu Visual Studio musi być prezentacji marki spójne SQL Studio, który otacza powłoki ISO, wymaga swój własny unikatowy pomocy zawartości znakowanie dla każdego tematu.  Zintegrowanych partnerów Shell może być ich tematy pomocy mieścić się w nadrzędnej zawartości pomocy produktu Visual Studio przy zachowaniu ich własnych znakowania tematu.

 Pakiety znakowania są instalowane przez produkt zawierający podglądu pomocy.  W przypadku produktów Visual Studio:

- Bazowy pakiet znakowania (Branding_\<ustawień regionalnych > .mshc) jest zainstalowana w katalogu głównym aplikacji Help Viewer 2.1 (przykład: \Microsoft Help Viewer\v2.1 pliki (x86) C:\Program) przez pakiet językowy podglądu pomocy.  Jest ono używane w przypadkach, w których nie zainstalowano produkt znakowania pakietów (Brak zawartości został zainstalowany) lub gdzie zainstalowany pakiet znakowania są uszkodzone.  Elementy programu Visual Studio (logo i opinie) są ignorowane, gdy główny rezerwowego znakowania pakietu aplikacji jest używany.

- Po zainstalowaniu usługi zawartości pakietu zawartości programu Visual Studio znakowania pakietów jest również instalowany (w przypadku pierwszego scenariusza instalacji zawartości czasu).  W przypadku aktualizacji do znakowania pakietów, aktualizacja jest zainstalowana podczas następnej aktualizacji zawartości lub Akcja instalacji dodatkowego pakietu.

  Podgląd Pomocy firmy Microsoft obsługuje znakowania tematy, na podstawie metadanych tematu.

- Gdzie temat metadane definiuje samodzielnie marki = true, tematu, ponieważ renderować, nic nie rób (o ile to znakowania).

- Gdzie temat metadane definiuje samodzielnie marki = false, za pomocą pakietu znakowania skojarzone z wartością metadanych TopicVendor.

- Gdzie temat metadane definiuje name="Microsoft.Help.TopicVendor" zawartość =\< znakowania nazwę pakietu dostawcy MSHA >, za pomocą pakietu znakowania zdefiniowane w wartość zawartości.

- W ramach katalogu programu Visual Studio ma priorytet stosowania znakowania pakietów.  Stosowany jest znakowania pierwszy domyślne programu Visual Studio, a następnie, jeśli zdefiniowane w metadanych tematu i obsługiwane przez skojarzony znakowania pakietów (zgodnie z definicją w msha instalacji), zdefiniowane przez dostawcę znakowania są stosowane jako przesłonięcie.

  Elementy znakowania zazwyczaj można podzielić na trzy główne kategorie:

- Elementy nagłówka (przykłady link opinii, tekst warunkowego zastrzeżenie, logo)

- Zawartość zachowania (przykłady obejmują rozwijanie/zwijanie kontrolki tekstu elementy i elementy fragment kodu)

- Stopka elementów (np. prawa autorskie)

  Elementy uznawany za elementy marki obejmują (szczegółowo opisane w tej specyfikacji):

- Logo katalogu/produktu (Visual Studio np.)

- Elementy link i wysyłania wiadomości e-mail opinii

- Tekst klauzuli wyłączenia odpowiedzialności

- Tekst praw autorskich

  Pliki obsługi w pakiecie znakowania Pomoc usługi Visual Studio obejmują:

- Grafika (logo, ikon itp.)

- Branding.js — pliki pomocnicze zachowania zawartości skryptu

- Branding.XML — ciągów, które są stale używane w całym zawartości katalogu.  Uwaga: elementy tekstowe lokalizacji programu Visual Studio w branding.xml, obejmują _locID = "\<unikatową wartość >"

- Branding.css — definicji stylów w celu zachowania spójności prezentacji

- Printing.css — definicje styl spójne drukowania prezentacji

  Jak wspomniano powyżej, znakowania pakiety są skojarzone z tematem:

- Gdy SelfBranded = false jest zdefiniowany w metadanych, temat dziedziczy katalogu znakowania pakietów

- Lub kiedy SelfBranded = false i jest unikatowy pakiet znakowania zdefiniowanych w MSHA i dostępne, gdy zawartość jest zainstalowany

  Dla VSPs Implementowanie niestandardowych znakowania pakietów (VSP zawartości, SelfBranded = True), jest jednym ze sposobów, aby kontynuować rozpoczęcie rezerwowego oznaczonego pakietu (zainstalowany w programie Podgląd pomocy), a następnie zmień nazwę pliku, zgodnie z potrzebami.  Branding_\<ustawień regionalnych > .mshc plik jest plikiem zip z rozszerzeniem pliku zmieniony na .mshc, więc po prostu Zmień rozszerzenie z .mshc na zip i wyodrębnić zawartość.  Poniżej znajduje się pakiet elementy znakowania i zmodyfikuj odpowiednio (na przykład zmiana logo VSP logo i odwołania do logo w pliku Branding.xml, zaktualizuj Branding.xml na charakterystyce VSP itp.).

  Gdy wszystkie modyfikacje są wykonywane, Utwórz plik zip zawierający żądaną elementy znakowania i zmień rozszerzenie na .mshc.

  Aby skojarzyć oznaczonego niestandardowego pakietu, należy utworzyć MSHA, który zawiera odwołanie do znakowania plików mshc wraz z zawartością mshc, (zawierający tematów).  Poniżej przedstawiono "MSHA" sposób tworzenia podstawowego MSHA.

  Plik Branding.xml zawiera elementy listy, używany do renderowania spójnie określonych elementów w jednym z tematów, jeśli zawiera temat \<meta name="Microsoft.Help.SelfBranded" zawartość = "false" / >.  Visual Studio listę elementów w pliku Branding.xml znajduje się poniżej.  Ta lista jest przeznaczona do użycia jako szablon dla wdrażający platformę powłoki ISO, w którym mogą modyfikować te elementy (na przykład logo, opinie i prawach autorskich), aby spełnić swoje własne znakowania produktu wymaga.

  Uwaga: Zmienne oznaczone przez "{n}" ma zależności w kodzie — usuwanie lub zmiana tych wartości spowoduje, że błędy i ewentualnie awarii aplikacji. Identyfikatory lokalizacji (przykład _locID="codesnippet.n") są objęte znakowania pakiet rozszerzeń Visual Studio.

  **Branding.xml**

|||
|-|-|
|Funkcja:|**CollapsibleArea**|
|Użycie:|Rozwiń zwija formantu zawartości tekstu|
|**Element**|**Wartość**|
|ExpandText|Expand|
|CollapseText|Zwiń|
|Funkcja:|**CodeSnippet**|
|Użycie:|Tekst kontrolki fragmentu kodu.  Uwaga: Zawartości fragmentu kodu przy użyciu miejsca "Bez podziału" zostanie zmieniony na miejsce.|
|**Element**|**Wartość**|
|CopyToClipboard|Kopiuj do schowka|
|ViewColorizedText|Wyświetl w trybie kolorowym|
|CombinedVBTabDisplayLanguage|Visual Basic (przykład)|
|VBDeclaration|Deklaracja|
|VBUsage|Użycie|
|Funkcja:|**Opinie, stopki i Logo**|
|Użycie:|Zapewniają kontrolę opinii dla klienta przekazać opinię na temat bieżącego, za pośrednictwem poczty e-mail.  Tekst o prawach autorskich dla zawartości.  Definicja logo.|
|**Element**|**Wartość (te parametry można modyfikować, aby sprostać wymaganiom zawartości nabywcy.)**|
|CopyRight|© 2013 Microsoft Corporation. Wszelkie prawa zastrzeżone.|
|SendFeedback|\<href = "{0}" {1}> Wyślij opinię\</a > na ten temat do firmy Microsoft.|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|
|Funkcja:|**Zrzeczenie odpowiedzialności**|
|Użycie:|Zestaw przypadków określonych się zastrzeżeniami do wymagań maszyny translacji zawartości.|
|**Element**|**Wartość**|
|MT_Editable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|MT_NonEditable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|MT_QualityEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|MT_QualityNonEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|MT_BetaContents|Ten artykuł został przetłumaczony maszynowo dla wydania wstępnego. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|MT_BetaRecycledContents|Ten artykuł został przetłumaczony ręcznie dla wydania wstępnego. Jeśli masz połączenie z Internetem, wybierz "Wyświetl ten temat online", aby wyświetlić tą stronę w trybie edycji razem z oryginalnej zawartości w języku angielskim jednocześnie.|
|Funkcja:|**LinkTable**|
|Użycie:|Obsługa linków w temacie online|
|**Element**|**Wartość**|
|LinkTableTitle|Tabela łączy|
|TopicEnuLinkText|Pokaż angielską wersję\</a > w tym temacie, który jest dostępny na tym komputerze.|
|TopicOnlineLinkText|Wyświetl ten temat \<href = "{0}" {1}> online\</a >|
|OnlineText|Tryb online|
|Funkcja:|**Kontrolki dźwięku wideo**|
|Użycie:|Wyświetlanie elementów i tekst dla zawartości wideo|
|**Element**|**Wartość**|
|MultiMediaNotSupported|Internet Explorer 9 i instalacji do obsługi {0} zawartości.|
|VideoText|Wyświetlanie obrazu wideo|
|Audiotekst|strumieniowe przesyłanie audio|
|OnlineVideoLinkText|\<p > Aby wyświetlić wideo, związane z tym tematem, kliknij {0} \<href = "{1}" >{2}tutaj\</a >.\< /p >|
|OnlineAudioLinkText|\<p > Aby wysłuchać nagrań audio, związanych z bieżącym tematem, kliknij przycisk {0} \<href = "{1}" >{2}tutaj\</a >.\< /p >|
|Funkcja:|**Formant zawartości nie jest zainstalowany**|
|Użycie:|Elementy tekstowe (parametry) używany do renderowania contentnotinstalled.htm|
|**Element**|**Wartość**|
|ContentNotInstalledTitle|Nie znaleziono zawartości na komputerze.|
|ContentNotInstalledDownloadContentText|\<p > Aby pobrać zawartość na komputerze z systemem \<href = "{0}" {1}> klikając kartę Zarządzaj\</a >.\< /p >|
|ContentNotInstalledText|\<p > Brak zainstalowanej zawartości na komputerze. Skontaktuj się z administratorem dla instalacji lokalnej zawartości pomocy. \</p >|
|Funkcja:|**Kontrolki nie można odnaleźć tematu**|
|Użycie:|Elementy tekstowe (parametry) używany do renderowania topicnotfound.htm|
|**Element**|**Wartość**|
|TopicNotFoundTitle|Nie można odnaleźć żądanego tematu na komputerze.|
|TopicNotFoundViewOnlineText|\<p > nie można odnaleźć żądanego tematu na komputerze, ale możesz \<href = "{0}" {1}> przeglądać temat online\</a >.\< /p >|
|TopicNotFoundDownloadContentText|\<p > odnośniki do podobnych tematów w panelu nawigacji lub \<href = "{0}" {1}> klikając kartę Zarządzaj\</a > Aby pobrać zawartość na komputerze.\< /p >|
|TopicNotFoundText|\<p > nie można odnaleźć żądanego tematu na komputerze. \</p >|
|Funkcja:|**Temat uszkodzony kontroli**|
|Użycie:|Elementy tekstowe (parametry) używany do renderowania topiccorrupted.htm|
|**Element**|**Wartość**|
|TopicCorruptedTitle|Nie można wyświetlić żądanego tematu.|
|TopicCorruptedViewOnlineText|\<p > Podgląd pomocy nie może wyświetlić żądanego tematu. Może to być błąd w zawartości tematu lub podstawowej zależności systemu. \</p >|
|Funkcja:|**Kontrolki strony głównej**|
|Użycie:|Tekst, który obsługuje wyświetlanie zawartości węzeł najwyższego poziomu podglądu pomocy.|
|**Element**|**Wartość**|
|HomePageTitle|Strona główna podglądu pomocy|
|HomePageIntroduction|\<p > Witamy w Podglądzie pomocy firmy Microsoft, kluczowego źródła informacji dla wszystkich osób korzystających z narzędzi, produktów, technologii i usług firmy Microsoft. Podgląd Pomocy umożliwia dostęp do instrukcje i informacje, przykładowego kodu, artykuły techniczne i inne. Aby znaleźć zawartość, należy przejrzeć spis treści, użyć wyszukiwania pełnotekstowego oraz nawigowanie po zawartości przy użyciu indeksu — słowo kluczowe. \</p >|
|HomePageContentInstallText|\<p >\<br / > Użyj \<href = "{0}" {1}> Zarządzaj zawartością\</a > kartę, aby wykonać następujące czynności:\<ul >\<li > dodać zawartość do komputera.\< /li >\<li > sprawdzić aktualizacje zawartości lokalnej.\< /li >\<li > usunąć zawartość z komputera.\< /li >\</ul >\</p >|
|HomePageInstalledBooks|Zainstalowane książki|
|HomePageNoBooksInstalled|Nie znaleziono zawartości na komputerze.|
|HomePageHelpSettings|Ustawienia zawartości pomocy|
|HomePageHelpSettingsText|\<p > Twoje bieżące ustawienie to pomocy lokalnej. Podgląd Pomocy wyświetla zawartość, który jest zainstalowany na komputerze. \<br / > Aby zmienić źródło zawartości pomocy, na pasku menu programu Visual Studio wybierz \<span style = "{0}" > Pomoc, ustaw preferencje pomocy\</span >.\< br / >\</p >|
|MB|MB|

 **branding.js**

 Plik branding.js zawiera JavaScript używany przez elementy znakowania programu Visual Studio podglądu pomocy.  Poniżej znajduje się lista elementów znakowania i pomocnicze funkcji JavaScript.  Wszystkie ciągi, które mają zostać zlokalizowane dla tego pliku są definiowane w sekcji "Możliwych do zlokalizowania ciągi" na początku tego pliku.  Lokalizacja ciągów w pliku branding.js ICL pliku w utworzeniu.

||||
|-|-|-|
|**Funkcja oznaczania marką**|**Funkcja języka JavaScript**|**Opis**|
|Var...||Definiowanie zmiennych|
|Pobierz język kodu użytkownika|setUserPreferenceLang|Indeks mapuje # do języka kodu|
|Ustawianie i pobieranie wartości plików cookie|getCookie, setCookie||
|Dziedziczonego elementu członkowskiego|changeMembersLabel|Rozwiń/Zwiń dziedziczonego elementu członkowskiego|
|When SelfBranded=False|onLoad|Odczytaj ciąg zapytania, aby sprawdzić, czy jest to żądanie wydruku.  Ustaw wszystkie codesnippets, aby skoncentrować się na karcie preferowanych użytkownika.  Jeśli jest to żądanie wydruku, ustaw isPrinterFriendly na wartość true. Sprawdź, czy trybu wysokiego kontrastu.|
|Fragment kodu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|zapis wszystkich obiektów kontroli zwijany do listy.|
||CA_Click|na podstawie stanu zwijanej przestrzeni, definiuje, które obraz i tekst, aby przedstawić|
|Kontrast obsługę Logo|isBlackBackground()|Wywoływane w celu określenia, czy czarnym tle.  Tylko dokładne przypadku w trybie dużego kontrastu.|
||isHighContrast()|Użyj zakresu kolorowy, aby wykryć trybu wysokiego kontrastu|
||onHighContrast(black)|Wywołuje się po wykryciu o wysokim kontraście|
|Funkcje dzieł|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|Funkcje multimedialne|podpis (rozpoczęcia, zakończenia, tekst, stylu)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||styleRectify (nazwa_stylu, styleValue)||
||showCC(id)||
||subtitle(ID)||

 **PLIKI HTM**

 Pakiet ze znakowaniem zawiera zbiór plików HTM, które obsługują scenariusze komunikacji informacje o kluczu użytkownikom zawartości pomocy, na przykład strony głównej, który zawiera sekcja zawierająca opis, który konfiguruje zawartości są zainstalowane i stron, informujący użytkownika, gdy tematy nie można znaleźć w lokalnym zbiór tematów. Te pliki HTM można modyfikować dla każdego produktu.  Dostawców ISO powłoki będą mogli pobrać domyślnego pakietu znakowania i zmianę zachowania i zawartość tych stron do zestawu swoich potrzeb.  Pliki te odnoszą się do ich odpowiednich pakietów znakowania, w kolejności dla znakowania tagów, aby pobrać odpowiadająca jej zawartość z pliku branding.xml.

||||
|-|-|-|
|**Plik**|**Korzystanie**|**Wyświetlane źródła zawartości**|
|homepage.htm|Jest to strona, wyświetlająca aktualnie zainstalowaną zawartość i wszystkie inne komunikaty odpowiednie do zaprezentowania użytkownikowi o ich zawartości.  Ten plik zawiera dodatkowe meta danych atrybutu "Microsoft.Help.Id" zawartość = "-1" który umieszcza to zawartości w górnej części lokalnej zawartości spisu treści.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.XML, tag \<HomePageTitle >|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.XML, tag \<HomePageIntroduction >|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.XML, tag \<HomePageContentInstallText >|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Nagłówek sekcji Branding.xml tag\<HomePageInstalledBooks >, danych generowanych na podstawie aplikacji, \<HomePageNoBooksInstalled > gdy nie książek są zainstalowane.|
||<HOME_PAGE_SETTINGS_SECTION_ADD />|Nagłówek sekcji Branding.xml tag \<HomePageHelpSettings >, sekcja tekstu \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Gdy tematu istnieje w zestawie lokalnego, ale dla jakiegoś powodu nie można wyświetlić (uszkodzony zawartości).||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, tag \<TopicCorruptedTitle >|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.XML, tag \<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|Gdy tematu nie znajduje się w lokalnej zawartości ustawione ani dostępna online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.XML, tag \<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.XML, tag \<TopicNotFoundText >|
|contentnotinstalled.htm|Gdy brak zawartości lokalnej zainstalowany dla produktu.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.XML, tag \<ContentNotInstalledTitle >|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.XML, tag \<ContentNotInstalledDownloadContentText >|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.XML, tag \<ContentNotInstalledText >|

 **Pliki CSS**

 Pomoc przeglądarki znakowania pakiet rozszerzeń Visual Studio zawiera dwa pliki css do obsługi spójne prezentacji zawartości Pomocy programu Visual Studio:

- Branding.css — zawiera elementy css do renderowania gdzie SelfBranded = false

- Printer.css — zawiera elementy css do renderowania gdzie SelfBranded = false

  Pliki Branding.css zawiera definicje dla programu Visual Studio tematu prezentacji (zastrzeżenie: to, że branding.css zawarte w Branding_\<ustawień regionalnych > .mshc usługi pakietu mogą ulec zmianie).

  **Pliki graficzne**

  Zawartość usługi Visual Studio Wyświetla logo programu Visual Studio, a także innych grafik.  Poniżej przedstawiono pełną listę plików graficznych w pakiecie znakowania programu Visual Studio podglądu pomocy.

||||
|-|-|-|
|**Plik**|**Korzystanie**|**Przykłady**|
|Clear.GIF|Używany do renderowania obszaru zwijany||
|footer_slice.GIF|Prezentacja stopki||
|info_icon.gif|Używany podczas wyświetlania informacji|Zrzeczenie odpowiedzialności|
|online_icon.gif|Ta ikona jest ma zostać skojarzony z linków online||
|tabLeftBD.gif|Używany do renderowania kontenera fragmentu kodu||
|tabRightBD.gif|Używany do renderowania kontenera fragmentu kodu||
|vs_logo_bk.gif|Służąca do odwołania logo normalne kontrast, zgodnie z definicją w tagu Branding.xml \<LogoFileName >.  W przypadku produktów Visual Studio Nazwa logo jest vs_logo_bk.gif.||
|vs_logo_wh.gif|Służąca do odwołania normalne logo wysoka, zgodnie z definicją w tagu Branding.xml \<LogoFileNameHC >.  For Visual Studio products, logo name is vs_logo_wh.gif.||
|ccOff.png|Podpisy grafiki||
|ccOn.png|Podpisy grafiki||
|ImageSprite.png|Używany do renderowania obszaru zwijany|rozwijać i zwijać grafiki|

### <a name="deploying-a-set-of-topics"></a>Wdrażanie zbiór tematów
 Jest to prosty i szybki samouczek dotyczący tworzenia zestawu rozmieszczania zawartości podglądu pomocy, składająca się z plikiem MSHA i zestaw plików cab lub MSHCs zawierający tematów. MSHA jest plik XML, który opisuje zestaw plików cab lub MSHC plików. W Podglądzie pomocy można odczytać MSHA, aby uzyskać listę zawartości (. Plik CAB lub. Pliki MSHC) dostępną do zainstalowania.

 Jest to tylko podstawowe informacje opisujące wykraczającego poza podstawowe schematu XML dla MSHA podglądu pomocy.  Jest przykładem implementacji poniżej to krótkie omówienie i przykładowy HelpContentSetup.msha.

 Nazwa MSHA, dla celów tego poradnika jest HelpContentSetup.msha (nazwa pliku może być cokolwiek z rozszerzeniem. MSHA). HelpContentSetup.msha (przykład poniżej) powinna zawierać listę plików cab lub MSHCs dostępne.  Typ pliku musi być spójny MSHA (obsługuje kombinację typów plików MSHA i plików CAB). Dla każdego pliku CAB lub MSHC, powinien istnieć \<klasy div = "pakiet" >...  \< /div > (zobacz poniższy przykład).

 Uwaga: w poniższym przykładzie implementacji wprowadzono znakowania pakietów. Jest to niezbędne do uwzględnienia w celu uzyskania wymaganych elementów renderowania zawartości programu Visual Studio i zachowania zawartości.

 Sample HelpContentSetup.msha file: (Zastąp "content wartość 1. nazwa" i "zawartości, nazwę zestawu 2" itd. przy użyciu nazwy pliku.)

```
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

1. Utwórz folder lokalny, podobny do "C:\SampleContent"

2. W tym przykładzie użyjemy MSHC pliki zawierają tematy.  MSHC jest zip z rozszerzeniem pliku zmieniła się z rozszerzeniem .zip do. MSHC.

3. Utwórz poniżej HelpContentSetup.msha jako plik tekstowy (Notatnik został użyty do utworzenia pliku) i zapisz go w folderze wspomniano powyżej (zobacz krok 1).

   Klasa "Znakowania" istnieje i jest unikatowa. Mshc znakowania znajduje się w tym podstawowe informacje, dzięki czemu będzie mieć zainstalowaną zawartość, oznaczenia marką, a zachowania zawartości, które są zawarte w MSHCs będzie miał odpowiednią obsługę zawartym w pakiecie znakowania. Bez tego błędy powoduje, że gdy system wyszukuje elementy pomocy technicznej, które nie są częścią zgranych (zainstalowane) zawartości.

   Do uzyskania znakowania pakietów programu Visual Studio, skopiuj Branding_en US.mshc pliku C:\Program Files (x86) \Microsoft Help Viewer\v2.1\ do folderu roboczego.

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

 Używaniu i rozszerzaniu powyższych czynności umożliwi VSPs wdrożyć swoje zestawy zawartości dla programu Visual Studio podglądu pomocy.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Dodawanie pomocy do programu Visual Studio Shell (Integrated i Isolated)
 **Wprowadzenie**

 W tym instruktażu pokazano, jak dołączyć zawartości pomocy do aplikacji programu Visual Studio Shell, a następnie wdrożyć go.

 **Wymagania**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 Isolated Shell Redist](https://aka.ms/VS2013/IsoShell-LP/all)

   **Omówienie**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Powłoki jest wersją [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] IDE, w którym można oprzeć aplikacji. Takie aplikacje zawierają programu Isolated Shell wraz z rozszerzeń, które tworzysz. Użyj szablonów projektu Isolated Shell, które są zawarte w [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] zestawu SDK do kompilowania rozszerzeń.

   Podstawowe kroki tworzenia aplikacji Isolated Shell i jego pomocy:

3. Uzyskaj [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] pakiet redystrybucyjny powłoki ISO (do pobrania firmy Microsoft).

4. W programie Visual Studio Utwórz rozszerzenie pomocy, na podstawie programu Isolated Shell na przykład, rozszerzenie pomocy firmy Contoso, które jest opisane w dalszej części tego przewodnika.

5. Otoczenie rozszerzenie i powłoki ISO do dystrybucji, do wdrożenia MSI (Konfiguracja aplikacji). Ten przewodnik nie obejmuje kroku konfiguracji.

   Utwórz magazyn zawartości programu Visual Studio. W scenariuszu Integrated Shell Zmień Visual Studio12 nazwa katalogu produktów w następujący sposób:

- Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.

- Utwórz plik o nazwie CatalogType.xml i dodać go do folderu. Ten plik powinien zawierać następujące wiersze kodu:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Zdefiniuj magazynu zawartości w rejestrze. W przypadku Integrated Shell należy zmienić VisualStudio12 produktu nazwa katalogu:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Klucz: Wartość ciągu LocationPath: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   Klucz: Wartość ciągu CatalogName: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Dokumentacja

  **Tworzenie projektu**

  Aby utworzyć rozszerzenie Isolated Shell:

1. W programie Visual Studio w obszarze **pliku**, wybierz **nowy projekt**w obszarze **inne typy projektów** wybierz **rozszerzalności**, a następnie wybierz polecenie  **Program Visual Studio Shell izolowany**. Nadaj projektowi nazwę `ContosoHelpShell`) aby utworzyć projekt rozszerzenia na podstawie szablonu programu Visual Studio Isolated Shell.

2. W Eksploratorze rozwiązań Otwórz ApplicationCommands.vsct w projekcie ContosoHelpShellUI w folderze plików zasobów. Upewnij się, że ten wiersz jest ujęty w komentarz (wyszukaj frazę "No_Help"): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. Wybierz klawisz F5, aby skompilować i uruchomić **debugowania**. W doświadczalnym wystąpieniu izolowane środowisko IDE powłoki, wybierz **pomocy** menu. Upewnij się, że **Wyświetl Pomoc**, **Dodawanie i usuwanie zawartości Pomocy**, i **Ustaw preferencje pomocy** polecenia pojawiają się.

4. W Eksploratorze rozwiązań Otwórz ContosoHelpShell.pkgdef w projekcie ContosHelpShell w folderze dostosowania powłoki. Aby zdefiniować katalogu firmy Contoso pomocy, Dodaj następujące wiersze:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. W Eksploratorze rozwiązań Otwórz ContosoHelpShell.Application.pkgdef w projekcie ContosHelpShell w folderze dostosowania powłoki. Aby włączyć pomocy F1, Dodaj następujące wiersze:

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

6. W Eksploratorze rozwiązań w menu kontekstowym rozwiązania ContosoHelpShell wybierz **właściwości** elementu menu. W obszarze **właściwości konfiguracji**, wybierz opcję **programu Configuration Manager**. W **konfiguracji** kolumny, zmienić każda wartość "Debug" na "Wersja".

7. Skompiluj rozwiązanie. Spowoduje to utworzenie zestawu plików w folderze wersji, która będzie używana w następnej sekcji.

   Aby przetestować, tak, jakby wdrożona:

8. Na maszynie są wdrażane firmy Contoso, aby zainstalować pobrane powłoki ISO (które).

9. Utwórz folder w \\\Program Files (x86)\\i nadaj mu nazwę `Contoso`.

10. Skopiuj zawartość z folderu ContosoHelpShell wersji, aby \\\Contoso\ folder w bazie wiedzy \Program Files (x86).

11. Uruchom Edytor rejestru, wybierając **Uruchom** w **Start** menu i wprowadzając `Regedit`. W Edytorze rejestru wybierz **pliku**, a następnie **importu**. Przejdź do folderu projektu ContosoHelpShell. W podfolderze ContosoHelpShell wybierz ContosoHelpShell.reg.

12. Utwórz magazyn zawartości:

     Dla powłoki ISO - tworzenie Contoso magazynu zawartości C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     Aby uzyskać [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Integrated Shell, Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. Utwórz CatalogType.xml i dodać do magazynu zawartości (w poprzednim kroku), zawierający:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Dodaj następujące klucze rejestru:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: Wartość ciągu LocationPath:

     Dla powłoki ISO:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Integrated Shell:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     Klucz: Wartość ciągu CatalogName: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Dokumentacja. Dla powłoki ISO jest to nazwa katalogu.

15. Skopiuj zawartość (pliki cab lub MSHC i MSHA) do folderu lokalnego.

16. Przykład Integrated Shell wiersz polecenia dla testów magazynu zawartości. Dla powłoki ISO Zmień wartości katalogu i launchingApp zgodnie z potrzebami dopasować produktu.

      "C:\Program Files (x86)\Microsoft Help Viewer\v2.1\HlpViewer.exe" /catalogName VisualStudio12 /helpQuery method=”page&id=ContosoTopic0” /launchingApp Microsoft,VisualStudio,12.0

17. Uruchom aplikację Contoso (z katalogu głównego aplikacji Contoso). W powłoce ISO wybierz **pomocy** element menu, a następnie zmień **Ustaw preferencje pomocy** do **korzystanie z lokalnej pomocy**.

18. W powłoce, wybierz **pomocy** elementu menu, następnie **Wyświetl Pomoc**. Podgląd pomocy lokalnej powinien być uruchamiany. Wybierz **zarządzanie zawartością** kartę. W obszarze **źródło instalacji**, wybierz **dysku** przycisku opcji. Wybierz **...**  przycisk, a następnie przejdź do folderu lokalnego, zawierające zawartości firmy Contoso (skopiowany do folderu lokalnego w kroku powyżej). Wybierz HelpContentSetup.msha. Firmy Contoso powinien teraz wyświetlane jako książki w opcji książki. Wybierz **Dodaj**, a następnie wybierz **aktualizacji** przycisku (prawym dolnym rogu).

19. W środowisku IDE firmy Contoso wybierz klawisz F1, aby przetestować funkcje F1.

### <a name="additional-resources"></a>Dodatkowe zasoby

Dla interfejsu API środowiska uruchomieniowego, zobacz [interfejsu API Windows Help](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Aby uzyskać więcej informacji na temat jak korzystać z pomocy interfejsu API, zobacz [przykłady kodu dla podglądu pomocy](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e).

Aktualizacje na istotne problemy, zobacz [Readme podglądu pomocy](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409).