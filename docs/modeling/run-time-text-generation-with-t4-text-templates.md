---
title: Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 344e15b69bf3e8308c62c6fa1074720b0cd7618d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520838"
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4

Można generować ciągi tekstowe w aplikacji w czasie wykonywania przy użyciu szablonów tekstowych środowiska uruchomieniowego programu Visual Studio. Komputer, na którym jest wykonywana aplikacja, nie musi mieć programu Visual Studio. Szablony środowiska uruchomieniowego są czasami nazywane "wstępnie przetworzonymi szablonami tekstu", ponieważ w czasie kompilacji szablon generuje kod, który jest wykonywany w czasie wykonywania.

Każdy szablon jest mieszaniną tekstu, tak jak będzie wyświetlana w wygenerowanym ciągu, i fragmentów kodu programu. Fragmenty programu przekazują wartości dla zmiennych części ciągu, a także kontrolują elementy warunkowe i powtarzalne.

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

Zwróć uwagę, że szablon jest stroną HTML, w której części zmiennych zostały zamienione na kod programu. Możesz rozpocząć projekt takiej strony, pisząc statyczny prototyp strony HTML. Następnie można zamienić tabelę i inne części zmiennych na kod programu generujący zawartość, która różni się od jednej okazji do następnego.

Użycie szablonu w aplikacji sprawia, że można łatwiej zobaczyć ostateczną postać danych wyjściowych niż na przykład długa seria instrukcji Write. Wprowadzanie zmian w formularzu danych wyjściowych jest łatwiejsze i bardziej niezawodne.

## <a name="creating-a-run-time-text-template-in-any-application"></a>Tworzenie szablonu tekstu w czasie wykonywania w dowolnej aplikacji

### <a name="to-create-a-run-time-text-template"></a>Aby utworzyć szablon tekstu czasu wykonywania

1. W Eksplorator rozwiązań, w menu skrótów projektu, wybierz polecenie **Dodaj**  >  **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **szablon tekstu środowiska uruchomieniowego**. (W Visual Basic poszukaj w obszarze **wspólne elementy**  >  **Ogólne**).

3. Wpisz nazwę pliku szablonu.

    > [!NOTE]
    > Nazwa pliku szablonu zostanie użyta jako nazwa klasy w wygenerowanym kodzie. W związku z tym nie powinna zawierać spacji ani znaków interpunkcyjnych.

4. Wybierz pozycję **Dodaj**.

    Tworzony jest nowy plik z rozszerzeniem **TT**. Właściwość **niestandardowego narzędzia** jest ustawiona na **TextTemplatingFilePreprocessor**. Zawiera następujące wiersze:

    ```
    <#@ template language="C#" #>
    <#@ assembly name="System.Core" #>
    <#@ import namespace="System.Linq" #>
    <#@ import namespace="System.Text" #>
    <#@ import namespace="System.Collections.Generic" #>
    ```

## <a name="converting-an-existing-file-to-a-run-time-template"></a>Konwertowanie istniejącego pliku na szablon czasu wykonywania

Dobrym sposobem na utworzenie szablonu jest przekonwertowanie istniejącego przykładu danych wyjściowych. Na przykład, jeśli aplikacja będzie generować pliki HTML, możesz zacząć od utworzenia zwykłego pliku HTML. Upewnij się, że działa prawidłowo i że jego wygląd jest poprawny. Następnie Uwzględnij je w projekcie programu Visual Studio i Konwertuj go na szablon.

### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Aby skonwertować istniejący plik tekstowy na szablon czasu wykonywania

1. Dołącz plik do projektu programu Visual Studio. W Eksplorator rozwiązań, w menu skrótów projektu, wybierz **Dodaj**  >  **istniejący element**.

2. Ustaw właściwość **niestandardowych narzędzi** pliku na **TextTemplatingFilePreprocessor**. W Eksplorator rozwiązań, w menu skrótów pliku, wybierz **Właściwości**.

    > [!NOTE]
    > Jeśli właściwość jest już ustawiona, upewnij się, że jest **TextTemplatingFilePreprocessor** , a nie **TextTemplatingFileGenerator**. Taka sytuacja może wystąpić, jeśli dołączysz plik, który ma już rozszerzenie **. tt**.

3. Zmień rozszerzenie nazwy pliku **TT**. Mimo że ten krok jest opcjonalny, ułatwia to uniknięcie otwierania pliku w nieprawidłowym edytorze.

