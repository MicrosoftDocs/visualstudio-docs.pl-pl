---
title: Zestaw SDK Podgląd Pomocy firmy Microsoft | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f7cbe9606b73741e1e59eb14f40cb277052944a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545083"
---
# <a name="microsoft-help-viewer-sdk"></a>Zestaw SDK Podglądu Pomocy firmy Microsoft
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ten artykuł zawiera następujące zadania dla integratorów podglądu pomocy programu Visual Studio:

- Tworzenie tematu (obsługa F1)

- Tworzenie pakietu znakowania zawartości podglądu pomocy

- Wdrażanie zestawu artykułów

- Dodawanie pomocy do programu Visual Studio Shell (zintegrowany lub izolowany)

- Dodatkowe zasoby

### <a name="creating-a-topic-f1-support"></a>Tworzenie tematu (obsługa F1)
 Ta sekcja zawiera omówienie składników przedstawianego tematu, wymagania dotyczące tematu, Krótki opis sposobu tworzenia tematu (w tym wymagania dotyczące obsługi F1), a wreszcie — przykładowy temat z renderowanym wynikiem.

 **Omówienie tematu pomocy**

 Gdy temat jest wywoływany do renderowania, podgląd pomocy Pobiera elementy pakietu znakowania, które są skojarzone z tematem w momencie instalacji lub ostatniej aktualizacji, wraz z tematem XHTML, i łączy te dwa w celu wyświetlenia wyświetlanego widoku zawartości (Znakowanie danych i danych tematu).  Pakiet znakowania zawiera logo, obsługę zachowań zawartości oraz tekst znakowania (Copyright itp.).  Aby uzyskać więcej informacji na temat elementów pakietu znakowania, zobacz "Tworzenie pakietu znakowania" poniżej.  W przypadku wystąpienia z tym tematem nie jest skojarzony żaden pakiet znakowania, podgląd pomocy użyje pakietu znakowania powrotu znajdującego się w katalogu głównym aplikacji podglądu pomocy (Branding_en-US. mshc).

 **Wymagania dotyczące tematu podglądu pomocy**

 Aby można było poprawnie renderować zawartość w podglądzie pomocy, nieprzetworzonym temacie musi być W3C Basic 1,1 XHTML.

 Temat zwykle zawiera dwie sekcje:

- Metadane (zobacz informacje o metadanych zawartości): dane dotyczące tematu, na przykład unikatowy identyfikator tematu, wartość słowa kluczowego, identyfikator spisu treści tematu, identyfikator węzła nadrzędnego itp.

- Zawartość treści: zgodna z W3C Basic 1,1 XHTML, która obejmuje obsługiwane zachowania zawartości (zwijane obszary, fragmenty kodu itp.). Pełna lista jest pokazana poniżej).

  Kontrolki obsługiwane przez pakiet znaków programu Visual Studio:

- Linki

- CodeSnippet

- CollapsibleArea

- Dziedziczony element członkowski

- LanguageSpecificText

  Obsługiwane ciągi języka (bez uwzględniania wielkości liter):

- javascript

- CSharp lub c #

- cplusplus lub VisualC + + lub c++

- JScript

- VisualBasic lub VB

- f # lub FSharp lub FS

- inne — ciąg, który reprezentuje nazwę języka

  **Tworzenie tematu podglądu pomocy**

  Utwórz nowy dokument XHTML o nazwie ContosoTopic4.htm i Dołącz tag tytułu (poniżej).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

 Następnie Dodaj dane, aby określić, w jaki sposób ma być prezentowany temat (z własnym oznaczeniem lub nie), jak odwoływać się do tego tematu dla F1, gdzie ten temat istnieje w spisie treści, jego identyfikator (do odwołania do łącza w innych tematach) itp.  Zapoznaj się z poniższą tabelą "metadane zawartości", aby zapoznać się z pełną listą obsługiwanych metadanych.

- W takim przypadku będziemy używać naszego pakietu markowego, czyli wariantu pakietu markowego podglądu pomocy programu Visual Studio.

- Dodaj nazwę meta F1 i wartość ("Microsoft. help. F1" Content = "ContosoTopic4"), która będzie zgodna z podaną wartością F1 w zbiorze właściwości IDE.  (Zobacz sekcję Obsługa F1, aby uzyskać więcej informacji).   Jest to wartość, która jest dopasowywana do wywołania F1 z poziomu IDE, aby wyświetlić ten temat w przypadku wybrania klawisza F1 w IDE.

- Dodaj identyfikator tematu. Jest to ciąg, który jest używany przez inne tematy do łączenia się z tym tematem.  Jest to identyfikator podglądu pomocy dla tego tematu.

- W przypadku spisu treści Dodaj węzeł nadrzędny tego tematu, aby określić, gdzie będzie widoczny ten węzeł spisu treści.

- W przypadku spisu treści Dodaj kolejność węzłów tego tematu. Gdy węzeł nadrzędny ma n numerów węzłów podrzędnych, Zdefiniuj w kolejności węzłów podrzędnych tej lokalizacji tematu. Na przykład ten temat ma numer 4 z 4 tematów podrzędnych.)

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

 Treść (bez nagłówka i stopki) tematu będzie zawierać linki do stron, sekcję notatki, obszar zwijany, fragment kodu i sekcję tekstu określonego dla języka.  Zapoznaj się z sekcją znakowanie, aby uzyskać informacje o tych obszarach prezentowanego tematu.

1. Dodaj tag tytułu tematu:  `<div class="title">Contoso Topic 4</div>`

2. Dodaj sekcję Uwagi: `<div class="alert"> add your table tag and text </div>`

