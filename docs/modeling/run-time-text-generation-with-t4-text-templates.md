---
title: Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 050af194c9fbdcabf99a880a0e9c5c4bf8913a3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946171"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4

Ciągi tekstowe można wygenerować w aplikacji w czasie wykonywania przy użyciu szablonów tekstowych środowiska uruchomieniowego programu Visual Studio. Komputer, na którym aplikacja wykonuje ma program Visual Studio. Środowisko uruchomieniowe szablony są czasami nazywane "wstępnie przetworzonych szablonów tekstowych" ponieważ w czasie kompilacji, szablon generuje kod, który jest wykonywany w czasie wykonywania.

Każdy szablon jest kombinację tekstu, która będzie wyświetlana w wygenerowanym ciągu i fragmenty kodu programu. Fragmenty program Podaj wartości dla zmiennej części ciągu, a także kontrolować sposób Warunkowość oraz części.

Na przykład następujący szablon może służyć w aplikacji, która tworzy raport HTML.

```html
<#@ template language="C#" #>
<html><body>
<h1>Sales for Previous Month</h2>
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
This report is Company Confidential.
</body></html>
```

Należy zauważyć, że szablon jest stroną HTML, w którym zostały zastąpione zmiennej części kodu programu. Można rozpocząć projektu strony sieci, pisząc prototyp statycznej strony HTML. W tabeli i innymi częściami zmiennej można następnie zastąpić za pomocą kodu programu, który generuje zawartości, która różni się z rozwiązaniem do następnego.

Przy użyciu szablonu w Twojej aplikacji sprawia, że łatwiej jest zobaczyć ostatecznej postaci w danych wyjściowych, nie można wykonać następujące akcje w, na przykład długiego szeregu instrukcje zapisu. Zmiany wprowadzone w formie danych wyjściowych jest łatwiejsze i bardziej niezawodne.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Tworzenie szablonu tekstu czasu wykonywania w dowolnej aplikacji

### <a name="to-create-a-run-time-text-template"></a>Aby utworzyć szablon tekstowy czasu wykonywania

1. W Eksploratorze rozwiązań w menu skrótów projektu wybierz **Dodaj** > **nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **szablonie tekstowym czasu wykonywania**. (W języku Visual Basic, sprawdź w obszarze **wspólne elementy** > **ogólne**.)

3. Wpisz nazwę dla pliku szablonu.

    > [!NOTE]
    > Nazwa pliku szablonu będzie służyć jako nazwy klasy w wygenerowanym kodzie. W związku z tym nie powinna ona mieć spacji i znaków przestankowych.

4. Wybierz **Dodaj**.

    Tworzony jest nowy plik, który ma rozszerzenie **.tt**. Jego **narzędzie niestandardowe** właściwość jest ustawiona na **TextTemplatingFilePreprocessor**. Zawiera następujące wiersze:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Konwertowanie istniejącego pliku na szablon czasu wykonywania

Dobrym sposobem, aby utworzyć szablon jest do konwersji istniejących przykładowe dane wyjściowe. Na przykład jeśli aplikacja generuje pliki HTML, można uruchomić, tworząc zwykły plik HTML. Upewnij się, że działa prawidłowo i czy jego wygląd jest poprawna. Następnie Uwzględnij ją w projekcie programu Visual Studio i przekonwertować go do szablonu.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Aby przekonwertować istniejącego pliku tekstowego szablon czasu wykonywania

1. Dołącz plik do projektu programu Visual Studio. W Eksploratorze rozwiązań w menu skrótów projektu, wybierz **Dodaj** > **istniejący element**.

2. Ustaw plik **narzędzia niestandardowe** właściwości **TextTemplatingFilePreprocessor**. W Eksploratorze rozwiązań w menu skrótów pliku, wybierz **właściwości**.

    > [!NOTE]
    > Jeśli właściwość została już ustawiona, upewnij się, że jest **TextTemplatingFilePreprocessor** i nie **TextTemplatingFileGenerator**. Może się to zdarzyć, jeśli dołączyć plik, który ma już rozszerzenie **.tt**.