4. Usuń wszystkie spacje lub znaki interpunkcyjne z głównej części nazwy pliku. Na przykład "My Web Page.tt" może być niepoprawna, ale wartość "MyWebPage.tt" jest poprawna. Nazwa pliku zostanie użyta jako nazwa klasy w wygenerowanym kodzie.

5. Wstaw poniższy wiersz na początku pliku. Jeśli pracujesz w projekcie Visual Basic, Zamień "C#" na "VB".

    `<#@ template language="C#" #>`

## <a name="the-content-of-the-run-time-template"></a>Zawartość szablonu czasu wykonywania

### <a name="template-directive"></a>Szablon — dyrektywa

Zachowaj pierwszy wiersz szablonu, tak jak podczas tworzenia pliku:

`<#@ template language="C#" #>`

Parametr Language będzie zależeć od języka projektu.

### <a name="plain-content"></a>Zwykła zawartość

Edytuj plik **TT** , aby zawierał tekst, który ma być generowany przez aplikację. Na przykład:

```html
<html><body>
<h1>Sales for January</h2>
<!-- table to be inserted here -->
This report is Company Confidential.
</body></html>
```

### <a name="embedded-program-code"></a>Osadzony kod programu

Można wstawić kod programu między `<#` i `#>` . Na przykład:

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

Zauważ, że instrukcje są wstawiane między `<# ... #>` wyrażeniami i między `<#= ... #>` . Aby uzyskać więcej informacji, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-template"></a>Korzystanie z szablonu

### <a name="the-code-built-from-the-template"></a>Kod skompilowany na podstawie szablonu

Podczas zapisywania pliku **. tt** zostanie wygenerowany plik. **CS** lub **. vb** . Aby wyświetlić ten plik w **Eksplorator rozwiązań**, rozwiń węzeł plik **. tt** . W projekcie Visual Basic najpierw wybierz opcję **Pokaż wszystkie pliki** na pasku narzędzi **Eksplorator rozwiązań** .

Należy zauważyć, że plik pomocniczy zawiera klasę częściową, która zawiera metodę o nazwie `TransformText()` . Tę metodę można wywołać z poziomu aplikacji.

### <a name="generating-text-at-run-time"></a>Generowanie tekstu w czasie wykonywania

W kodzie aplikacji można wygenerować zawartość szablonu przy użyciu wywołania w następujący sposób:

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

Aby umieścić wygenerowaną klasę w konkretnym obszarze nazw, ustaw właściwość **przestrzeń nazw narzędzia niestandardowego** pliku szablonu tekstu.

### <a name="debugging-runtime-text-templates"></a>Debugowanie szablonów tekstowych środowiska uruchomieniowego

Debugowanie i testowanie szablonów tekstu środowiska uruchomieniowego w taki sam sposób jak zwykły kod.

Punkt przerwania można ustawić w szablonie tekstowym. Jeśli uruchomisz aplikację w trybie debugowania z programu Visual Studio, możesz przewinąć kod i oszacować wyrażenia czujki w zwykły sposób.

### <a name="passing-parameters-in-the-constructor"></a>Przekazywanie parametrów w konstruktorze

Zwykle szablon musi importować niektóre dane z innych części aplikacji. Aby to ułatwić, kod skompilowany przez szablon jest klasą częściową. Można utworzyć inną część tej samej klasy w innym pliku w projekcie. Ten plik może zawierać konstruktora z parametrami, właściwościami i funkcjami, do których można uzyskać dostęp w kodzie, który jest osadzony w szablonie, i przez resztę aplikacji.

Na przykład można utworzyć oddzielny plik **MyWebPageCode.cs**:

```csharp
partial class MyWebPage
{
    private MyData m_data;
    public MyWebPage(MyData data) { this.m_data = data; }}
```

W pliku szablonu **MyWebPage.tt**można napisać:

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

W Visual Basic osobnym pliku **MyWebPageCode. vb** zawiera:

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

Szablon może być wywoływany przez przekazanie parametru w konstruktorze:

```vb
Dim data = New My.Templates.MyData
    ' Add data values here ....
Dim page = New My.Templates.MyWebPage(data)
Dim pageContent = page.TransformText()
System.IO.File.WriteAllText("outputPage.html", pageContent)
```

#### <a name="passing-data-in-template-properties"></a>Przekazywanie danych we właściwościach szablonu

