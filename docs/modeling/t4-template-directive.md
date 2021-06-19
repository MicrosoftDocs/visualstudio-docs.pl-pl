---
title: Dyrektywa T4 dotycząca szablonu
description: Dowiedz się, Visual Studio szablon tekstowy T4 zazwyczaj rozpoczyna się od dyrektywy szablonu, która określa sposób przetwarzania szablonu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 622a6392df2608048a3ac24fda0f4dffc8e43dd4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386140"
---
# <a name="t4-template-directive"></a>Dyrektywa T4 dotycząca szablonu

Szablon Visual Studio T4 zazwyczaj rozpoczyna się od dyrektywy , która określa sposób `template` przetwarzania szablonu. Powinna istnieć nie więcej niż jedna dyrektywa szablonu w szablonie tekstowym i wszystkich plikach, które on uwzględnia.

Aby uzyskać ogólne omówienie pisania szablonów tekstowych, zobacz [Writing a T4 Text Template (Pisanie szablonu tekstowego T4).](../modeling/writing-a-t4-text-template.md)

## <a name="using-the-template-directive"></a>Używanie dyrektywy Template

```
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>
```

Dyrektywa `template` ma kilka atrybutów, które umożliwiają określenie różnych aspektów przekształcenia. Wszystkie atrybuty są opcjonalne.

## <a name="compileroptions-attribute"></a>Atrybut compilerOptions

Przykład:

`compilerOptions="optimize+"`

Prawidłowe wartości:

Wszystkie prawidłowe opcje kompilatora.

Ignorowane dla szablonów w czasie wykonywania (wstępnie przetworzonych).

Te opcje są stosowane, gdy szablon został przekonwertowany na lub , a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] wynikowy kod jest kompilowany.

## <a name="culture-attribute"></a>Atrybut culture

Przykład:

`culture="de-CH"`

Prawidłowe wartości:

"", niezmienna kultura, co jest ustawieniem domyślnym.

Kultura jest wyrażona jako ciąg w postaci xx-XX. Na przykład en-US, ja-JP, de-CH, de-DE. Aby uzyskać więcej informacji, zobacz <xref:System.Globalization.CultureInfo?displayProperty=fullName>.

Atrybut culture określa kulturę, jaka ma zostać użyta w przypadku konwersji bloku wyrażenia na tekst.

## <a name="debug-attribute"></a>Atrybut debug

Przykład:

```
debug="true"
```

Prawidłowe wartości:

`true`

`false` (ustawienie domyślne)

Jeśli atrybut ma wartość , plik kodu pośredniego będzie zawierać informacje umożliwiające debugerowi bardziej precyzyjne zidentyfikowanie pozycji w szablonie, w której `debug` `true` wystąpił podział lub wyjątek.

W przypadku szablonów czasu projektowania plik kodu pośredniego zostanie zapisany w **katalogu %TEMP%.**

Aby uruchomić szablon czasu projektowania w debugerze, zapisz szablon tekstowy, a następnie otwórz menu skrótów szablonu tekstu w programie Eksplorator rozwiązań i wybierz pozycję **Debuguj szablon T4.**

## <a name="hostspecific-attribute"></a>Atrybut hostspecific

Przykład:

```
hostspecific="true"
```

Prawidłowe wartości:

`true`

`false` (ustawienie domyślne)

`trueFromBase`

Jeśli ustawisz wartość tego atrybutu na , właściwość o nazwie zostanie dodana do `true` `Host` klasy wygenerowanej przez szablon tekstowy. Właściwość jest odwołaniem do hosta aparatu przekształcania i jest zadeklarowana jako [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110)). Jeśli został zdefiniowany niestandardowy host, można go rzutować na niestandardowy typ hosta.

