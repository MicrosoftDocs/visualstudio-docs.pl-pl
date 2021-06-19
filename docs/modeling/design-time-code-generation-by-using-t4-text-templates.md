---
title: Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4
description: Dowiedz się, jak szablony tekstowe T4 w czasie projektowania umożliwiają generowanie kodu programu i innych plików w Visual Studio projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f8b7bc48a5c409dbecbb313fd277a31ad1cec287
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389140"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4

Szablony tekstowe T4 czasu projektowania umożliwiają generowanie kodu programu i innych plików w Visual Studio projektu. Zazwyczaj szablony są pisane tak, aby zmieniały kod generowany w zależności od danych z *modelu.* Model to plik lub baza danych zawierająca kluczowe informacje o wymaganiach aplikacji.

Na przykład możesz mieć model, który definiuje przepływ pracy jako tabelę lub diagram. Na podstawie modelu można wygenerować oprogramowanie, które wykonuje przepływ pracy. Gdy wymagania użytkowników zmienią się, można łatwo omówić nowy przepływ pracy z użytkownikami. Ponowne generowanie kodu z przepływu pracy jest bardziej niezawodne niż ręczne aktualizowanie kodu.

> [!NOTE]
> Model *to* źródło danych, które opisuje konkretny aspekt aplikacji. Może to być dowolna forma, w dowolnym rodzaju pliku lub bazy danych. Nie musi mieć określonej formy, takiej jak model UML lub Domain-Specific language. Typowe modele mają postać tabel lub plików XML.

Prawdopodobnie znasz już generowanie kodu. Podczas definiowania zasobów w pliku **resx** w rozwiązaniu Visual Studio automatycznie generowany jest zestaw klas i metod. Plik zasobów sprawia, że edycja zasobów jest znacznie łatwiejsza i bardziej niezawodna niż w przypadku edytowania klas i metod. Za pomocą szablonów tekstowych można wygenerować kod w taki sam sposób ze źródła własnego projektu.

Szablon tekstowy zawiera mieszankę tekstu, który chcesz wygenerować, i kod programu, który generuje zmienne części tekstu. Kod programu umożliwia powtarzanie lub warunkowe pomijanie części wygenerowanego tekstu. Wygenerowany tekst może być kodem programu, który będzie częścią aplikacji.

## <a name="create-a-design-time-t4-text-template"></a>Tworzenie szablonu Design-Time T4

1. Utwórz nowy projekt Visual Studio lub otwórz istniejący.

2. Dodaj plik szablonu tekstowego do projektu i nadaj mu nazwę z rozszerzeniem **.tt**.

    Aby to zrobić, **w Eksplorator rozwiązań** menu skrótów projektu wybierz pozycję **Dodaj**  >  **nowy element.** W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję Szablon **tekstowy** w środkowym okienku.

    Zwróć uwagę, **że właściwością narzędzia niestandardowego** pliku jest **TextTemplatingFileGenerator.**