Alternatywny sposób przekazywania danych do szablonu polega na dodaniu właściwości publicznych do klasy szablonu w definicji klasy częściowej. Aplikacja może ustawić właściwości przed wywołaniem `TransformText()` .

Możesz również dodać pola do klasy Template w definicji częściowej. Dzięki temu można przekazać dane między kolejnymi wykonaniami szablonu.

### <a name="use-partial-classes-for-code"></a>Użyj klas częściowych dla kodu

Wielu deweloperów woli uniknąć pisania dużych treści kodu w szablonach. Zamiast tego można definiować metody w klasie częściowej, która ma taką samą nazwę jak plik szablonu. Wywołaj te metody z szablonu. W ten sposób szablon pokazuje dokładniej, jak będzie wyglądać docelowy ciąg wyjściowy. Dyskusje na temat wyglądu wyniku można oddzielić od logiki tworzenia wyświetlanych danych.

### <a name="assemblies-and-references"></a>Zestawy i odwołania

Jeśli chcesz, aby kod szablonu odwoływał się do platformy .NET lub innego zestawu, takiego jak **System.Xml.dll**, Dodaj go do **odwołań** projektu w zwykły sposób.

Jeśli chcesz zaimportować przestrzeń nazw w taki sam sposób jak w przypadku `using` instrukcji, możesz to zrobić za pomocą `import` dyrektywy:

```
<#@ import namespace="System.Xml" #>
```

Dyrektywy te należy umieścić na początku pliku bezpośrednio po `<#@template` dyrektywie.

### <a name="shared-content"></a>Udostępniona zawartość

Jeśli masz tekst współużytkowany przez kilka szablonów, możesz go umieścić w osobnym pliku i uwzględnić go w każdym pliku, w którym powinien wyglądać:

```
<#@include file="CommonHeader.txt" #>
```

Dołączona zawartość może zawierać dowolną kombinację kodu programu i zwykłego tekstu oraz może zawierać inne dyrektywy include i inne dyrektywy.

Dyrektywy include można użyć w dowolnym miejscu tekstu pliku szablonu lub w dołączonym pliku.

### <a name="inheritance-between-run-time-text-templates"></a>Dziedziczenie między szablonami tekstu w czasie wykonywania

Zawartość między szablonami czasu wykonywania można udostępnić, pisząc szablon klasy bazowej, który może być abstrakcyjny. Użyj `inherits` parametru `<@#template#>` dyrektywy, aby odwołać się do innej klasy szablonu środowiska uruchomieniowego.

#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Wzorzec dziedziczenia: fragmenty w metodach podstawowych

W wzorcu używanym w poniższym przykładzie Zwróć uwagę na następujące kwestie:

- Klasa bazowa `SharedFragments` definiuje metody w blokach funkcji klasy `<#+ ... #>` .

- Klasa bazowa nie zawiera żadnego wolnego tekstu. Zamiast tego wszystkie bloki tekstu występują w metodach klasy.

- Klasa pochodna wywołuje metody zdefiniowane w `SharedFragments` .

- Aplikacja wywołuje `TextTransform()` metodę klasy pochodnej, ale nie przekształca klasy bazowej `SharedFragments` .

- Podstawowa i pochodna klasy są szablonami tekstowymi środowiska uruchomieniowego; oznacza to, że właściwość **Narzędzia niestandardowego** jest ustawiona na **TextTemplatingFilePreprocessor**.

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

#### <a name="inheritance-pattern-text-in-base-body"></a>Wzorzec dziedziczenia: tekst w podstawowej treści

W tym alternatywnym podejściu do używania dziedziczenia szablonów, zbiorczo tekst jest zdefiniowany w szablonie podstawowym. Szablony pochodne zapewniają dane i fragmenty tekstu mieszczące się w zawartości podstawowej.

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

Szablony czasu projektowania: Jeśli chcesz użyć szablonu, aby wygenerować kod, który będzie częścią aplikacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Szablony czasu wykonywania można używać w dowolnej aplikacji, w której szablony i ich zawartość są określane w czasie kompilacji. Jeśli jednak chcesz napisać rozszerzenie programu Visual Studio, które generuje tekst z szablonów, które zmieniają się w czasie wykonywania, zobacz [Wywoływanie transformacji tekstu w rozszerzeniu programu vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
- [Przybornik T4](http://olegsych.com/T4Toolbox/)
