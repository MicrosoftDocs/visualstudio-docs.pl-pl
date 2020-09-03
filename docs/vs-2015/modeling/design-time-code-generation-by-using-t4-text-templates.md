---
title: Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, guidelines for code generation
- text templates, data source model
- TextTemplatingFileGenerator custom tool
- Transform All Templates
- text templates, getting started
- Text Template project item
- text templates, generating code for your application
ms.assetid: 2774b83d-1adb-4c66-a607-746e019b80c0
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efdbf1b96e1dc49f5b9c48cebe6cededc9ea7c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534150"
---
# <a name="design-time-code-generation-by-using-t4-text-templates"></a>Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablony tekstu T4 w czasie projektowania pozwalają generować kod programu i inne pliki w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekcie. Zwykle należy napisać szablony, aby różnicować kod generowany przez nich zgodnie z danymi z *modelu*. Model to plik lub baza danych, która zawiera najważniejsze informacje o wymaganiach aplikacji.

 Na przykład można mieć model, który definiuje przepływ pracy jako tabelę lub diagram. Z modelu można wygenerować oprogramowanie, które wykonuje przepływ pracy. W przypadku zmiany wymagań użytkowników można łatwo omówić nowy przepływ pracy z użytkownikami. Ponowne generowanie kodu z przepływu pracy jest bardziej niezawodne niż ręczne aktualizowanie kodu.

> [!NOTE]
> *Model* to źródło danych opisujące konkretny aspekt aplikacji. Może to być dowolny formularz w dowolnym rodzaju pliku lub bazy danych. Nie musi znajdować się w żadnej konkretnej formie, takiej jak model UML lub model języka specyficznego dla domeny. Typowe modele są w postaci tabel lub plików XML.

 Prawdopodobnie masz już doświadczenie z generowaniem kodu. Podczas definiowania zasobów w pliku **resx** w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu zestaw klas i metod jest generowany automatycznie. Plik resources sprawia, że edytowanie zasobów jest znacznie prostsze i bardziej niezawodne niż w przypadku konieczności edytowania klas i metod. Za pomocą szablonów tekstowych można generować kod w taki sam sposób, jak w przypadku źródła własnego projektu.

 Szablon tekstowy zawiera kombinację tekstu, który ma zostać wygenerowany, i kod programu generujący zmienne części tekstu. Kod programu i umożliwia powtarzanie lub warunkowe pomijanie części wygenerowanego tekstu. Wygenerowany tekst może być kodem programu, który będzie częścią aplikacji.

## <a name="creating-a-design-time-t4-text-template"></a>Tworzenie szablonu tekstu T4 w czasie projektowania

#### <a name="to-create-a-design-time-t4-template-in-visual-studio"></a>Aby utworzyć szablon T4 w czasie projektowania w programie Visual Studio

1. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt lub Otwórz istniejący.

     Na przykład w menu **plik** wybierz polecenie **Nowy**, **projekt**.

2. Dodaj plik szablonu tekstu do projektu i nadaj mu nazwę, która ma rozszerzenie **. tt**.

     W tym celu w **Eksplorator rozwiązań**, w menu skrótów projektu, wybierz **Dodaj**, **nowy element**. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **szablon tekstowy** w środkowym okienku.

     Zwróć uwagę, że właściwość **niestandardowego narzędzia** pliku to **TextTemplatingFileGenerator**.