3. Otwórz ten plik. Będzie ona już zawierać następujące dyrektywy:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Jeśli szablon został dodany do [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektu, atrybut języka będzie miał wartość " `VB` ".

4. Dodaj tekst na końcu pliku. Na przykład:

   ```
   Hello, world!
   ```

5. Zapisz plik.

    Może zostać wyświetlony komunikat **Ostrzeżenie o** zabezpieczeniach z prośbą o potwierdzenie uruchomienia szablonu. Kliknij przycisk **OK**.

6. W **Eksplorator rozwiązań** rozwiń węzeł pliku szablonu, a znajdziesz plik z rozszerzeniem **.txt**. Plik zawiera tekst wygenerowany na podstawie szablonu.

   > [!NOTE]
   > Jeśli projekt jest projektem Visual Basic, musisz kliknąć pozycję **Pokaż** wszystkie pliki, aby wyświetlić plik wyjściowy.

### <a name="regenerate-the-code"></a>Ponowne generowanie kodu

Szablon zostanie wykonany, generując plik pomocniczy, w dowolnym z następujących przypadków:

- Edytuj szablon, a następnie zmień fokus na inne Visual Studio okna.

- Zapisz szablon.

- Kliknij **pozycję Przekształć wszystkie** szablony w menu **Kompilacja.** Spowoduje to przekształcenie wszystkich szablonów w Visual Studio rozwiązania.

- W **Eksplorator rozwiązań** menu skrótów dowolnego pliku wybierz polecenie **Uruchom narzędzie niestandardowe.** Ta metoda służy do przekształcania wybranego podzestawu szablonów.

Można również skonfigurować projekt Visual Studio tak, aby szablony były wykonywane po zmianie odczytywanych plików danych. Aby uzyskać więcej informacji, zobacz [Ponowne generowanie kodu automatycznie.](#Regenerating)

## <a name="generate-variable-text"></a>Generowanie tekstu zmiennej

Szablony tekstowe umożliwiają używanie kodu programu do zmieniania zawartości wygenerowanego pliku.

1. Zmień zawartość `.tt` pliku:

   ```csharp
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   <#int top = 10;

   for (int i = 0; i<=top; i++)
   { #>
      The square of <#= i #> is <#= i*i #>
   <# } #>
   ```

   ```vb
   <#@ template hostspecific="false" language="VB" #>
   <#@ output extension=".txt" #>
   <#Dim top As Integer = 10

   For i As Integer = 0 To top
   #>
       The square of <#= i #> is <#= i*i #>
   <#
   Next
   #>
   ```

2. Zapisz plik tt i ponownie sprawdź wygenerowany .txt plik. Wyświetla on listę kwadratów liczb z wartości od 0 do 10.

   Zwróć uwagę, że instrukcje są ujęte w `<#...#>` , i pojedyncze wyrażenia w obrębie `<#=...#>` . Aby uzyskać więcej informacji, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

   Jeśli napiszesz kod generujący w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , dyrektywa powinna zawierać `template` . `language="VB"` Wartość domyślna to `"C#"`.

## <a name="debugging-a-design-time-t4-text-template"></a>Debugowanie szablonu Design-Time tekstowego T4

Aby debugować szablon tekstowy:

- Wstaw `debug="true"` do `template` dyrektywy . Na przykład:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Ustaw punkty przerwania w szablonie w taki sam sposób, jak w przypadku zwykłego kodu.

- Wybierz **pozycję Debuguj szablon T4** z menu skrótów pliku szablonu tekstowego w Eksplorator rozwiązań.

   Szablon jest uruchamiany i zatrzymuje się w punktach przerwania. Możesz badać zmienne i przechodzić przez kod w zwykły sposób.

> [!TIP]
> `debug="true"` sprawia, że wygenerowana mapa kodu jest dokładniejsza w szablonie tekstowym przez wstawienie większej liczby dyrektyw numerowania wiersza do wygenerowanego kodu. Jeśli go nie opuścisz, punkty przerwania mogą zatrzymać uruchomienie w niewłaściwym stanie.
>
> Jednak możesz pozostawić klauzulę w dyrektywie szablonu nawet wtedy, gdy nie debugujesz. Powoduje to tylko niewielki spadek wydajności.

## <a name="generating-code-or-resources-for-your-solution"></a>Generowanie kodu lub zasobów dla rozwiązania

Możesz generować pliki programu, które różnią się w zależności od modelu. Model to dane wejściowe, takie jak baza danych, plik konfiguracji, model UML, model DSL lub inne źródło. Zazwyczaj generujesz kilka plików programu z tego samego modelu. Aby to osiągnąć, należy utworzyć plik szablonu dla każdego wygenerowanego pliku programu i wszystkie szablony odczytać ten sam model.

### <a name="to-generate-program-code-or-resources"></a>Aby wygenerować kod programu lub zasoby

1. Zmień dyrektywę output, aby wygenerować plik odpowiedniego typu, taki jak cs, vb, resx lub .xml.

2. Wstaw kod, który wygeneruje wymagany kod rozwiązania. Jeśli na przykład chcesz wygenerować trzy deklaracje pól liczb całkowitych w klasie:

    ```csharp

    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    <# var properties = new string [] {"P1", "P2", "P3"}; #>
    // This is generated code:
    class MyGeneratedClass {
    <# // This code runs in the text template:
      foreach (string propertyName in properties)  { #>
      // Generated code:
      private int <#= propertyName #> = 0;
    <# } #>
    }
    ```

    ```vb
    <#@ template debug="false" hostspecific="false" language="VB" #>
    <#@ output extension=".cs" #>
    <# Dim properties = {"P1", "P2", "P3"} #>
    class MyGeneratedClass {
    <#
       For Each propertyName As String In properties
    #>
      private int <#= propertyName #> = 0;
    <#
       Next
    #>
    }

    ```

3. Zapisz plik i sprawdź wygenerowany plik, który teraz zawiera następujący kod:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generowanie kodu i wygenerowanego tekstu

Podczas generowania kodu programu najważniejsze jest uniknięcie mylącego generowania kodu wykonywanego w szablonie i wynikowego wygenerowanego kodu, który staje się częścią rozwiązania. Oba języki nie muszą być takie same.

Poprzedni przykład ma dwie wersje. W jednej wersji kod generujący znajduje się w języku C#. W drugiej wersji kod generujący jest Visual Basic. Jednak tekst wygenerowany przez oba te klasy jest taki sam i jest klasą języka C#.

W ten sam sposób można użyć szablonu do wygenerowania [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] kodu w dowolnym języku. Wygenerowany tekst nie musi być w żadnym konkretnym języku i nie musi być kodem programu.

### <a name="structuring-text-templates"></a>Strukturyzowanie szablonów tekstowych

Zgodnie z dobrą praktyką kod szablonu dzielimy na dwie części:

- Część konfiguracji lub zbierania danych, która ustawia wartości w zmiennych, ale nie zawiera bloków tekstowych. W poprzednim przykładzie ta część to inicjalizacja `properties` .

   Jest to czasami nazywane sekcją "model", ponieważ konstruuje model w magazynie i zwykle odczytuje plik modelu.

- Część generowania tekstu `foreach(...){...}` (w przykładzie), która używa wartości zmiennych.

   Nie jest to konieczne oddzielenie, ale jest to styl, który ułatwia odczytywanie szablonu przez zmniejszenie złożoności części, która zawiera tekst.

## <a name="reading-files-or-other-sources"></a>Odczytywanie plików lub innych źródeł

Aby uzyskać dostęp do pliku modelu lub bazy danych, kod szablonu może używać zestawów, takich jak System.XML. Aby uzyskać dostęp do tych zestawów, należy wstawić dyrektywy takie jak:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

Dyrektywa udostępnia określony zestaw kodowi szablonu w taki sam sposób, jak sekcja Odwołania Visual Studio `assembly` projektu. Nie trzeba dołączać odwołania do System.dll, które jest przywoływyne automatycznie. Dyrektywa umożliwia używanie typów bez używania ich w pełni kwalifikowanych nazw w taki sam sposób jak dyrektywa `import` `using` w zwykłym pliku programu.

Na przykład po zaimportowaniu **System.IO** można napisać:

```csharp

<# var properties = File.ReadLines("C:\\propertyList.txt");#>
...
<# foreach (string propertyName in properties) { #>
...
```

```vb
<# For Each propertyName As String In
             File.ReadLines("C:\\propertyList.txt")
#>
```

### <a name="opening-a-file-with-a-relative-pathname"></a>Otwieranie pliku ze względną nazwą ścieżki

Aby załadować plik z lokalizacji względem szablonu tekstowego, możesz użyć `this.Host.ResolvePath()` . Aby użyć tej funkcji. Hosta, należy ustawić `hostspecific="true"` w `template` :

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Następnie możesz napisać na przykład:

```csharp
<# string filename = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim filename = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Można również użyć `this.Host.TemplateFile` funkcji , która identyfikuje nazwę bieżącego pliku szablonu.

Typ `this.Host` (w VB, `Me.Host` ) to `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost` .

### <a name="getting-data-from-visual-studio"></a>Pobieranie danych z Visual Studio

Aby korzystać z usług Visual Studio, ustaw `hostSpecific` atrybut i załaduj `EnvDTE` zestaw. `Microsoft.VisualStudio.TextTemplating`Zaimportuj plik , który `GetCOMService()` zawiera metodę rozszerzenia .  Następnie można użyć funkcji IServiceProvider.GetCOMService() w celu uzyskania dostępu do jednostek DTE i innych usług. Na przykład:

```src
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

> [!TIP]
> Szablon tekstowy jest uruchamiany we własnej domenie aplikacji, a dostęp do usług jest uzyskiwany przez marshaling. W takim przypadku getCOMService() jest bardziej niezawodne niż GetService().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Automatyczne ponowne generowanie kodu

Zazwyczaj kilka plików w rozwiązaniu Visual Studio jest generowanych z jednym modelem wejściowym. Każdy plik jest generowany na podstawie własnego szablonu, ale wszystkie szablony odwołują się do tego samego modelu.

Jeśli model źródłowy zmieni się, należy ponownie uruchomić wszystkie szablony w rozwiązaniu. Aby to zrobić ręcznie, wybierz pozycję **Przekształć wszystkie szablony** w menu **Kompilacja.**

Jeśli zainstalowano zestaw SDK modelowania Visual Studio, wszystkie szablony mogą być przekształcane automatycznie podczas każdej kompilacji. W tym celu edytuj plik projektu (csproj lub vbproj) w edytorze tekstów i dodaj następujące wiersze pod koniec pliku po innych `<import>` instrukcjach:

> [!NOTE]
> Zestaw SDK przekształcania szablonu tekstu i Visual Studio SDK modelowania tekstu są instalowane automatycznie podczas instalowania określonych funkcji Visual Studio. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

::: moniker-end

Aby uzyskać więcej informacji, zobacz [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Raportowanie błędów

Aby umieścić komunikaty o błędach i ostrzeżeniach w Visual Studio błędu, można użyć tych metod:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Konwertowanie istniejącego pliku na szablon

Przydatną funkcją szablonów jest to, że wyglądają bardzo podobnie do plików, które generują, wraz z wstawionego kodu programu. Sugeruje to przydatną metodę tworzenia szablonu. Najpierw utwórz zwykły plik jako prototyp, taki jak plik, a następnie stopniowo wprowadzaj kod generacji, który [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] zmienia wynikowy plik.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Aby przekonwertować istniejący plik na szablon czasu projektowania

1. Do Visual Studio dodaj plik typu, który chcesz wygenerować, taki jak `.cs` , `.vb` lub `.resx` .

2. Przetestuj nowy plik, aby upewnić się, że działa.

3. W Eksplorator rozwiązań zmień rozszerzenie nazwy pliku na **.tt**.

4. Sprawdź następujące właściwości pliku **tt:**

   |Właściwość |Ustawienie |
   |-|-|
   | **Narzędzie niestandardowe =** | **Texttemplatingfilegenerator** |
   | **Akcja kompilacji =** | **Brak** |

5. Wstaw następujące wiersze na początku pliku:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Jeśli chcesz napisać kod generujący szablon w pliku , ustaw atrybut [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] `language` na wartość zamiast `"VB"` `"C#"` .

    Ustaw atrybut na rozszerzenie nazwy pliku dla typu pliku, który chcesz wygenerować, na przykład `extension` `.cs` , lub `.resx` `.xml` .

6. Zapisz plik.

    Zostanie utworzony plik podmiotu zależnego z określonym rozszerzeniem. Jego właściwości są poprawne dla typu pliku. Na przykład **właściwością akcja kompilacji** pliku cs będzie **Kompilowanie**.

    Sprawdź, czy wygenerowany plik zawiera taką samą zawartość jak oryginalny plik.

7. Zidentyfikuj część pliku, która ma się różnić. Na przykład część, która pojawia się tylko w określonych warunkach, lub część, która jest powtarzana, lub gdzie konkretne wartości się różnią. Wstaw generujący kod. Zapisz plik i sprawdź, czy plik pomocniczy został poprawnie wygenerowany. Powtórz ten krok.

## <a name="guidelines-for-code-generation"></a>Wytyczne dotyczące generowania kodu

Zobacz [Wytyczne dotyczące pisania szablonów tekstowych T4.](../modeling/guidelines-for-writing-t4-text-templates.md)

## <a name="next-steps"></a>Następne kroki

|Następny krok|Temat|
|-|-|
|Napisz i debuguj bardziej zaawansowany szablon tekstowy z kodem, który używa funkcji pomocniczych, dołączonych plików i danych zewnętrznych.|[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)|
|Generowanie dokumentów na podstawie szablonów w czasie uruchamiania.|[Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Uruchamianie generowania tekstu poza Visual Studio.|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Przekształć dane w język specyficzny dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Pisanie procesorów dyrektyw w celu przekształcania własnych źródeł danych.|[Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Zobacz też

- [Zalecenia dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)
