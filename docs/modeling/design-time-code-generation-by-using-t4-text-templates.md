---
title: Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08451c679f372cb376c6baf97a9a4d06282ba45f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748422"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4

Szablony tekstu T4 w czasie projektowania pozwalają generować kod programu i inne pliki w projekcie programu Visual Studio. Zwykle należy napisać szablony, aby różnicować kod generowany przez nich zgodnie z danymi z *modelu*. Model to plik lub baza danych, która zawiera najważniejsze informacje o wymaganiach aplikacji.

Na przykład można mieć model, który definiuje przepływ pracy jako tabelę lub diagram. Z modelu można wygenerować oprogramowanie, które wykonuje przepływ pracy. W przypadku zmiany wymagań użytkowników można łatwo omówić nowy przepływ pracy z użytkownikami. Ponowne generowanie kodu z przepływu pracy jest bardziej niezawodne niż ręczne aktualizowanie kodu.

> [!NOTE]
> *Model* to źródło danych opisujące konkretny aspekt aplikacji. Może to być dowolny formularz w dowolnym rodzaju pliku lub bazy danych. Nie musi znajdować się w żadnej konkretnej formie, takiej jak model UML lub model języka specyficznego dla domeny. Typowe modele są w postaci tabel lub plików XML.

Prawdopodobnie masz już doświadczenie z generowaniem kodu. Podczas definiowania zasobów w pliku **resx** w rozwiązaniu programu Visual Studio zestaw klas i metod jest generowany automatycznie. Plik resources sprawia, że edytowanie zasobów jest znacznie prostsze i bardziej niezawodne niż w przypadku konieczności edytowania klas i metod. Za pomocą szablonów tekstowych można generować kod w taki sam sposób, jak w przypadku źródła własnego projektu.

Szablon tekstowy zawiera kombinację tekstu, który ma zostać wygenerowany, i kod programu generujący zmienne części tekstu. Kod programu umożliwia powtarzanie lub warunkowe pominięcie części wygenerowanego tekstu. Wygenerowany tekst może być kodem programu, który będzie częścią aplikacji.

## <a name="create-a-design-time-t4-text-template"></a>Tworzenie szablonu tekstu T4 w czasie projektowania

1. Utwórz nowy projekt programu Visual Studio lub Otwórz istniejący.

2. Dodaj plik szablonu tekstu do projektu i nadaj mu nazwę, która ma rozszerzenie **. tt**.

    W tym celu w **Eksplorator rozwiązań**, w menu skrótów projektu, wybierz **Dodaj**  > **nowy element**. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **szablon tekstowy** w środkowym okienku.

    Zwróć uwagę, że właściwość **niestandardowego narzędzia** pliku to **TextTemplatingFileGenerator**.

3. Otwórz plik. Zawiera już następujące dyrektywy:

   ```
   <#@ template hostspecific="false" language="C#" #>
   <#@ output extension=".txt" #>
   ```

    Jeśli szablon został dodany do projektu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], atrybut Language będzie "`VB`".

4. Dodaj tekst na końcu pliku. Na przykład:

   ```
   Hello, world!
   ```

5. Zapisz plik.

    Może zostać wyświetlone okno komunikatu z **ostrzeżeniem o zabezpieczeniach** z prośbą o potwierdzenie, że chcesz uruchomić szablon. Kliknij przycisk **OK**.

6. W **Eksplorator rozwiązań**rozwiń węzeł plik szablonu i znajdziesz plik z rozszerzeniem **txt**. Plik zawiera tekst wygenerowany na podstawie szablonu.

   > [!NOTE]
   > Jeśli projekt jest projektem Visual Basic, należy kliknąć przycisk **Pokaż wszystkie pliki** , aby wyświetlić plik wyjściowy.

### <a name="regenerate-the-code"></a>Wygeneruj ponownie kod

Szablon zostanie wykonany, generując plik pomocniczy w jednym z następujących przypadków:

- Edytuj szablon, a następnie zmień fokus na inne okno programu Visual Studio.

- Zapisz szablon.