3. Dodaj obszar zwijany:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Dodawanie fragmentu kodu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Dodaj tekst specyficzny dla języka kodu:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` należy pamiętać, że devLangnu = umożliwia wprowadzanie innych języków. Na przykład devLangnu = "Pascal" będzie wyświetlał Pascal, gdy fragment kodu DisplayLanguage = Pascal

6. Dodaj linki do stron: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Uwaga: w przypadku nieobsługiwanego nowego koloru "język wyświetlania" (przykład: F #, COBOL, Pascal) kolorowanie kodu w fragmencie kodu będzie monochromatyczne.

 **Przykład podglądu pomocy** Kod ilustruje sposób definiowania metadanych, fragmentu kodu, obszaru zwijanego i tekstu specyficznego dla języka.

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

 W programie Visual Studio wybranie klawisza F1 powoduje wygenerowanie wartości dostarczonych z położenia kursora w środowisku IDE i wypełnienie "zbiorem właściwości" wartościami podanymi (na podstawie lokalizacji kursora). Gdy kursor znajduje się nad funkcją x, funkcja x jest aktywna/w fokus i wypełnia zbiór właściwości wartościami.  Po wybraniu klawisza F1 zbiór właściwości jest wypełniany, a program Visual Studio F1 sprawdza, czy domyślne źródło pomocy dla klientów jest lokalne lub w trybie online (w trybie online jest to ustawienie domyślne), następnie tworzy odpowiedni ciąg w zależności od ustawienia użytkownika (wartość domyślna to online) — wykonanie powłoki (zobacz Podręcznik administratora pomocy dla parametrów uruchamiania programu exe) z parametrami dla lokalnego podglądu pomocy + słów kluczowych z zbioru właściwości, jeśli lokalna pomoc jest domyślna lub adres URL MSDN ze słowem kluczowym na liście parametrów.

 Jeśli trzy ciągi są zwracane dla F1, nazywanego ciągiem wielowartościowym, podejmij pierwszy termin, poszukaj trafień i jeśli zostanie on znaleziony, wszystko gotowe; w przeciwnym razie przejdź do następnego ciągu.  Zaporządkuj sprawy. Prezentacja wielowartościowych słów kluczowych powinna być najdłuższym ciągiem do najkrótszego ciągu.  Aby sprawdzić to w przypadku słów kluczowych wielowartościowych, spójrz na ciąg adresu URL F1 w trybie online, który będzie zawierać wybrane słowo kluczowe.

 W programie Visual Studio 2012 celowo nastąpiło silniejsze dzielenie między trybami online i offline, dzięki czemu w przypadku ustawienia użytkownika w trybie online po prostu przekazano żądanie F1 bezpośrednio do naszej usługi zapytań online w witrynie MSDN, a nie za pomocą usługi Routing przez agenta biblioteki pomocy, który miał w programie Visual Studio 2010. Następnie należy zastanowić się nad stanem "zainstalowano zawartość dostawcy = true" w celu określenia, czy wykonać coś innego w tym kontekście. Jeśli wartość jest równa true, to analiza i logika routingu są wykonywane w zależności od tego, co chcesz obsługiwać klientom. W przypadku wartości false po prostu przejdziemy do subskrypcji MSDN. Jeśli ustawienie użytkownika ma wartość lokalna, wszystkie wywołania przejdą do lokalnego aparatu pomocy.

 Diagram przepływu F1:

 ![Przepływ F1](../../extensibility/internals/media/f1flow.png "F1flow")

 Gdy domyślne źródło zawartości pomocy podglądu pomocy jest ustawione na online (Uruchom w przeglądarce):

- Funkcje programu Visual Studio partner (VSP) emitują wartość do zbioru właściwości F1 (prefiks zbioru właściwości. słowo kluczowe i adres URL online dla prefiksu znaleziony w rejestrze): F1 wysyła do przeglądarki parametry VSP + +.

- Funkcje programu Visual Studio (edytor języka, elementy menu specyficzne dla programu Visual Studio itp.): F1 wysyła do przeglądarki adres URL programu Visual Studio.

  Gdy domyślne źródło zawartości pomocy podglądu pomocy jest ustawione na lokalną pomoc (Uruchom w podglądzie pomocy):

- Funkcje VSP, w których słowo kluczowe pasuje między zbiorem właściwości F1 i indeksem magazynu lokalnego (czyli prefiksem zbioru właściwości. słowo kluczowe = wartość znaleziona w indeksie magazynu lokalnego): F1 renderuje temat w podglądzie pomocy.

- Funkcje programu Visual Studio (Brak opcji dla VSP, aby przesłonić zbiór właściwości emitowany z funkcji programu Visual Studio): F1 renderuje temat programu Visual Studio w podglądzie pomocy.

  Ustaw następujące wartości rejestru, aby włączyć rezerwę klawisza F1 dla zawartości pomocy dla dostawcy. Powrót do klawisza F1 oznacza, że podgląd pomocy jest ustawiony w celu wyszukania zawartości klawisza F1 w trybie online, a zawartość dostawcy jest instalowana lokalnie na dysku twardym użytkownika. Podgląd pomocy powinien przyjrzeć się lokalnej pomocy dotyczącej zawartości, mimo że ustawieniem domyślnym jest pomoc online.

1. Ustaw wartość **VendorContent** w kluczu rejestru Help 2,1:

   - W przypadku 32-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = DWORD: 00000001

   - W przypadku 64-bitowych systemów operacyjnych:

        HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

        "VendorContent" = DWORD: 00000001

2. Zarejestruj przestrzeń nazw partnera w kluczu rejestru Help 2,1:

   - W przypadku 32-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.1\Partner<em> \\<przestrzeni \> nazw</em>

      "lokalizacja" = "offline"

   - W przypadku 64-bitowych systemów operacyjnych:

      HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Partner<em> \\<przestrzeni \> nazw</em>

      "lokalizacja" = "offline"

   **Analiza podstawowej natywnej przestrzeni nazw**

   Aby włączyć analizę podstawowej przestrzeni nazw natywnych, w rejestrze Dodaj nową wartość DWORD o nazwie: BaseNativeNamespaces i ustaw ją na 1 (w kluczu katalogu, który ma zostać objęty pomocą techniczną).  Jeśli na przykład chcesz użyć wykazu programu Visual Studio, możesz dodać klucz do ścieżki:

   HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Gdy napotkasz słowo kluczowe F1 w NAGŁÓWKu lub METODzie formatu, znak "/" zostanie przeanalizowany, co spowoduje powstanie następującej konstrukcji:

- Nagłówek: będzie przestrzenią nazw, której można użyć do zarejestrowania w rejestrze

- Metoda: zostanie to słowo kluczowe, które zostanie przesłane przez.

  Na przykład dana Biblioteka niestandardowa o nazwie CustomLibrary i metoda o nazwie MyTestMethod, gdy żądanie F1 zostanie sformatowane jako `CustomLibrary/MyTestMethod` .

  Użytkownik może następnie zarejestrować CustomLibrary jako przestrzeń nazw w ramach Hive partnera i podać dowolny klucz lokalizacji, który życzy, a słowo kluczowe przesłane do zapytania będzie MyTestMethod.

  **Włącz narzędzie do debugowania pomocy w środowisku IDE**

  Dodaj następujący klucz rejestru i wartość:

  HKEY_CURRENT_USER klucz pomocy \Software\Microsoft\VisualStudio\12.0\Dynamic: Wyświetlaj dane wyjściowe debugowania w wartości handlowej: tak

  W IDE, w obszarze menu Pomoc wybierz pozycję "Debuguj kontekst pomocy"

  **Metadane zawartości**

  W poniższej tabeli każdy ciąg, który pojawia się między nawiasami jest symbolem zastępczym, który musi zostać zastąpiony przez rozpoznaną wartość. Na przykład, w \<meta name="Microsoft.Help.Locale" content="[language code]" /> , "kod języka]" musi zostać zastąpione przez wartość taką jak "en-us".

|Właściwość (reprezentacja HTML)|Opis|
|--------------------------------------|-----------------|
|\< meta name="Microsoft.Help.Locale" content="[language-code]" />|Ustawia ustawienia regionalne dla tego tematu. Jeśli ten tag jest używany w temacie, musi być używany tylko raz i musi być wstawiony powyżej wszelkich innych tagów pomocy firmy Microsoft. Jeśli ten tag nie jest używany, tekst treści tematu jest indeksowany przy użyciu funkcji dzielenia wyrazów, która jest skojarzona z ustawieniami regionalnymi produktu, jeśli jest określona; w przeciwnym razie jest używany łącznik pl-US Word. Ten tag jest zgodny z ISOC RFC 4646. Aby upewnić się, że pomoc firmy Microsoft działa prawidłowo, Użyj tej właściwości zamiast atrybutu języka ogólnego.|
|\< meta name="Microsoft.Help.TopicLocale" content="[language-code]" />|Ustawia ustawienia regionalne dla tego tematu, gdy są również używane inne ustawienia lokalne. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Ten tag jest używany, gdy katalog zawiera zawartość w więcej niż jednym języku. Wiele tematów w wykazie może mieć ten sam identyfikator, ale każdy z nich musi określać unikatowy TopicLocale. Temat, który określa TopicLocale, który odpowiada ustawieniom regionalnym wykazu, jest tematem, który jest wyświetlany w spisie treści. Jednak wszystkie wersje językowe tematu są wyświetlane w wynikach wyszukiwania.|
|\< title>Tytuły\</title>|Określa tytuł tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Jeśli treść tematu nie zawiera \<div> sekcji title, ten tytuł zostanie wyświetlony w temacie i w spisie treści.|
|\< meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/>|Określa tekst łącza, które jest wyświetlane w okienku indeks podglądu pomocy. Po kliknięciu linku jest wyświetlany temat. Można określić wiele słów kluczowych indeksu dla tematu lub pominąć ten tag, jeśli nie chcesz, aby linki do tego tematu pojawiły się w indeksie. Słowa kluczowe "K" z wcześniejszych wersji pomocy można przekonwertować na tę właściwość.|
|\< meta name="Microsoft.Help.Id" content="[TopicID]"/>|Ustawia identyfikator dla tego tematu. Ten tag jest wymagany i musi być używany tylko raz w temacie. Identyfikator musi być unikatowy wśród tematów w wykazie, które mają takie same ustawienia regionalne. W innym temacie można utworzyć link do tego tematu za pomocą tego identyfikatora.|
|\< meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/>|Określa słowo kluczowe F1 dla tego tematu. Możesz określić wiele słów kluczowych F1 dla tematu lub pominąć ten tag, jeśli nie chcesz, aby ten temat był wyświetlany, gdy użytkownik naciśnie klawisz F1. Zwykle dla tematu określono tylko jedno słowo kluczowe F1. Słowa kluczowe "F" z wcześniejszych wersji pomocy można przekonwertować na tę właściwość.|
|\< meta name="Description" content="[topic description]" />|Zawiera krótkie podsumowanie zawartości w tym temacie. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Ta właściwość jest dostępna bezpośrednio przez bibliotekę zapytań. nie jest on przechowywany w pliku indeksu.|
 meta Name = "Microsoft. help. TocParent" Content = "[parent_Id]"/>|Określa temat nadrzędny tego tematu w spisie treści. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest Microsoft.Help.Id elementu nadrzędnego. Temat może mieć tylko jedną lokalizację w spisie treści. wartość "-1" jest traktowana jako identyfikator tematu dla katalogu głównego spisu treści. Na stronie Strona [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] główna podglądu pomocy. Jest to taka sama przyczyna, w przypadku której w celu zagwarantowania, że są one wyświetlane na najwyższym poziomie, TocParent =-1. Strona główna podglądu pomocy jest stroną systemową i nie jest do ponownego przemieszczenia. Jeśli VSP próbuje dodać stronę o IDENTYFIKATORze-1, może ona zostać dodana do zestawu zawartości, ale podgląd pomocy zawsze będzie używać strony systemowej — Strona główna podglądu pomocy|
|\< meta name="Microsoft.Help.TocOrder" content="[positive integer]"/>|Określa, gdzie znajduje się w spisie treści, względem tematów dotyczących elementów równorzędnych. Ten tag jest wymagany i musi być używany tylko raz w temacie. Wartość jest liczbą całkowitą. Temat, który określa liczbę całkowitą o niższej wartości pojawia się powyżej tematu, który określa wartość całkowitą o wyższej wartości.|
|\< meta name="Microsoft.Help.Product" content="[product code]"/>|Określa produkt opisany w tym temacie. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Te informacje można również podać jako parametr przekazywany do indeksatora pomocy.|
|\< meta name="Microsoft.Help.ProductVersion" content="[version number]"/>|Określa wersję produktu, który opisano w tym temacie. Jeśli ten tag jest używany w temacie, musi być używany tylko raz. Te informacje można również podać jako parametr przekazywany do indeksatora pomocy.|
|\< meta name="Microsoft.Help.Category" content="[string]"/>|Używane przez produkty do identyfikowania podsekcji zawartości. Można zidentyfikować wiele podsekcji tematu lub pominąć ten tag, jeśli nie chcesz, aby linki identyfikować podsekcje. Ten tag jest używany do przechowywania atrybutów dla TargetOS i TargetFrameworkMoniker, gdy temat zostanie przekonwertowany ze starszej wersji pomocy. Format zawartości to AttributeName: atrybutu AttributeValue.|
|\< meta name="Microsoft.Help.TopicVersion content="[topic version number]"/>|Określa tę wersję tematu, gdy w wykazie istnieją różne wersje. Ponieważ Microsoft.Help.Id nie jest gwarancją unikatowości, ten tag jest wymagany, gdy więcej niż jedna wersja tematu istnieje w wykazie, na przykład gdy wykaz zawiera temat dla .NET Framework 3,5 i tematu dla .NET Framework 4 i oba mają ten sam Microsoft.Help.Id.|
|\< meta name="SelfBranded" content="[TRUE or FALSE]"/>|Określa, czy w tym temacie jest stosowany pakiet znakowania programu Help Library Manager lub pakiet znakowania charakterystyczny dla tematu. Ten tag musi mieć wartość TRUE lub FALSE. Jeśli wartość jest równa TRUE, pakiet oznakowania dla skojarzonego tematu przesłania pakiet oznakowania, który jest ustawiany podczas uruchamiania programu Help Library Manager, tak aby temat był renderowany jako zamierzony, nawet jeśli różni się od renderowania innej zawartości. Jeśli ma wartość FALSE, bieżący temat jest renderowany zgodnie z pakietem znakowania ustawionym podczas uruchamiania programu Help Library Manager. Domyślnie program Help Library Manager przyjmuje, że sama znakowanie ma wartość false, chyba że zmienna SelfBranded jest zadeklarowana jako TRUE; w związku z tym nie trzeba deklarować \<meta name="SelfBranded" content="FALSE"/> .|

### <a name="creating-a-branding-package"></a>Tworzenie pakietu znakowania
 Wersja programu Visual Studio obejmuje wiele różnych produktów Visual Studio, w tym izolowane i zintegrowane powłoki dla partnerów programu Visual Studio.  Każdy z tych produktów wymaga pewnego stopnia pomocy technicznej oznakowania treści pomocy, która jest unikatowa dla produktu.  Na przykład tematy programu Visual Studio muszą mieć spójną prezentację markową, natomiast program SQL Studio, który otacza powłokę ISO, wymaga własnej unikatowego znakowania zawartości pomocy dla każdego tematu.  Zintegrowany partner powłoki może chcieć, aby tematy pomocy były zawarte w zawartości pomocy produktu Visual Studio nadrzędnego przy zachowaniu własnych oznaczeń.

 Pakiety znakowania są instalowane przez produkt zawierający podgląd pomocy.  W przypadku produktów Visual Studio:

- Pakiet języka powrotu (Branding_ \<locale> . mshc) jest instalowany w katalogu głównym aplikacji 2,1 pomocy (przykład: C:\Program Files (x86) \Microsoft help Viewer\v2.1) przez pakiet językowy podglądu pomocy.  Ta wartość jest używana w przypadkach, gdy nie zainstalowano pakietu znakowania produktu (nie zainstalowano żadnej zawartości) lub jeśli zainstalowany pakiet znakowania jest uszkodzony.  Elementy programu Visual Studio (logo i opinie) są ignorowane, gdy jest używany pakiet znakowania powrotu aplikacji głównej.

- Gdy zawartość programu Visual Studio jest instalowana z usługi pakietu zawartości, instalowany jest również pakiet znakowania (na potrzeby scenariusza instalacji zawartości po raz pierwszy).  Jeśli jest dostępna aktualizacja pakietu znakowania, aktualizacja zostanie zainstalowana podczas działania następnej aktualizacji zawartości lub dodatkowej instalacji pakietu.

  Podgląd Pomocy firmy Microsoft obsługuje znakowanie tematów w oparciu o metadane tematu.

- Gdzie metadane tematu definiują funkcję samomarkd = true, renderowanie tematu w taki sposób, nic nie rób (o ile jest to znakowanie).

- Gdzie metadanych tematu definiuje opcję samomarkd = false, należy użyć pakietu znakowania skojarzonego z wartością metadanych TopicVendor.

- Gdzie Metadata tematu definiuje Name = "Microsoft. help. TopicVendor" Content = \< branding package name in vendor MSHA> , Użyj pakietu znakowania zdefiniowanego w wartości zawartości.

- W ramach wykazu programu Visual Studio istnieje priorytetowa aplikacja pakietów znakowania.  Pierwsze domyślne oznakowanie programu Visual Studio jest stosowane, a następnie, jeśli zostało zdefiniowane w metadanych tematu i obsługiwane przez skojarzony pakiet znakowania (zgodnie z definicją w MSHA instalacji), oznakowanie zdefiniowane przez dostawcę jest stosowane jako przesłonięcie.

  Elementy znakowania zazwyczaj należą do trzech głównych kategorii:

- Elementy nagłówka (przykłady: link do opinii, tekst warunkowego wykluczania, logo)

- Zachowania zawartości (przykłady obejmują elementy tekstu kontrolki Rozwiń/Zwiń i elementy fragmentu kodu)

- Elementy stopki (przykład Copyright)

  Elementy uznawane za elementy oznaczone marką obejmują (szczegółowo w tej specyfikacji):

- Katalog/logo produktu (przykład Visual Studio)

- Link opinii i elementy poczty e-mail

- Tekst odpowiedzialności

- Tekst Copyright

  Pliki pomocnicze w pakiecie znakowania podglądu pomocy programu Visual Studio obejmują:

- Grafika (logo, ikony itd.)

- Branding.js — pliki skryptów obsługujące zachowania zawartości

- Branding.xml — ciągi, które są często używane w całej zawartości katalogu.  Uwaga: w przypadku elementów tekstowych lokalizacji programu Visual Studio w branding.xml należy uwzględnić _locID = " \<unique value> "

- Znakowanie. css — definicje stylu na potrzeby spójności prezentacji

- Drukowanie. css — definicje stylów dla spójnej prezentacji drukowanej

  Jak wspomniano powyżej, pakiety znakowania są skojarzone z tematem:

- Gdy SelfBranded = false jest zdefiniowany w metadanych, temat dziedziczy pakiet znakowania katalogu

- Lub gdy SelfBranded = false i istnieje unikatowy pakiet znakowania, który jest zdefiniowany w MSHA i jest dostępny po zainstalowaniu zawartości

  W przypadku VSPs zaimplementowania niestandardowych pakietów znakowania (zawartość VSP, SelfBranded = true), jeden z metod, aby kontynuować, zaczyna się od pakietu znakowania powrotu (instalowany z podglądem pomocy) i zmienia nazwę pliku zgodnie z potrzebami.  Plik Branding_ \<locale> . mshc jest plikiem ZIP z rozszerzeniem pliku zmienionym na. mshc, więc po prostu zmień rozszerzenie z. mshc na. zip i Wyodrębnij zawartość.  Poniżej znajdują się elementy pakietu markowego i modyfikuje się zgodnie z potrzebami (na przykład Zmień logo na logo VSP i odwołanie do logo w pliku Branding.xml, zaktualizuj Branding.xml na specyficzne dla VSP, itp.).

  Po zakończeniu wszystkich modyfikacji Utwórz plik zip zawierający wymagane elementy znakowania i Zmień rozszerzenie na mshc.

  Aby skojarzyć niestandardowy pakiet znakowania, Utwórz MSHA, który zawiera odwołanie do pliku marking mshc wraz z mshc zawartości (zawierające tematy).  Aby uzyskać informacje na temat tworzenia podstawowego MSHA, zobacz poniżej "MSHA".

  Plik Branding.xml zawiera elementy listy używane do spójnego renderowania określonych elementów w temacie, gdy temat zawiera \<meta name="Microsoft.Help.SelfBranded" content="false"/> .  Poniżej znajduje się lista elementów programu Visual Studio, które znajdują się w pliku Branding.xml.  Ta lista jest przeznaczona do użycia jako szablon przyjętych elementów do pobrania powłoki ISO, gdzie modyfikują te elementy (na przykład logo, opinie i prawa autorskie) w celu spełnienia własnych potrzeb związanych z znakowaniem produktów.

  Uwaga: zmienne zapisane przez "{n}" mają zależności kodu — usunięcie lub zmiana tych wartości spowoduje błędy i ewentualne awarie aplikacji. Identyfikatory lokalizacji (przykład _locID = "codesnippet. n") są zawarte w pakiecie znakowania programu Visual Studio.

  **Branding.xml**

Funkcja: **CollapsibleArea** use: expand zwija tekst kontrolki zawartości

|**Element**|**Wartość**|
|-|-|
|ExpandText|Rozwiń|
|CollapseText|Zwiń|

Funkcja:**CodeSnippet** use: tekst kontrolki fragmentu kodu.  Uwaga: zawartość fragmentu kodu z rozrywanym miejscem zostanie zmieniona na spacja.

|**Element**|**Wartość**|
|-|-|
|CopyToClipboard|Kopiuj do schowka|
|ViewColorizedText|Wyświetl kolory|
|CombinedVBTabDisplayLanguage|Visual Basic (przykład)|
|VBDeclaration|Oświadczeń|
|VBUsage|Użycie|

Funkcja: **informacje zwrotne, stopka i logo** : Podaj kontrolę opinii dla klienta, aby przekazać opinię na temat bieżącego tematu za pośrednictwem poczty e-mail.  Tekst praw autorskich dla zawartości.  Definicja logo.

|**Element**|**Wartość (te ciągi mogą być modyfikowane w celu spełnienia wymagań dotyczących przyjmowanego przez zawartość).**|
|-|-|
|Prawo|© 2013 Microsoft Corporation. All rights reserved.|
|SendFeedback|\<a href="{0}" {1}>Prześlij opinię \</a> na temat tego tematu do firmy Microsoft.|
|FeedbackLink||
|LogoTitle|[!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]|
|LogoFileName|vs_logo_bk.gif|
|LogoFileNameHC|vs_logo_wh.gif|

Funkcja: **oświadczenie** dotyczące użycia: zestaw specyficznych dla odrzutów dla zawartości przetłumaczonej maszynowo.

|**Element**|**Wartość**|
|-|-|
|MT_Editable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|
|MT_NonEditable|Ten artykuł został przetłumaczony maszynowo. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|
|MT_QualityEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|
|MT_QualityNonEditable|Ten artykuł został przetłumaczony ręcznie. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|
|MT_BetaContents|Ten artykuł został przetłumaczony maszynowo dla wstępnej wersji. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|
|MT_BetaRecycledContents|Ten artykuł został przetłumaczony ręcznie w wersji wstępnej. Jeśli masz połączenie z Internetem, wybierz pozycję "Wyświetl ten temat online", aby wyświetlić tę stronę w trybie edycji razem z pierwotną zawartością w języku angielskim w tym samym czasie.|

Funkcja: użycie **linku** : obsługa linków tematu online

|**Element**|**Wartość**|
|-|-|
|LinkTableTitle|Tabela łączy|
|TopicEnuLinkText|Zapoznaj się z angielską wersją \</a> tego tematu, która jest dostępna na komputerze.|
|TopicOnlineLinkText|Wyświetl ten temat \<a href="{0}" {1}> online\</a>|
|OnlineText|Tryb online|

Funkcja: użycie **kontrolki audio wideo** : Wyświetlanie elementów i tekstu dla zawartości wideo

|**Element**|**Wartość**|
|-|-|
|MultiMediaNotSupported|Aby można było obsługiwać zawartość, musi być zainstalowany program Internet Explorer 9 lub nowszy {0} .|
|VideoText|Wyświetlanie wideo|
|AudioText|przesyłanie strumieniowe audio|
|OnlineVideoLinkText|\<p>Aby wyświetlić film wideo skojarzony z tym tematem, kliknij {0} \<a href="{1}"> {2} tutaj \</a> .\</p>|
|OnlineAudioLinkText|\<p>Aby nawiązać połączenie z dźwiękiem skojarzonym z tym tematem, kliknij {0} \<a href="{1}"> {2} tutaj \</a> .\</p>|

Funkcja: **zawartość nie jest zainstalowana kontrolka** use: elementy tekstowe (ciągi) używane do renderowania contentnotinstalled.htm

|**Element**|**Wartość**|
|-|-|
|ContentNotInstalledTitle|Nie znaleziono zawartości na komputerze.|
|ContentNotInstalledDownloadContentText|\<p>Aby pobrać zawartość na komputer, \<a href="{0}" {1}> kliknij kartę Zarządzanie \</a> .\</p>|
|ContentNotInstalledText|\<p>Na komputerze nie jest zainstalowana żadna zawartość. Skontaktuj się z administratorem w celu zainstalowania lokalnej zawartości pomocy.\</p>|

Funkcja: **nie znaleziono tematu sterującego** use: elementy tekstowe (ciągi) używane do renderowania topicnotfound.htm

|**Element**|**Wartość**|
|-|-|
|TopicNotFoundTitle|Nie można znaleźć żądanego tematu na komputerze.|
|TopicNotFoundViewOnlineText|\<p>Nie znaleziono żądanego tematu na komputerze, ale można \<a href="{0}" {1}> wyświetlić temat w trybie online \</a> .\</p>|
|TopicNotFoundDownloadContentText|\<p>Zobacz okienko nawigacji, aby uzyskać linki do podobnych tematów, lub \<a href="{0}" {1}> kliknij kartę Zarządzanie, \</a> Aby pobrać zawartość do komputera.\</p>|
|TopicNotFoundText|\<p>Nie znaleziono żądanego tematu na komputerze.\</p>|

Funkcja: w **temacie uszkodzona kontrola** użycia: elementy tekstowe (ciągi) używane do renderowania topiccorrupted.htm

|**Element**|**Wartość**|
|-|-|
|TopicCorruptedTitle|Nie można wyświetlić żądanego tematu.|
|TopicCorruptedViewOnlineText|\<p>Podgląd pomocy nie może wyświetlić żądanego tematu. Może wystąpić błąd w zawartości tematu lub podstawowej zależności od systemu.\</p>|

Funkcja: użycie **kontrolki strony głównej** : tekst obsługujący wyświetlanie zawartości węzła najwyższego poziomu podglądu pomocy.

|**Element**|**Wartość**|
|-|-|
|HomePageTitle|Strona główna podglądu pomocy|
|HomePageIntroduction|\<p>Witamy w Podgląd Pomocy firmy Microsoft, podstawowe źródło informacji dla wszystkich osób korzystających z narzędzi, produktów, technologii i usług firmy Microsoft. Podgląd pomocy zapewnia dostęp do informacji o sposobach i odwołaniach, przykładowym kodzie, artykułach technicznych i innych. Aby znaleźć potrzebną zawartość, przejrzyj Spis treści, użyj wyszukiwania pełnotekstowego lub przejdź przez zawartość przy użyciu indeksu słowa kluczowego.\</p>|
|HomePageContentInstallText|\<p>\<br />Za pomocą \<a href="{0}" {1}> karty Zarządzanie zawartością \</a> można wykonać następujące czynności: \<ul> \<li> Dodaj zawartość do komputera. \</li> \<li> Sprawdź, czy są aktualizacje zawartości lokalnej. \</li> \<li> Usuń zawartość z komputera.\</li>\</ul>\</p>|
|HomePageInstalledBooks|Zainstalowane książki|
|HomePageNoBooksInstalled|Nie znaleziono zawartości na komputerze.|
|HomePageHelpSettings|Ustawienia zawartości pomocy|
|HomePageHelpSettingsText|\<p>Bieżące ustawienie to lokalna pomoc. Podgląd pomocy wyświetla zawartość zainstalowaną na komputerze. \<br /> Aby zmienić źródło zawartości pomocy, na pasku menu programu Visual Studio wybierz \<span style="{0}"> Pomoc, ustaw preferencję pomocy \</span> .\<br />\</p>|
|Megabajt|MB|

 **branding.js**

 Plik branding.js zawiera kod JavaScript używany przez elementy oznakowania podglądu pomocy programu Visual Studio.  Poniżej znajduje się lista elementów znakowania i obsługa języka JavaScript.  Wszystkie ciągi do zlokalizowania dla tego pliku są zdefiniowane w sekcji "lokalizowalne ciągi" w górnej części tego pliku.  Plik ICL został utworzony dla ciągów Loc w pliku branding.js.

|**Funkcja znakowania**|**JavaScript — funkcja**|**Opis**|
|-|-|-|
|Var...||Definiowanie zmiennych|
|Pobieranie języka kodu użytkownika|setUserPreferenceLang|mapuje indeks # do języka kodu|
|Ustawianie i pobieranie wartości cookie|getcookas, setcookas||
|Dziedziczony element członkowski|changeMembersLabel|Rozwiń/Zwiń Dziedziczony element członkowski|
|Gdy SelfBranded = false|onLoad|Odczytaj ciąg zapytania, aby sprawdzić, czy jest to żądanie drukowania.  Ustaw wszystkie codesnippets, aby skoncentrować się na karcie preferowane przez użytkownika.  Jeśli jest to żądanie drukowania, ustaw dla isPrinterFriendly wartość true. Sprawdź tryb dużego kontrastu.|
|Fragment kodu|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Napisz wszystkie zwijane obiekty kontrolek do listy.|
||CA_Click|na podstawie stanu obszaru zwijanego definiuje, który obraz i tekst mają być obecne|
|Obsługa kontrastu logo|isBlackBackground()|Wywołuje się, by określić, czy tło jest czarne.  Tylko dokładne w trybie dużego kontrastu.|
||isHighContrast()|Użyj kolorowego zakresu w celu wykrycia trybu dużego kontrastu|
||onHighContrast (czarny)|Wywołuje się, gdy zostanie wykryty duży kontrast|
|Funkcje LST|||
||addToLanSpecTextIdSet (identyfikator)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet (lang)||
|Funkcje multimedialne|Caption (początek, koniec, tekst, styl)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff (identyfikator)||
||toSeconds (t)||
||getAllComments (węzeł)||
||styleRectify (styleName, styleValue)||
||showCC (identyfikator)||
||podtytuł (ID)||

 **PLIKI HTM**

 Pakiet znakowania zawiera zestaw plików HTM, które obsługują scenariusze przekazywania informacji o kluczach w celu ułatwienia użytkownikom zawartości, na przykład Strona główna zawierająca sekcję opisującą, które zestawy zawartości są zainstalowane, oraz strony informujące użytkownika o tym, że nie można znaleźć tematów w lokalnym zestawie tematów. Te pliki HTM można modyfikować na produkt.  Dostawcy powłoki ISO mogą korzystać z domyślnego pakietu znakowania i zmieniać zachowanie i zawartość tych stron w celu ich potrzeby.  Te pliki odnoszą się do odpowiedniego pakietu markowego, aby Tagi znakowania pobierają odpowiednią zawartość z pliku branding.xml.

|**Plik**|**Używanych**|**Wyświetlone źródło zawartości**|
|-|-|-|
|homepage.htm|Jest to strona wyświetlająca aktualnie zainstalowaną zawartość oraz wszelkie inne komunikaty, które są odpowiednie dla użytkownika dotyczące ich zawartości.  Ten plik ma dodatkowy atrybut metadanych "Microsoft.Help.Id" Content = "-1", który umieszcza tę zawartość w górnej części lokalnego SPISu treści zawartości.||
||<META_HOME_PAGE_TITLE_ADD/>|Branding.xml, tag \<HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD/>|Branding.xml, tag \<HomePageIntroduction>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD/>|Branding.xml, tag \<HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD/>|Sekcja nagłówka Branding.xml znacznik \<HomePageInstalledBooks> , dane wygenerowane z aplikacji,  \<HomePageNoBooksInstalled> gdy nie są zainstalowane żadne książki.|
||<HOME_PAGE_SETTINGS_SECTION_ADD/>|Sekcja nagłówka Branding.xml znacznik \<HomePageHelpSettings> , tekst sekcji \<HomePageHelpSettingsText> .|
|topiccorrupted.htm|Gdy w zestawie lokalnym istnieje temat, ale z jakiegoś powodu nie można wyświetlić (uszkodzona zawartość).||
||<META_TOPIC_CORRUPTED_TITLE_ADD/>|Branding.xml, tag \<TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD/>|Branding.xml, tag \<TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Jeśli temat nie zostanie znaleziony w lokalnym zestawie zawartości lub jest dostępny w trybie online||
||<META_TOPIC_NOT_FOUND_TITLE_ADD/>|Branding.xml, tag \<TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD/>|Branding.xml, tag \<TopicNotFoundViewOnlineText> + \<TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD/>|Branding.xml, tag \<TopicNotFoundText>|
|contentnotinstalled.htm|W przypadku braku zainstalowanej zawartości lokalnej dla produktu.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD/>|Branding.xml, tag \<ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD/>|Branding.xml, tag \<ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD/>|Branding.xml, tag \<ContentNotInstalledText>|

 **Pliki CSS**

 Pakiet znakowania podglądu pomocy programu Visual Studio zawiera dwa pliki CSS do obsługi spójnej prezentacji zawartości pomocy programu Visual Studio:

- Znakowanie. css — zawiera elementy CSS do renderowania, gdzie SelfBranded = false

- Printer. css — zawiera elementy CSS do renderowania, gdzie SelfBranded = false

  Znakowanie plików CSS zawiera definicje dla prezentacji tematu programu Visual Studio (zastrzeżenie polega na tym, że znakowanie. css zawarte w Branding_ \<locale> . mshc z usługi pakietu może ulec zmianie).

  **Pliki graficzne**

  Zawartość programu Visual Studio zawiera logo programu Visual Studio, a także inne grafiki.  Poniżej przedstawiono kompletną listę plików graficznych w pakiecie znakowania podglądu pomocy programu Visual Studio.

|**Plik**|**Używanych**|**Przykłady**|
|-|-|-|
|clear.gif|Używane do renderowania zwijanego obszaru||
|footer_slice.gif|Prezentacja stopki||
|info_icon.gif|Używane podczas wyświetlania informacji|Disclaimer|
|online_icon.gif|Ta ikona ma być skojarzona z linkami online||
|tabLeftBD.gif|Używane do renderowania kontenera fragmentów kodu||
|tabRightBD.gif|Używane do renderowania kontenera fragmentów kodu||
|vs_logo_bk.gif|Używany do normalnych odwołań do logo kontrastu zgodnie z definicją w tagu Branding.xml \<LogoFileName> .  W przypadku produktów Visual Studio nazwa logo jest vs_logo_bk.gif.||
|vs_logo_wh.gif|Używany do zwykłych odwołań do logo, jak zdefiniowano w tagu Branding.xml \<LogoFileNameHC> .  W przypadku produktów Visual Studio nazwa logo jest vs_logo_wh.gif.||
|ccOff.png|Ilustracja przedstawiająca podpis||
|ccOn.png|Ilustracja przedstawiająca podpis||
|ImageSprite.png|Używane do renderowania zwijanego obszaru|rozwinięta lub zwinięta grafika|

### <a name="deploying-a-set-of-topics"></a>Wdrażanie zestawu tematów
 Jest to prosty i szybki samouczek dotyczący tworzenia zestawu zawartości podglądu pomocy składającego się z pliku MSHA oraz zestawu OOZ lub MSHCs zawierającego tematy. MSHA to plik XML, który opisuje zestaw plików CAB lub MSHC. Podgląd pomocy może odczytać MSHA, aby uzyskać listę zawartości (. CAB lub. Pliki MSHC) są dostępne dla instalacji lokalnej.

 Jest to tylko podstawowy opis podstawowego schematu XML dla podglądu pomocy MSHA.  Poniżej przedstawiono przykładową implementację poniżej krótkiego omówienia i przykładu HelpContentSetup. msha.

 Nazwa MSHA na potrzeby tego elementu głównego to HelpContentSetup. msha (nazwa pliku może być dowolna, z rozszerzeniem. MSHA). HelpContentSetup. msha (przykład poniżej) powinien zawierać listę dostępnych plików CAB lub MSHCs.  Typ pliku musi być spójny w ramach MSHA (nie obsługuje kombinacji typów plików MSHA i CAB). Dla każdego pliku CAB lub MSHC powinien być \<div class="package"> ...\</div> (Zobacz przykład poniżej).

 Uwaga: w poniższym przykładzie implementacji dołączono pakiet znakowania. Jest to niezbędne do uwzględnienia w celu uzyskania wymaganych elementów renderowania zawartości programu Visual Studio i zachowań zawartości.

 Przykładowy plik HelpContentSetup. msha: (Zastąp "Nazwa zestawu zawartości 1" i "Nazwa zestawu zawartości 2" itp. nazwami plików).

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

1. Utwórz folder lokalny, podobny do "C:\SampleContent"

2. Na potrzeby tego przykładu będziemy używać plików MSHC do przechowywania tematów.  MSHC to plik zip z rozszerzeniem. zip. MSHC.

3. Utwórz poniżej HelpContentSetup. msha jako plik tekstowy (Notatnik został użyty do utworzenia pliku) i Zapisz go w powyższym zanotowanym folderze (zobacz krok 1).

   Klasa "marking" istnieje i jest unikatowa. Oznakowanie mshc jest zawarte w tym podręczniku, dzięki czemu zainstalowana zawartość będzie miała znakowanie, a zachowania zawartości zawarte w MSHCs będą mieć odpowiednie elementy obsługi zawarte w pakiecie znakowania. Z tego powodu błędy będą wyglądały, gdy system wyszuka elementy obsługi, które nie są częścią zgranej (zainstalowanej) zawartości.

   Aby uzyskać pakiet znakowania programu Visual Studio, skopiuj plik Branding_en-US. mshc w folderze C:\Program Files (x86) \Microsoft help Viewer\v2.1\ do folderu roboczego.

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

 Użycie i rozszerzenie powyższych kroków umożliwi VSPs wdrożenie ich zestawów zawartości dla podglądu pomocy programu Visual Studio.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Dodawanie pomocy do programu Visual Studio Shell (zintegrowany i izolowany)
 **Wprowadzenie**

 W tym instruktażu pokazano, jak dołączyć zawartość pomocy do aplikacji powłoki programu Visual Studio, a następnie wdrożyć ją.

 **Wymagania**

1. [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]

2. [Visual Studio 2013 Redist izolowanej powłoki](https://aka.ms/VS2013/IsoShell-LP/all)

   **Omówienie**

   [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)]Powłoka jest wersją [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] środowiska IDE, na którym można oprzeć aplikację. Takie aplikacje zawierają izolowaną powłokę wraz z rozszerzeniami, które tworzysz. Używaj izolowanych szablonów projektów powłoki, które są zawarte w [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] zestawie SDK, do kompilowania rozszerzeń.

   Podstawowe kroki tworzenia izolowanych aplikacji opartych na powłoce i jej pomocy:

3. Uzyskaj [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] pakiet redystrybucyjny powłoki ISO (plik do pobrania firmy Microsoft).

4. W programie Visual Studio Utwórz rozszerzenie pomocy oparte na izolowanej powłoki, na przykład rozszerzenie pomocy contoso, które zostało opisane w dalszej części tego przewodnika.

5. Zawiń rozszerzenie i pakiet redystrybucyjny powłoki ISO do pliku MSI wdrożenia (Konfiguracja aplikacji). Ten Instruktaż nie obejmuje kroku instalacji.

   Utwórz magazyn zawartości programu Visual Studio. W przypadku scenariusza zintegrowanej powłoki Zmień wartość Visual Studio12 na nazwę wykazu produktów w następujący sposób:

- Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12.

- Utwórz plik o nazwie CatalogType.xml i dodaj go do folderu. Plik powinien zawierać następujące wiersze kodu:

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <catalogType>UserManaged</catalogType>
  ```

  Zdefiniuj magazyn zawartości w rejestrze. Dla zintegrowanej powłoki Zmień VisualStudio12 na nazwę katalogu produktu:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12

   Key: LocationPath wartość ciągu: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12\en-US

   Key: nazwa_katalogu — wartość ciągu: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Dokumentacja

  **Tworzenie projektu**

  Aby utworzyć rozszerzenie powłoki izolowanej:

1. W programie Visual Studio w **obszarze plik**wybierz pozycję **Nowy projekt**, w obszarze **Inne typy projektów** wybierz pozycję **rozszerzalność**, a następnie wybierz pozycję  **izolowany powłoka programu Visual Studio**. Nazwij projekt `ContosoHelpShell` ), aby utworzyć projekt rozszerzalności oparty na szablonie powłoki izolowanej programu Visual Studio.

2. W Eksplorator rozwiązań w projekcie ContosoHelpShellUI w folderze pliki zasobów Otwórz ApplicationCommands. vsct. Upewnij się, że ten wiersz jest oznaczony jako komentarz (Wyszukaj ciąg "No_Help"): `<!-- <define name=“No_HelpMenuCommands”/> -->`

3. Wybierz klawisz F5, aby skompilować i uruchomić **debugowanie**. W eksperymentalnym wystąpieniu środowiska IDE izolowanej powłoki wybierz menu **Pomoc** . Upewnij się, że są wyświetlane polecenia **Wyświetl pomoc**, **Dodaj i Usuń zawartość pomocy**oraz **Ustaw polecenie preferencji pomocy** .

4. W Eksplorator rozwiązań w projekcie ContosHelpShell w folderze Dostosowywanie powłoki Otwórz ContosoHelpShell. pkgdef. Aby zdefiniować wykaz pomocy firmy Contoso, Dodaj następujące wiersze:

   ```
    [$RootKey$\Help]
   "Product"="Contoso"
   "Catalog"="Contoso"
   “Version"="100"
   "BrandingPackage"="ContosoBrandingPackage.mshc"
   ```