3. Zmień rozszerzenie nazwy pliku **.tt**. Mimo że ten krok jest opcjonalny, pomaga uniknąć, otwierając plik w edytorze niepoprawne.

4. Usuń wszelkie spacje lub znaki interpunkcyjne z głównej części nazwy pliku. Na przykład "Moje Page.tt sieci Web" jest nieprawidłowa, ale "MyWebPage.tt" jest prawidłowa. Nazwa pliku będzie służyć jako nazwy klasy w wygenerowanym kodzie.

5. Wstaw następujący wiersz na początku pliku. Jeśli pracujesz w projekcie Visual Basic, zastąp "C#" z "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Zawartość szablonu środowiska wykonawczego

### <a name="template-directive"></a>— Dyrektywa szablonu

Pierwszy wiersz szablonu należy pamiętać, jak podczas tworzenia pliku:

`<#@ template language="C#" #>`

Parametr języka będzie zależeć od języka projektu.

### <a name="plain-content"></a>Zwykły zawartości

Edytuj **.tt** plik zawiera tekst, który ma aplikację w celu wygenerowania. Na przykład:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Osadzony kod programów

Możesz wstawić kod programu między `<#` i `#>`. Na przykład:

```csharp
<table>
    <# for (int i = 1; i <= 10; i++)
       { #>
         <tr><td>Test name <#= i #> </td>
             <td>Test value <#= i * i #> </td> </tr>
    <# } #>
 </table>
```

```vb
<table>
<#
    For i As Integer = 1 To 10
#>
    <tr><td>Test name <#= i #> </td>
      <td>Test value <#= i*i #> </td></tr>
<#
    Next
#>
</table>
```

Należy zauważyć, że instrukcje zostały wstawione między `<# ... #>` i wyrażenia są wstawiane `<#= ... #>`. Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Przy użyciu szablonu

### <a name="the-code-built-from-the-template"></a>Kod utworzony na podstawie szablonu

Podczas zapisywania **.tt** pliku, podmiot zależny firmy **.cs** lub **.vb** generowany jest plik. Aby wyświetlić ten plik w **Eksploratora rozwiązań**, rozwiń węzeł **.tt** węzła pliku. W projekcie języka Visual Basic, należy najpierw wybrać **Pokaż wszystkie pliki** w **Eksploratora rozwiązań** paska narzędzi.

Zwróć uwagę, że pomocniczy plik zawiera częściową klasą, która zawiera metodę o nazwie `TransformText()`. Tę metodę można wywołać z aplikacji.

### <a name="generating-text-at-run-time"></a>Generowanie tekstu w czasie wykonywania

W kodzie aplikacji, można wygenerować zawartość szablonu przy użyciu wywołania w następujący sposób:

```csharp
MyWebPage page = new MyWebPage();
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

```vb
Dim page = New My.Templates.MyWebPage
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

Aby umieścić wygenerowanej klasy w określonej przestrzeni nazw, należy ustawić **niestandardowe narzędzie Namespace** właściwości pliku szablonu tekstu.

### <a name="debugging-runtime-text-templates"></a>Debugowanie szablony tekstowe czasu wykonywania

Debugowanie i testowanie szablony tekstowe czasu wykonywania w taki sam sposób jak zwykłym kodem.

Możesz ustawić punkt przerwania w szablonie tekstu. Jeśli aplikacja jest uruchomiona w trybie debugowania w programie Visual Studio, można przejść przez kod i ocenić Czujka wyrażeń w zwykły sposób.

### <a name="passing-parameters-in-the-constructor"></a>Przekazywanie parametrów w Konstruktorze

Zazwyczaj szablonu należy zaimportować dane z innych części aplikacji. Aby to proste, kodu utworzonego przez szablon jest klasy częściowej. Możesz utworzyć inną częścią tej samej klasie w innym pliku w projekcie. Ten plik może zawierać konstruktora z parametrami, właściwości i funkcje, które są dostępne zarówno przez kod, który jest osadzony w szablonie, a przez pozostałe części aplikacji.

