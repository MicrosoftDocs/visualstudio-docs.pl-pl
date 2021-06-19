---
title: Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4
description: Dowiedz się, jak generować ciągi tekstowe w aplikacji w czasie wykonywania przy użyciu Visual Studio tekstowych środowiska uruchomieniowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96d37bc586f9e8d6134377244c3181a52ec11a84
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387557"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4

Ciągi tekstowe w aplikacji można generować w czasie wykonywania przy użyciu Visual Studio tekstowych środowiska uruchomieniowego. Komputer, na którym jest wykonywana aplikacja, nie musi mieć Visual Studio. Szablony środowiska uruchomieniowego są czasami nazywane "wstępnie przetworzonymi szablonami tekstowym", ponieważ w czasie kompilacji szablon generuje kod wykonywany w czasie wykonywania.

Każdy szablon to połączenie tekstu, który będzie wyświetlany w wygenerowanym ciągu, i fragmentów kodu programu. Fragmenty programu dostarczają wartości dla zmiennych części ciągu, a także kontrolują części warunkowe i powtórzone.

Na przykład w aplikacji, która tworzy raport HTML, można użyć następującego szablonu.

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

Zwróć uwagę, że szablon jest stroną HTML, na której części zmiennych zostały zastąpione kodem programu. Projektowanie takiej strony można rozpocząć od napisania statycznego prototypu strony HTML. Następnie można zastąpić tabelę i inne części zmiennych kodem programu, który generuje zawartość, która różni się od jednej okazji.

Użycie szablonu w aplikacji ułatwia wyświetlanie ostatecznej formy danych wyjściowych, niż można by było użyć na przykład długiej serii instrukcji zapisu. Wprowadzenie zmian w postaci danych wyjściowych jest łatwiejsze i bardziej niezawodne.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Tworzenie Run-Time tekstowego w dowolnej aplikacji

### <a name="to-create-a-run-time-text-template"></a>Aby utworzyć szablon tekstowy czasu uruchamiania

1. W Eksplorator rozwiązań menu skrótów projektu wybierz pozycję **Dodaj**  >  **nowy element.**

2. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję Szablon **tekstowy środowiska uruchomieniowego**. (W Visual Basic w obszarze **Typowe elementy**  >  **Ogólne).**

3. Wpisz nazwę pliku szablonu.

    > [!NOTE]
    > Nazwa pliku szablonu będzie używana jako nazwa klasy w wygenerowanym kodzie. W związku z tym nie powinna mieć spacji ani znaków interpunkcji.

4. Wybierz **pozycję Dodaj.**

    Zostanie utworzony nowy plik z rozszerzeniem **.tt**. Jego **właściwość Narzędzia niestandardowego** jest ustawiona na **TextTemplatingFilePreprocessor**. Zawiera on następujące wiersze:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Konwertowanie istniejącego pliku na szablon Run-Time szablonu

Dobrym sposobem na utworzenie szablonu jest przekonwertowanie istniejącego przykładu danych wyjściowych. Jeśli na przykład aplikacja będzie generować pliki HTML, możesz rozpocząć od utworzenia zwykłego pliku HTML. Upewnij się, że działa prawidłowo i że jego wygląd jest poprawny. Następnie uwzględnij go w Visual Studio projektu i przekonwertuj go na szablon.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Aby przekonwertować istniejący plik tekstowy na szablon czasu uruchomienia

1. Dołącz plik do Visual Studio projektu. W Eksplorator rozwiązań menu skrótów projektu wybierz pozycję **Dodaj**  >  **istniejący element**.

2. Ustaw właściwość Narzędzia niestandardowe **pliku** na **wartość TextTemplatingFilePreprocessor**. W Eksplorator rozwiązań menu skrótów pliku wybierz pozycję **Właściwości**.

    > [!NOTE]
    > Jeśli właściwość jest już ustawiona, upewnij się, że jest to **właściwość TextTemplatingFilePreprocessor,** a nie **TextTemplatingFileGenerator.** Może się tak zdarzyć, jeśli dołączysz plik, który ma już rozszerzenie **.tt**.

3. Zmień rozszerzenie nazwy pliku na **.tt**. Chociaż ten krok jest opcjonalny, pomaga uniknąć otwierania pliku w nieprawidłowym edytorze.