5. W Eksplorator rozwiązań w projekcie ContosHelpShell w folderze Dostosowywanie powłoki Otwórz ContosoHelpShell. Application. pkgdef. Aby włączyć Pomoc F1, Dodaj następujące wiersze:

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

6. W Eksplorator rozwiązań, w menu kontekstowym rozwiązania ContosoHelpShell wybierz element menu **Właściwości** . W obszarze **Właściwości konfiguracji**wybierz pozycję **Configuration Manager**. W kolumnie **Konfiguracja** Zmień wartości każdej "debug" na "Release".

7. Skompiluj rozwiązanie. Spowoduje to utworzenie zestawu plików w folderze wersji, który zostanie użyty w następnej sekcji.

   Aby przetestować ten sposób jako jeśli został wdrożony:

8. Na komputerze, na którym jest wdrażana firma Contoso, należy zainstalować pobraną (powyżej) powłokę ISO.

9. Utwórz folder w folderze \\ \Program Files (x86) \\ i nadaj mu nazwę `Contoso` .

10. Skopiuj zawartość z folderu ContosoHelpShell Release do \\ folderu \Program Files (x86) \Contoso\.

11. Uruchom Edytor rejestru, wybierając pozycję  **Uruchom** w menu **Start** i wprowadzając polecenie `Regedit` . W Edytorze rejestru wybierz **plik**, a następnie **Importuj**. Przejdź do folderu projektu ContosoHelpShell. W podfolderze ContosoHelpShell wybierz ContosoHelpShell. reg.