- Kliknij kolejno pozycje **Przekształć wszystkie szablony** w menu **kompilacja** . Spowoduje to przekształcenie wszystkich szablonów w rozwiązaniu programu Visual Studio.

- W **Eksplorator rozwiązań**, w menu skrótów dowolnego pliku, wybierz **Uruchom narzędzie niestandardowe**. Użyj tej metody, aby przekształcić wybrany podzestaw szablonów.

Możesz również skonfigurować projekt programu Visual Studio tak, aby szablony były wykonywane, gdy pliki danych, które zostały przez nich odczytane, uległy zmianie. Aby uzyskać więcej informacji, zobacz Ponowne [generowanie kodu automatycznie](#Regenerating).

## <a name="generate-variable-text"></a>Generuj tekst zmiennej

Szablony tekstowe umożliwiają użycie kodu programu w celu zróżnicowania zawartości wygenerowanego pliku.

1. Zmień zawartość pliku `.tt`:

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

2. Zapisz plik. tt i ponownie Zbadaj wygenerowany plik txt. Wyświetla listę kwadratów liczb z przenoszącą od 0 do 10.

   Zauważ, że instrukcje są ujęte w `<#...#>` i pojedyncze wyrażenia w `<#=...#>`. Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

   Jeśli napiszesz kod generujący w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dyrektywa `template` powinna zawierać `language="VB"`. `"C#"` jest wartością domyślną.

## <a name="debugging-a-design-time-t4-text-template"></a>Debugowanie szablonu tekstu T4 w czasie projektowania

Aby debugować szablon tekstowy:

- Wstaw `debug="true"` do dyrektywy `template`. Na przykład:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Ustaw punkty przerwania w szablonie w taki sam sposób, jak w przypadku zwykłego kodu.

- Wybierz **Debuguj szablon T4** z menu skrótów pliku szablonu tekstu w Eksplorator rozwiązań.

   Szablon jest uruchamiany i zatrzyma się w punktach przerwania. Można przeanalizować zmienne i krokowo przez kod w zwykły sposób.

> [!TIP]
> `debug="true"` powoduje, że wygenerowany kod mapuje się dokładniej do szablonu tekstu, wstawiając więcej dyrektyw numerowania wierszy do wygenerowanego kodu. Jeśli go opuścisz, punkty przerwania mogą przestać działać w nieprawidłowym stanie.
>
> Ale można pozostawić klauzulę w dyrektywie Template, nawet jeśli nie jest debugowana. Powoduje to, że jest to bardzo mały spadek wydajności.

## <a name="generating-code-or-resources-for-your-solution"></a>Generowanie kodu lub zasobów dla rozwiązania

Istnieje możliwość generowania plików programu, które różnią się w zależności od modelu. Model to dane wejściowe, takie jak baza danych, plik konfiguracji, model UML, model DSL lub inne źródło. Zwykle generowane są kilka plików programów z tego samego modelu. Aby to osiągnąć, należy utworzyć plik szablonu dla każdego wygenerowanego pliku programu i wszystkie szablony odczytywać ten sam model.

### <a name="to-generate-program-code-or-resources"></a>Aby wygenerować kod lub zasoby programu

1. Zmień dyrektywę wyjściową, aby wygenerować plik odpowiedniego typu, na przykład CS, VB lub XML.

2. Wstaw kod, który będzie generował kod rozwiązania, którego potrzebujesz. Na przykład, jeśli chcesz wygenerować trzy deklaracje pola liczb całkowitych w klasie:

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

3. Zapisz plik i sprawdź, czy wygenerowany plik zawiera teraz następujący kod:

    ```csharp
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generowanie kodu i wygenerowanego tekstu

Podczas generowania kodu programu najważniejsze jest, aby uniknąć pomyłki generowanego kodu, który jest wykonywany w szablonie, oraz wygenerowanego kodu, który stał się częścią rozwiązania. Te dwa języki nie muszą być takie same.

Poprzedni przykład ma dwie wersje. W jednej wersji kod generujący znajduje się w C#. W innej wersji kod generujący jest Visual Basic. Ale tekst wygenerowany przez oba te elementy są takie same i jest C# klasą.

W ten sam sposób możesz użyć szablonu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], aby wygenerować kod w dowolnym języku. Wygenerowany tekst nie musi znajdować się w żadnym konkretnym języku i nie musi być kodem programu.

### <a name="structuring-text-templates"></a>Tworzenie struktury szablonów tekstowych

W przypadku dobrych rozwiązań warto rozdzielić kod szablonu na dwie części:

- Konfiguracja lub część zbierania danych, która ustawia wartości w zmiennych, ale nie zawiera bloków tekstowych. W poprzednim przykładzie ta część jest inicjalizacją `properties`.

   Jest to czasami nazywane sekcją "model", ponieważ konstruuje model w sklepie i zwykle odczytuje plik modelu.

- Część służąca do generowania tekstu (`foreach(...){...}` w przykładzie), która używa wartości zmiennych.

   Nie jest to konieczne separacja, ale jest to styl, który ułatwia odczytywanie szablonu przez zredukowanie złożoności części zawierającej tekst.

## <a name="reading-files-or-other-sources"></a>Odczytywanie plików lub innych źródeł

Aby uzyskać dostęp do pliku modelu lub bazy danych, kod szablonu może używać zestawów, takich jak system. XML. Aby uzyskać dostęp do tych zestawów, należy wstawić dyrektywy takie jak następujące:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

Dyrektywa `assembly` sprawia, że określony zestaw jest dostępny dla kodu szablonu w taki sam sposób jak sekcja References w projekcie programu Visual Studio. Nie trzeba dołączać odwołania do pliku System. dll, który jest przywoływany automatycznie. Dyrektywa `import` umożliwia korzystanie z typów bez użycia ich w pełni kwalifikowanych nazw w taki sam sposób jak w przypadku dyrektywy `using` w zwykłym pliku programu.

Na przykład po zaimportowaniu **System.IO**można napisać:

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

### <a name="opening-a-file-with-a-relative-pathname"></a>Otwieranie pliku z względną ścieżką

Aby załadować plik z lokalizacji względem szablonu tekstu, można użyć `this.Host.ResolvePath()`. Do użycia. Należy ustawić `hostspecific="true"` w `template`:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
```

Następnie można napisać:

```csharp
<# string fileName = this.Host.ResolvePath("filename.txt");
  string [] properties = File.ReadLines(filename);
#>
...
<#  foreach (string propertyName in properties { #>
...
```

```vb
<# Dim fileName = Me.Host.ResolvePath("propertyList.txt")
   Dim properties = File.ReadLines(filename)
#>
...
<#   For Each propertyName As String In properties
...
#>
```

Można również użyć `this.Host.TemplateFile`, który identyfikuje nazwę bieżącego pliku szablonu.

Typ `this.Host` (w języku VB, `Me.Host`) jest `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost`.

### <a name="getting-data-from-visual-studio"></a>Pobieranie danych z programu Visual Studio

Aby korzystać z usług oferowanych w programie Visual Studio, należy ustawić atrybut `hostSpecific` i załadować zestaw `EnvDTE`. Zaimportuj `Microsoft.VisualStudio.TextTemplating`, która zawiera `GetCOMService()` metodę rozszerzenia.  Następnie można użyć IServiceProvider. GetCOMService (), aby uzyskać dostęp do DTE i innych usług. Na przykład:

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
> Szablon tekstowy jest uruchamiany w jego własnej domenie aplikacji, a usługi są dostępne przez kierowanie. W takim przypadku GetCOMService () jest bardziej niezawodny niż GetService ().

## <a name="Regenerating"></a>Automatyczne generowanie kodu

Zazwyczaj kilka plików w rozwiązaniu programu Visual Studio jest generowanych z jednym modelem wejściowym. Każdy plik jest generowany na podstawie własnego szablonu, ale wszystkie szablony odwołują się do tego samego modelu.

Jeśli model źródłowy ulegnie zmianie, należy uruchomić ponowne uruchomienie wszystkich szablonów w rozwiązaniu. Aby to zrobić ręcznie, wybierz pozycję **Przekształć wszystkie szablony** w menu **kompilacja** .

Jeśli zainstalowano zestaw SDK modelowania programu Visual Studio, wszystkie szablony są przekształcane automatycznie za każdym razem, gdy wykonujesz kompilację. W tym celu należy edytować plik projektu (. csproj lub. vbproj) w edytorze tekstów i dodać następujące wiersze blisko końca pliku, po dowolnych innych instrukcjach `<import>`:

> [!NOTE]
> Zestaw SDK transformacji szablonu tekstu i Visual Studio Modeling SDK są instalowane automatycznie podczas instalowania określonych funkcji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

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

Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Raportowanie błędów

Aby umieścić komunikaty o błędach i ostrzeżeniach w oknie błędu programu Visual Studio, można użyć następujących metod:

```
Error("An error message");
Warning("A warning message");
```

## <a name="Converting"></a>Konwertowanie istniejącego pliku na szablon

Przydatną funkcją szablonów jest to, że wyglądają bardzo podobnie do generowanych przez nich plików wraz z niektórym wstawionym kodem programu. Sugeruje to przydatną metodę tworzenia szablonu. Najpierw utwórz zwykły plik jako prototyp, taki jak plik [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], a następnie stopniowo wprowadzaj kod generacji, który zmienia ten plik.

### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Aby skonwertować istniejący plik na szablon czasu projektowania

1. Do projektu programu Visual Studio Dodaj plik typu, który chcesz wygenerować, na przykład plik `.cs`, `.vb` lub `.resx`.

2. Przetestuj nowy plik, aby upewnić się, że działa.

3. W Eksplorator rozwiązań Zmień rozszerzenie nazwy pliku na **. tt**.

4. Sprawdź następujące właściwości pliku **TT** :

   | | |
   |-|-|
   | **Niestandardowe narzędzie =** | **TextTemplatingFileGenerator** |
   | **Akcja kompilacji =** | **Dawaj** |

5. Wstaw następujące wiersze na początku pliku:

   ```
   <#@ template debug="false" hostspecific="false" language="C#" #>
   <#@ output extension=".cs" #>
   ```

    Jeśli chcesz napisać kod generujący szablon w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ustaw atrybut `language` na `"VB"` zamiast `"C#"`.

    Ustaw atrybut `extension` na rozszerzenie nazwy pliku dla typu pliku, który chcesz wygenerować, na przykład `.cs`, `.resx` lub `.xml`.

6. Zapisz plik.

    Tworzony jest plik pomocniczy z określonym rozszerzeniem. Jego właściwości są poprawne dla typu pliku. Na przykład właściwość **Akcja kompilacji** pliku CS zostanie **skompilowana**.

    Sprawdź, czy wygenerowany plik zawiera tę samą zawartość co oryginalny plik.

7. Zidentyfikuj część pliku, który ma być różny. Na przykład część, która pojawia się tylko pod pewnymi warunkami lub częścią, która jest powtarzana lub która różni się od konkretnych wartości. Wstaw kod generujący. Zapisz plik i sprawdź, czy plik pomocniczy został prawidłowo wygenerowany. Powtórz ten krok.

## <a name="guidelines-for-code-generation"></a>Wskazówki dotyczące generowania kodu

Zapoznaj się z instrukcjami dotyczącymi [pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Następne kroki

|Następny krok|Temat|
|-|-|
|Pisanie i debugowanie bardziej zaawansowanego szablonu tekstu, z kodem korzystającym z funkcji pomocniczych, dołączonych plików i danych zewnętrznych.|[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)|
|Generuj dokumenty z szablonów w czasie wykonywania.|[Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Uruchom Generowanie tekstu poza programem Visual Studio.|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Przekształć dane w postaci języka specyficznego dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Napisz procesory dyrektywy, aby przekształcić własne źródła danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Zobacz także

- [Zalecenia dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)