4. Usuń wszelkie spacje lub znaki interpunktowe z głównej części nazwy pliku. Na przykład "Mój Page.tt sieci Web" będzie niepoprawny, ale "MyWebPage.tt" jest poprawne. Nazwa pliku będzie używana jako nazwa klasy w wygenerowanym kodzie.

5. Wstaw następujący wiersz na początku pliku. Jeśli pracujesz w projekcie Visual Basic, zastąp "C#" "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Zawartość szablonu Run-Time szablonu

### <a name="template-directive"></a>Dyrektywa template

Zachowaj pierwszy wiersz szablonu, tak jak podczas tworzenia pliku:

`<#@ template language="C#" #>`

Parametr language będzie zależeć od języka projektu.

### <a name="plain-content"></a>Zawartość w postaci zwykłego tekstu

Edytuj plik **tt,** aby zawierał tekst, który ma zostać wygenerowany przez aplikację. Na przykład:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Kod osadzonego programu

Kod programu można wstawiać między `<#` i `#>` . Na przykład:

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

Zwróć uwagę, że między wyrażeniami i są wstawiane instrukcje `<# ... #>` `<#= ... #>` . Aby uzyskać więcej informacji, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template"></a>Korzystanie z szablonu

### <a name="the-code-built-from-the-template"></a>Kod sbudowaną na podstawie szablonu

Po zapisaniu **pliku tt** zostanie wygenerowany pomocniczy plik **cs** **lub vb.** Aby wyświetlić ten plik w **Eksplorator rozwiązań**, rozwiń węzeł pliku **tt.** W projekcie Visual Basic najpierw wybierz pozycję **Pokaż wszystkie pliki** na pasku **Eksplorator rozwiązań** narzędzi.

Zwróć uwagę, że plik pomocniczy zawiera klasę częściową, która zawiera metodę o nazwie `TransformText()` . Tę metodę można wywołać z aplikacji.

### <a name="generating-text-at-run-time"></a>Generowanie tekstu w czasie uruchamiania

W kodzie aplikacji możesz wygenerować zawartość szablonu przy użyciu wywołania podobnego do tego:

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

Aby umieścić wygenerowaną klasę w określonej przestrzeni nazw, ustaw właściwość **Custom Tool Namespace** pliku szablonu tekstu.

### <a name="debugging-runtime-text-templates"></a>Debugowanie szablonów tekstowych środowiska uruchomieniowego

Debugowanie i testowanie szablonów tekstowych środowiska uruchomieniowego w taki sam sposób, jak w przypadku zwykłego kodu.

Punkt przerwania można ustawić w szablonie tekstowym. Jeśli uruchamiasz aplikację w trybie debugowania z Visual Studio, możesz przechodzić przez kod i oceniać wyrażenia wyrażeń zegarka w zwykły sposób.

### <a name="passing-parameters-in-the-constructor"></a>Przekazywanie parametrów w konstruktorze

Zazwyczaj szablon musi importować niektóre dane z innych części aplikacji. Aby to ułatwić, kod sbudowany przez szablon jest klasą częściową. Możesz utworzyć kolejną część tej samej klasy w innym pliku w projekcie. Ten plik może zawierać konstruktor z parametrami, właściwościami i funkcjami, do których można uzyskać dostęp zarówno za pomocą kodu osadzonego w szablonie, jak i przez pozostałą część aplikacji.

Można na przykład utworzyć oddzielny plik **MyWebPageCode.cs:**

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

W pliku szablonu **MyWebPage.tt**, możesz napisać:

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

#### <a name="constructor-parameters-in-visual-basic"></a>Parametry konstruktora w Visual Basic

W Visual Basic plik **MyWebPageCode.vb** zawiera:

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

Szablon można wywołać, przekazując parametr w konstruktorze:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Przekazywanie danych we właściwościach szablonu

Alternatywnym sposobem przekazywania danych do szablonu jest dodanie właściwości publicznych do klasy szablonu w definicji klasy częściowej. Aplikacja może ustawić właściwości przed wywołaniami `TransformText()` .

Możesz również dodać pola do klasy szablonu w częściowej definicji. Dzięki temu można przekazywać dane między kolejnymi wykonaniami szablonu.