12. Utwórz magazyn zawartości:

     Dla powłoki ISO — tworzenie magazynu zawartości contoso C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12

     Dla [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] powłoki zintegrowanej Utwórz folder C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12

13. Utwórz CatalogType.xml i Dodaj do magazynu zawartości (poprzedni krok) zawierającego:

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

14. Dodaj następujące klucze rejestru:

     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.1\Catalogs\VisualStudio12Key: LocationPath wartość ciągu:

     Dla powłoki ISO:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12

     [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Zintegrowana powłoka:

     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio12en-US

     Key: nazwa_katalogu — wartość ciągu: [!INCLUDE[vs_dev12](../../includes/vs-dev12-md.md)] Dokumentacja. W przypadku powłoki ISO jest to nazwa katalogu.

15. Skopiuj zawartość (OOZ lub MSHC i MSHA) do folderu lokalnego.

16. Przykładowy wiersz polecenia zintegrowanej powłoki służący do testowania magazynu zawartości. W przypadku powłoki ISO zmień odpowiednio wykaz i launchingApp wartości, aby odpowiadały produktowi.

      "C:\Program Files (x86) \Microsoft help Viewer\v2.1\HlpViewer.exe"/catalogName VisualStudio12/helpQuery Method = "Strona&ID = ContosoTopic0"/launchingApp Microsoft, VisualStudio, 12

17. Uruchom aplikację contoso (z poziomu katalogu głównego aplikacji Contoso). W obszarze powłoki ISO wybierz element menu **Pomoc** i Zmień **preferencję Ustaw pomoc** na korzystanie z **pomocy lokalnej**.

18. W obrębie powłoki wybierz element menu **Pomoc** , a następnie **Wyświetl pomoc**. Lokalna przeglądarka pomocy powinna zostać uruchomiona. Wybierz kartę **Zarządzanie zawartością** . W obszarze **Źródło instalacji**wybierz przycisk opcji **dysk** . Wybierz przycisk **...** i przejdź do folderu lokalnego zawierającego zawartość contoso (skopiowane do folderu lokalnego w powyższym kroku). Wybierz HelpContentSetup. msha. Firma Contoso powinna teraz być wyświetlana jako książka w wybranych książkach. Wybierz pozycję **Dodaj**, a następnie wybierz przycisk **Aktualizuj** (prawy dolny róg).

19. W środowisku IDE firmy Contoso wybierz klawisz F1, aby przetestować funkcję F1.

### <a name="additional-resources"></a>Dodatkowe zasoby

Aby uzyskać interfejs API środowiska uruchomieniowego, zobacz [interfejs API pomocy systemu Windows](https://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).

Aby uzyskać więcej informacji na temat korzystania z interfejsu API pomocy, zobacz [przykłady kodu podglądu pomocy](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Aby uzyskać aktualizacje dotyczące rozwiązywania problemów, zobacz [plik Readme podglądu pomocy](https://go.microsoft.com/fwlink/?LinkId=255960).