Ponieważ typ tej właściwości zależy od typu hosta, jest to przydatne wyłącznie podczas pisania szablonu tekstu, który działa tylko z określonym hostem. Ma zastosowanie do szablonów [czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ale nie szablonów [czasu uruchamiania.](../modeling/run-time-text-generation-with-t4-text-templates.md)

Gdy jest, a używasz Visual Studio, możesz rzutować na `hostspecific` `true` `this.Host` IServiceProvider, aby uzyskać dostęp do Visual Studio funkcji. Można również użyć `Host.ResolvePath(filename)` funkcji , aby uzyskać ścieżkę bezwzględną pliku w projekcie. Na przykład:

```csharp
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#@ import namespace="System.IO" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<# // Get the Visual Studio API as a service:
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

<#
 // Find a path within the current project:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>
```

Jeśli używasz jednocześnie atrybutów i , określ `inherits` host="trueFromBase" w klasie pochodnej i `hostspecific` host="true" w klasie bazowej. Pozwala to uniknąć podwójnej definicji `Host` właściwości w wygenerowanym kodzie.

## <a name="language-attribute"></a>Atrybut language

Przykład:

`language="VB"`

Prawidłowe wartości:

`C#` (ustawienie domyślne)

`VB`

Atrybut określa język ( lub ), który ma być używany dla kodu `language` [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] źródłowego w blokach instrukcji i wyrażeń. Pliku kodu pośredniego, z którego jest generowane wyjście, użyje tego języka. Język ten nie jest powiązany z językiem generowanym przez szablon, który może być dowolnym rodzajem tekstu.

Na przykład:

```vb
<#@ template language="VB" #>
<#@ output extension=".txt" #>
Squares of numbers:
<#
  Dim number As Integer
  For number = 1 To 4
#>
  Square of <#= number #> is <#= number * number #>
<#
  Next number
#>
```

## <a name="inherits-attribute"></a>Atrybut inherits

Można określić, aby kod szablonu dziedziczył z innej klasy, która również może być generowana z szablonu tekstu.

### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Dziedziczenie w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym)

Można użyć dziedziczenia między szablonami tekstowymi czasu wykonywania, aby utworzyć podstawowy szablon, który ma kilka wariantów pochodnych. Szablony czasu uruchamiania to te, które mają właściwość **Narzędzie niestandardowe** ustawioną na **TextTemplatingFilePreprocessor.** Szablon czasu wykonywania generuje kod, który można wywoływać w aplikacji, aby tworzyć tekst zdefiniowany w szablonie. Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

Jeśli nie określisz atrybutu, klasa bazowa i klasa pochodna są generowane `inherits` na podstawie szablonu tekstu. Po określeniu `inherits` atrybutu generowana jest tylko klasa pochodna. Klasa bazowa może być napisana odręcznie, ale musi mieć metody, które są używane w klasie pochodnej.

Zazwyczaj można określić inny wstępnie przetworzony szablon jako klasę bazową. Szablon podstawowy dostarcza wspólne bloki tekstu, które mogą się przeplatać z tekstem z szablonów pochodnych. Bloki cech klas mogą być stosowane `<#+ ... #>` do definiowania metod zawierających fragmenty tekstu. Na przykład można umieścić strukturę tekstu wyjściowego w szablonie podstawowym, zapewniającym wirtualne metody, które mogą zostać zastąpione w szablonach pochodnych:

Szablon tekstowy (wstępnie przetworzony) czasu wykonywania BaseTemplate.tt:

```scr
This is the common header.
<#
  SpecificFragment1();
#>
A common central text.
<#
  SpecificFragment2();
#>
This is the common footer.
<#+
  // Declare abstract methods
  protected virtual void SpecificFragment1() { }
  protected virtual void SpecificFragment2() { }
#>
```

Szablon tekstowy (wstępnie przetworzony) czasu wykonywania DerivedTemplate1.tt:

```csharp
<#@ template language="C#" inherits="BaseTemplate" #>
<#
  // Run the base template:
  base.TransformText();
#>
<#+
// Provide fragments specific to this derived template:
protected override void SpecificFragment1()
{
#>
   Fragment 1 for DerivedTemplate1
<#+
}
protected override void SpecificFragment2()
{
#>
   Fragment 2 for DerivedTemplate1
<#+
}
#>
```

Kod aplikacji do wywołania DerivedTemplate1:

```csharp
Console.WriteLine(new DerivedTemplate().TransformText());
```

Dane wyjściowe:

```
This is the common header.
   Fragment 1 for DerivedTemplate1
A common central text.
   Fragment 2 for DerivedTemplate1
This is the common footer.
```

Można utworzyć klasy podstawowe i pochodne w różnych projektach. Pamiętaj, aby dodać podstawowy projekt lub zestaw do odwołań projektu pochodnego.

Można również użyć zwykłej klasy odręcznej jako klasy bazowej. Klasa bazowa musi dostarczać metody stosowane w klasie pochodnej.

> [!WARNING]
> Jeśli używasz atrybutów i razem, określ `inherits` `hostspecific` hostspecific="trueFromBase" w klasie pochodnej i host="true" w klasie bazowej. Pozwala to uniknąć podwójnej definicji `Host` właściwości w wygenerowanym kodzie.

### <a name="inheritance-in-a-design-time-text-template"></a>Dziedziczenie w szablonie tekstowym czasu projektowania

Szablon tekstowy czasu projektowania to plik, dla którego dla narzędzia **niestandardowego** ustawiono wartość **TextTemplatingFileGenerator**. Szablon generuje plik wyjściowy kodu lub tekstu, który stanowi część Visual Studio projektu. Aby wygenerować plik wyjściowy, szablon najpierw jest tłumaczony na plik kodu programu pośredniego, którego zwykle nie widać. Atrybut `inherits` określa klasę bazową dla tego kodu pośredniego.

W przypadku szablonu tekstowego czasu projektowania można określić dowolną klasę bazową pochodzącą od klasy <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Użyj dyrektywy `<#@assembly#>` , aby załadować zestaw lub projekt, który zawiera klasę bazową.

Aby uzyskać więcej informacji, zobacz ["Dziedziczenie w szablonach tekstowych" w blogu Gareth Jones](/archive/blogs/garethj/vs2010-sp1-t4-template-inheritance-part-i-sample-metadata).

## <a name="linepragmas-attribute"></a>linePragmas, atrybut

Przykład:

`linePragmas="false"`

Prawidłowe wartości:

`true` (ustawienie domyślne)

`false`

Ustawienie tego atrybutu na false powoduje usunięcie znaczników, które identyfikują numery wierszy w wygenerowanym kodzie. Oznacza to, że kompilator będzie zgłaszał błędy, używając numerów wierszy wygenerowanego kodu. Daje to więcej opcji debugowania, ponieważ można wybrać debugowanie szablonu tekstu lub wygenerowanego kodu.

Ten atrybut może również pomóc, jeśli bezwzględne nazwy plików w pragmach powodują rozpraszanie scalania pod kontrolą kodu źródłowego.

## <a name="visibility-attribute"></a>atrybut visibility

Przykład:

`visibility="internal"`

Prawidłowe wartości:

`public` (ustawienie domyślne)

`internal`

W szablonie tekstowym czasu wykonywania, ustawia atrybut widoczności wygenerowanej klasy. Domyślnie klasa jest częścią publicznego interfejsu API kodu, ale dzięki ustawieniu możesz upewnić się, że tylko twój kod może używać klasy `visibility="internal"` generowania tekstu.