Na przykład można utworzyć osobny plik **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

W pliku szablonu **MyWebPage.tt**, można napisać:

```html
<h2>Sales figures</h2>
<table>
<# foreach (MyDataItem item in m_data.Items)
   // m_data is declared in MyWebPageCode.cs
   { #>
      <tr><td> <#= item.Name #> </td>
          <td> <#= item.Value #> </td></tr>
<# } // end of foreach
#>
</table>
```

Aby użyć tego szablonu w aplikacji:

```csharp
MyData data = ...;
MyWebPage page = new MyWebPage(data);
String pageContent = page.TransformText();
System.IO.File.WriteAllText("outputPage.html", pageContent);
```

#### <a name="constructor-parameters-in-visual-basic"></a>Parametry Konstruktora w języku Visual Basic

W języku Visual Basic, oddzielnym pliku **MyWebPageCode.vb** zawiera:

```vb
Namespace My.Templates
  Partial Public Class MyWebPage
    Private m_data As MyData
    Public Sub New(ByVal data As MyData)
      m_data = data
    End Sub
  End Class
End Namespace
```

Plik szablonu może zawierać:

```html
<#@ template language="VB" #>
<html><body>
<h1>Sales for January</h2>
<table>
<#
    For Each item In m_data.Items
#>
    <tr><td>Test name <#= item.Name #> </td>
      <td>Test value <#= item.Value #> </td></tr>
<#
    Next
#>
</table>
This report is Company Confidential.
</body></html>
```

Szablon może być wywoływany przez przekazanie parametr w Konstruktorze:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Przekazywanie danych we właściwościach szablonu

Alternatywny sposób przekazywanie danych do szablonu jest można dodać właściwości publiczne klasy szablonu w definicji klasy częściowej. Aplikację można ustawić właściwości przed wywołaniem `TransformText()`.

Można również dodać pola do klasy szablonu w definicji częściowej. Dzięki temu można przekazać dane między kolejnymi wykonaniami szablonu.

### <a name="use-partial-classes-for-code"></a>Używaj częściowe klasy dla kodu

Wielu programistów chce unikać pisania treści dużych kodu w szablonach. Zamiast tego można zdefiniować metody w klasie częściowej, który ma taką samą nazwę jak plik szablonu. Wywoływanie tych metod z szablonu. W ten sposób pokazuje szablonu więcej wyraźnie jakie docelowego ciągu danych wyjściowych będzie wyglądać. Dyskusje na temat wyglądu wyniki mogą być oddzielone od logiki, tworzenia danych, który jest wyświetlany.

### <a name="assemblies-and-references"></a>Zespoły i odwołania

Jeśli chcesz, aby kod szablonu do odwołania .NET lub innych zestawów, takich jak **System.Xml.dll**, dodaj go do swojego projektu **odwołania** w zwykły sposób.

Jeśli chcesz zaimportować przestrzeni nazw w taki sam sposób jak `using` instrukcji, można to zrobić za pomocą `import` dyrektywy:

```
<#@ import namespace="System.Xml" #>
```

Te dyrektywy muszą być umieszczone na początku pliku, natychmiast po `<#@template` dyrektywy.

### <a name="shared-content"></a>Zawartość udostępniona

Jeśli masz tekst, który jest udostępniany między kilka szablonów, można umieścić w oddzielnym pliku i dołączyć go w każdym pliku, w którym powinna zostać wyświetlona:

```
<#@include file="CommonHeader.txt" #>
```

Dołączona zawartość może zawierać kombinację kodu programu i zwykły tekst i może zawierać inne dołącza dyrektywę i inne dyrektywy.

Dyrektywa include można używanych w dowolnym miejscu w tekście pliku szablonu lub pliku dołączanym.