3. Otwórz ten plik. Zawiera już następujące dyrektywy:

    ```
    <#@ template hostspecific="false" language="C#" #>
    <#@ output extension=".txt" #>
    ```

     Jeśli szablon został dodany do [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu, atrybut Language będzie " `VB` ".

4. Dodaj tekst na końcu pliku. Na przykład:

    ```
    Hello, world!
    ```

5. Zapisz plik.

     Może zostać wyświetlone okno komunikatu z **ostrzeżeniem o zabezpieczeniach** z prośbą o potwierdzenie, że chcesz uruchomić szablon. Kliknij przycisk **OK**.

6. W **Eksplorator rozwiązań**rozwiń węzeł plik szablonu i znajdziesz plik z rozszerzeniem **txt**. Plik zawiera tekst wygenerowany na podstawie szablonu.

    > [!NOTE]
    > Jeśli projekt jest projektem Visual Basic, należy kliknąć przycisk **Pokaż wszystkie pliki** , aby wyświetlić plik wyjściowy.

### <a name="regenerating-the-code"></a>Ponowne generowanie kodu
 Szablon zostanie wykonany, generując plik pomocniczy w jednym z następujących przypadków:

- Edytuj szablon, a następnie zmień fokus na inne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okno.

- Zapisz szablon.

- Kliknij kolejno pozycje **Przekształć wszystkie szablony** w menu **kompilacja** . Spowoduje to przekształcenie wszystkich szablonów w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu.

- W **Eksplorator rozwiązań**, w menu skrótów dowolnego pliku, wybierz **Uruchom narzędzie niestandardowe**. Użyj tej metody, aby przekształcić wybrany podzestaw szablonów.

  Istnieje również możliwość skonfigurowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu, tak aby szablony były wykonywane, gdy pliki danych, które zostały przez nich odczytane, uległy zmianie. Aby uzyskać więcej informacji, zobacz Ponowne [generowanie kodu automatycznie](#Regenerating).

## <a name="generating-variable-text"></a>Generowanie tekstu zmiennej
 Szablony tekstowe umożliwiają użycie kodu programu w celu zróżnicowania zawartości wygenerowanego pliku.

#### <a name="to-generate-text-by-using-program-code"></a>Aby wygenerować tekst przy użyciu kodu programu

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

2. Zapisz plik. tt i ponownie Zbadaj wygenerowany plik txt. Wyświetla listę kwadratów liczb z przenoszącą od 0 do 10.

   Zauważ, że instrukcje są ujęte w nawiasy `<#...#>` i w obrębie `<#=...#>` . Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

   Jeśli napiszesz kod generujący w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , `template` dyrektywa powinna zawierać `language="VB"` . Wartość domyślna to `"C#"`.

## <a name="debugging-a-design-time-t4-text-template"></a>Debugowanie szablonu tekstu T4 w czasie projektowania
 Aby debugować szablon tekstowy:

- Wstaw `debug="true"` do `template` dyrektywy. Na przykład:

   `<#@ template debug="true" hostspecific="false" language="C#" #>`

- Ustaw punkty przerwania w szablonie w taki sam sposób, jak w przypadku zwykłego kodu.

- Wybierz **Debuguj szablon T4** z menu skrótów pliku szablonu tekstu w Eksplorator rozwiązań.

  Szablon zostanie uruchomiony i zatrzymany dla punktów przerwania. Można przeanalizować zmienne i krokowo przez kod w zwykły sposób.

> [!TIP]
> `debug="true"` sprawia, że wygenerowany kod mapuje się dokładniej do szablonu tekstu, wstawiając więcej dyrektyw numerowania wierszy do wygenerowanego kodu. Jeśli go opuścisz, punkty przerwania mogą przestać działać w nieprawidłowym stanie.
>
> Ale można pozostawić klauzulę w dyrektywie Template, nawet jeśli nie jest debugowana. Powoduje to, że jest to bardzo mały spadek wydajności.

## <a name="generating-code-or-resources-for-your-solution"></a>Generowanie kodu lub zasobów dla rozwiązania
 Istnieje możliwość generowania plików programu, które różnią się w zależności od modelu. Model to dane wejściowe, takie jak baza danych, plik konfiguracji, model UML, model DSL lub inne źródło. Zwykle generowane są kilka plików programów z tego samego modelu. Aby to osiągnąć, należy utworzyć plik szablonu dla każdego wygenerowanego pliku programu i wszystkie szablony odczytywać ten sam model.

#### <a name="to-generate-program-code-or-resources"></a>Aby wygenerować kod lub zasoby programu

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

    ```
    class MyGeneratedClass {
      private int P1 = 0;
      private int P2 = 0;
      private int P3 = 0;
    }
    ```

### <a name="generating-code-and-generated-text"></a>Generowanie kodu i wygenerowanego tekstu
 Podczas generowania kodu programu najważniejsze jest, aby uniknąć pomyłki generowanego kodu, który jest wykonywany w szablonie, oraz wygenerowanego kodu, który stał się częścią rozwiązania. Te dwa języki nie muszą być takie same.

 Poprzedni przykład ma dwie wersje. W jednej wersji kod generujący jest w języku C#. W innej wersji kod generujący jest Visual Basic. Ale tekst wygenerowany przez oba te elementy są takie same i jest klasą języka C#.

 W ten sam sposób można użyć [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonu do wygenerowania kodu w dowolnym języku. Wygenerowany tekst nie musi znajdować się w żadnym konkretnym języku i nie musi być kodem programu.

### <a name="structuring-text-templates"></a>Tworzenie struktury szablonów tekstowych
 W przypadku dobrych rozwiązań warto rozdzielić kod szablonu na dwie części:

- Konfiguracja lub część zbierania danych, która ustawia wartości w zmiennych, ale nie zawiera bloków tekstowych. W poprzednim przykładzie ta część jest inicjowana `properties` .

   Jest to czasami nazywane sekcją "model", ponieważ konstruuje model w sklepie i zwykle odczytuje plik modelu.

- Część służąca do generowania tekstu ( `foreach(...){...}` w przykładzie), która używa wartości zmiennych.

  Nie jest to konieczne separacja, ale jest to styl, który ułatwia odczytywanie szablonu przez zredukowanie złożoności części zawierającej tekst.

## <a name="reading-files-or-other-sources"></a>Odczytywanie plików lub innych źródeł
 Aby uzyskać dostęp do pliku modelu lub bazy danych, kod szablonu może używać zestawów, takich jak System.XML. Aby uzyskać dostęp do tych zestawów, należy wstawić dyrektywy takie jak następujące:

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.IO" #>
```

 `assembly`Dyrektywa sprawia, że określony zestaw jest dostępny dla kodu szablonu w taki sam sposób, jak sekcja References [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Nie trzeba dołączać odwołania do System.dll, które jest przywoływane automatycznie. `import`Dyrektywa pozwala używać typów bez użycia ich w pełni kwalifikowanych nazw w taki sam sposób jak w przypadku `using` dyrektywy w zwykłym pliku programu.

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
 Aby załadować plik z lokalizacji względem szablonu tekstu, można użyć `this.Host.ResolvePath()` . Do użycia. Host, należy ustawić `hostspecific="true"` w `template` :

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

 Można również użyć `this.Host.TemplateFile` , który identyfikuje nazwę bieżącego pliku szablonu.

 Typ `this.Host` (w języku VB `Me.Host` ) to `Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost` .

### <a name="getting-data-from-vsprvs"></a>Pobieranie danych z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 Aby skorzystać z usług oferowanych w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ustaw `hostSpecific` atrybut i Załaduj `EnvDTE` zestaw. Następnie można użyć IServiceProvider. GetCOMService (), aby uzyskać dostęp do DTE i innych usług. Na przykład:

```scr
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetCOMService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>

```

> [!TIP]
> Szablon tekstowy jest uruchamiany w jego własnej domenie aplikacji, a usługi są dostępne przez kierowanie. W takim przypadku GetCOMService () jest bardziej niezawodny niż GetService ().

## <a name="regenerating-the-code-automatically"></a><a name="Regenerating"></a> Automatyczne generowanie kodu
 Zazwyczaj kilka plików w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu jest generowanych z jednym modelem wejściowym. Każdy plik jest generowany na podstawie własnego szablonu, ale wszystkie szablony odwołują się do tego samego modelu.

 Jeśli model źródłowy ulegnie zmianie, należy uruchomić ponowne uruchomienie wszystkich szablonów w rozwiązaniu. Aby to zrobić ręcznie, wybierz pozycję **Przekształć wszystkie szablony** w menu **kompilacja** .

 Jeśli zainstalowano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestaw SDK wizualizacji i modelowania, wszystkie szablony są przekształcane automatycznie za każdym razem, gdy wykonujesz kompilację. W tym celu należy edytować plik projektu (. csproj lub. vbproj) w edytorze tekstów i dodać następujące wiersze blisko końca pliku po dowolnych innych `<import>` instrukcjach:

```
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v11.0\TextTemplating\Microsoft.TextTemplating.targets" />
<PropertyGroup>
   <TransformOnBuild>true</TransformOnBuild>
   <!-- Other properties can be inserted here -->
</PropertyGroup>
```

 Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).

## <a name="error-reporting"></a>Raportowanie błędów
 Aby umieścić komunikaty o błędach i ostrzeżeniach w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oknie błędów, można użyć następujących metod:

```
Error("An error message");
Warning("A warning message");
```

## <a name="converting-an-existing-file-to-a-template"></a><a name="Converting"></a> Konwertowanie istniejącego pliku na szablon
 Przydatną funkcją szablonów jest to, że wyglądają bardzo podobnie do generowanych przez nich plików wraz z niektórym wstawionym kodem programu. Sugeruje to przydatną metodę tworzenia szablonu. Najpierw utwórz zwykły plik jako prototyp, taki jak [!INCLUDE[csprcs](../includes/csprcs-md.md)] plik, a następnie stopniowo wprowadzaj kod generacji, który zmienia ten plik.

#### <a name="to-convert-an-existing-file-to-a-design-time-template"></a>Aby skonwertować istniejący plik na szablon czasu projektowania

1. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekcie Dodaj plik typu, który chcesz wygenerować, taki jak `.cs` `.vb` plik, lub `.resx` .

2. Przetestuj nowy plik, aby upewnić się, że działa.

3. W Eksplorator rozwiązań Zmień rozszerzenie nazwy pliku na **. tt**.

4. Sprawdź następujące właściwości pliku **TT** :

    |Właściwość|Wartość|
    |-|-|
    |**Niestandardowe narzędzie =**|**TextTemplatingFileGenerator**|
    |**Akcja kompilacji =**|**Brak**|

5. Wstaw następujące wiersze na początku pliku:

    ```
    <#@ template debug="false" hostspecific="false" language="C#" #>
    <#@ output extension=".cs" #>
    ```

     Jeśli chcesz napisać kod generujący szablon w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , ustaw `language` atrybut `"VB"` zamiast `"C#"` .

     Ustaw `extension` atrybut na rozszerzenie nazwy pliku dla typu pliku, który chcesz wygenerować, na przykład, `.cs` `.resx` lub `.xml` .

6. Zapisz plik.

     Tworzony jest plik pomocniczy z określonym rozszerzeniem. Jego właściwości są poprawne dla typu pliku. Na przykład właściwość **Akcja kompilacji** pliku CS zostanie **skompilowana**.

     Sprawdź, czy wygenerowany plik zawiera tę samą zawartość co oryginalny plik.

7. Zidentyfikuj część pliku, który ma być różny. Na przykład część, która pojawia się tylko pod pewnymi warunkami lub częścią, która jest powtarzana lub która różni się od konkretnych wartości. Wstaw kod generujący. Zapisz plik i sprawdź, czy plik pomocniczy został prawidłowo wygenerowany. Powtórz ten krok.

## <a name="guidelines-for-code-generation"></a>Wskazówki dotyczące generowania kodu
 Zapoznaj się z instrukcjami dotyczącymi [pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md).

## <a name="next-steps"></a>Następne kroki

|Następny krok|Temat|
|---------------|-----------|
|Pisanie i debugowanie bardziej zaawansowanego szablonu tekstu, z kodem korzystającym z funkcji pomocniczych, dołączonych plików i danych zewnętrznych.|[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)|
|Generuj dokumenty z szablonów w czasie wykonywania.|[Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)|
|Generowanie tekstu uruchamiania poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Przekształć dane w postaci języka specyficznego dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Napisz procesory dyrektywy, aby przekształcić własne źródła danych.|[Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)|

## <a name="see-also"></a>Zobacz też
 [Zalecenia dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)