### <a name="use-partial-classes-for-code"></a>Używanie klas częściowych dla kodu

Wielu deweloperów woli unikać pisania dużych ilości kodu w szablonach. Zamiast tego można zdefiniować metody w klasie częściowej, która ma taką samą nazwę jak plik szablonu. Wywołaj te metody z szablonu. W ten sposób szablon bardziej wyraźnie pokazuje, jak będzie wyglądać docelowy ciąg danych wyjściowych. Dyskusje dotyczące wyglądu wyniku można oddzielić od logiki tworzenia wyświetlanych danych.

### <a name="assemblies-and-references"></a>Zestawy i odwołania

Jeśli kod szablonu ma odwoływać się do zestawu .NET lub innego zestawu,  takiego **jakSystem.Xml.dll,** dodaj go do odwołania projektu w zwykły sposób.

Jeśli chcesz zaimportować przestrzeń nazw w taki sam sposób jak w przypadku instrukcji , możesz `using` to zrobić za pomocą dyrektywy `import` :

```
<#@ import namespace="System.Xml" #>
```

Te dyrektywy należy umieścić na początku pliku, bezpośrednio po `<#@template` dyrektywie .

### <a name="shared-content"></a>Zawartość udostępniona

Jeśli masz tekst udostępniony między kilkoma szablonami, możesz umieścić go w osobnym pliku i dołączyć do każdego pliku, w którym powinien się on pojawić:

```
<#@include file="CommonHeader.txt" #>
```

Uwzględniona zawartość może zawierać dowolną mieszankę kodu programu i zwykłego tekstu oraz może zawierać inne dyrektywy include i inne dyrektywy.

Dyrektywy include można używać w dowolnym miejscu w tekście pliku szablonu lub dołączonego pliku.

### <a name="inheritance-between-run-time-text-templates"></a>Dziedziczenie między Run-Time tekstowych

Zawartość między szablonami czasu uruchamiania można udostępniać, pisząc szablon klasy bazowej, który może być abstrakcyjny. Użyj `inherits` parametru dyrektywy `<@#template#>` , aby odwołać się do innej klasy szablonu środowiska uruchomieniowego.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Wzorzec dziedziczenia: fragmenty w metodach podstawowych

We wzorcu użytym w poniższym przykładzie zwróć uwagę na następujące kwestie:

- Klasa bazowa `SharedFragments` definiuje metody w blokach cech klasy `<#+ ... #>` .

- Klasa bazowa nie zawiera żadnego tekstu. Zamiast tego wszystkie jego bloki tekstowe występują wewnątrz metod cech klasy.

- Klasa pochodna wywołuje metody zdefiniowane w `SharedFragments` klasie .

- Aplikacja wywołuje `TextTransform()` metodę klasy pochodnej, ale nie przekształca klasy bazowej `SharedFragments` .

- Klasy bazowe i pochodne są szablonami tekstowym środowiska uruchomieniowego. oznacza to, że **właściwość Narzędzie niestandardowe** jest ustawiona na wartość **TextTemplatingFilePreprocessor**.

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

**Wynikowe dane wyjściowe:**

```
begin 1
    Shared Text 2
end 1
```

#### <a name="inheritance-pattern-text-in-base-body"></a>Wzorzec dziedziczenia: tekst w treści podstawowej

W tym alternatywnym podejściu do korzystania z dziedziczenia szablonu większość tekstu jest definiowana w szablonie bazowym. Szablony pochodne zawierają fragmenty danych i tekstu, które mieszczą się w zawartości podstawowej.

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

Szablony czasu projektowania: jeśli chcesz użyć szablonu do wygenerowania kodu, który staje się częścią aplikacji, zobacz [Design-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)(Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4).

Szablonów czasu uruchamiania można używać w dowolnej aplikacji, w której szablony i ich zawartość są określane w czasie kompilacji. Jeśli jednak chcesz napisać rozszerzenie Visual Studio, które generuje tekst z szablonów, które zmieniają się w czasie uruchamiania, zobacz Temat Wywołania przekształcenia tekstu w [rozszerzeniu programu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [Przybornik T4](http://olegsych.com/T4Toolbox/)