### <a name="inheritance-between-run-time-text-templates"></a>Dziedziczenia między szablonami tekstu czasu wykonywania

Możesz udostępnić zawartości między szablonów czasu wykonywania, pisząc szablonu klasy bazowej, które mogą być abstrakcyjne. Użyj `inherits` parametru `<@#template#>` dyrektywy, aby odwoływać się do innej klasy szablonu środowiska uruchomieniowego.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Wzorzec dziedziczenia: Fragmenty w metod bazowych

We wzorcu używanych w przykładzie poniżej Zwróć uwagę następujące kwestie:

- Klasa bazowa `SharedFragments` definiuje metody w ramach bloki cech klas `<#+ ... #>`.

- Klasa bazowa nie zawiera bezpłatny tekstu. Zamiast tego wszystkie jego bloki tekstu występować wewnątrz metody funkcji klasy.

- Klasy pochodnej wywołuje metody zdefiniowane w `SharedFragments`.

- Wywołania aplikacji `TextTransform()` metody klasy pochodnej, ale nie przekształca klasy bazowej `SharedFragments`.

- Klasy podstawowe i pochodne są szablony tekstowe czasu wykonywania; oznacza to, że **narzędzie niestandardowe** właściwość jest ustawiona na **TextTemplatingFilePreprocessor**.

**SharedFragments.tt:**

```
<#@ template language="C#" #>
<#+
protected void SharedText(int n)
{
#>
   Shared Text <#= n #>
<#+
}
// Insert more methods here if required.
#>
```

**MyTextTemplate1.tt:**

```
<#@ template language="C#" inherits="SharedFragments" #>
begin 1
   <# SharedText(2); #>
end 1
```

**MyProgram.cs:**

```csharp
...
MyTextTemplate1 t1  = new MyTextTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Dane wyjściowe:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Wzorzec dziedziczenia: Tekst podstawowy treści

W tym o innym podejściu do przy użyciu szablonu dziedziczenia duża część tekstu jest zdefiniowana w szablonie podstawowym. Pochodne szablony zawierają dane i fragmentów tekstu, który mieści się w podstawowej zawartości.

**AbstractBaseTemplate1.tt:**

```
<#@ template language="C#" #>

Here is the description for this derived template:
  <#= this.Description #>

Here is the fragment specific to this derived template:
<#
  this.PushIndent("  ");
  SpecificFragment(42);
  this.PopIndent();
#>
End of common template.
<#+
  // State set by derived class before calling TextTransform:
  protected string Description = "";
  // 'abstract' method to be defined in derived classes:
  protected virtual void SpecificFragment(int n) { }
#>
```

**DerivedTemplate1.tt:**

```
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>
<#
  // Set the base template properties:
  base.Description = "Description for this derived class";

  // Run the base template:
  base.TransformText();

#>
End material for DerivedTemplate1.

<#+
// Provide a fragment specific to this derived template:

protected override void SpecificFragment(int n)
{
#>
   Specific to DerivedTemplate1 : <#= n #>
<#+
}
#>
```

**Kod aplikacji:**

```csharp
...
DerivedTemplate1 t1 = new DerivedTemplate1();
string result = t1.TransformText();
Console.WriteLine(result);
```

**Dane wyjściowe:**

```
Here is the description for this derived template:
  Description for this derived class

Here is the fragment specific to this derived template:
     Specific to DerivedTemplate1 : 42
End of common template.
End material for DerivedTemplate1.
```

## <a name="related-topics"></a>Tematy pokrewne

Szablonów czasu projektowania: Jeśli chcesz użyć szablonu, aby wygenerować kod stanie się częścią Twojej aplikacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Szablony czasu wykonywania mogą być używane w dowolnej aplikacji, w których szablonach a ich zawartość są określane w czasie kompilacji. Ale jeśli chcesz zapisać rozszerzenia programu Visual Studio, która generuje tekst za pomocą szablonów, które zmieniają się w czasie wykonywania, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [Przybornik T4](http://olegsych.com/T4Toolbox/)
