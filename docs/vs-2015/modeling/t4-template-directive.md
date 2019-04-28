---
title: T4 dotycząca Dyrektywa szablonu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2b0a8e04-6fee-4c6c-b086-e49fc728a3ed
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 252b554542df23e2d3197dfe28100546a6d25b32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411462"
---
# <a name="t4-template-directive"></a>Dyrektywa T4 dotycząca szablonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstowego T4 zwykle zaczyna się od `template` dyrektywy, który określa sposób przetwarzania szablonu. Powinna istnieć nie więcej niż jedna dyrektywa szablonu w szablonie tekstowym i wszystkich plikach, które on uwzględnia.  
  
 Aby uzyskać ogólne omówienie pisania szablonów tekstowych, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template-directive"></a>Używanie dyrektywy Template  
  
```  
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 `template` Dyrektywa ma kilka atrybutów, które pozwalają określić różne aspekty transformacji. Wszystkie atrybuty są opcjonalne.  
  
## <a name="compileroptions-attribute"></a>Atrybut compilerOptions  
 Przykład:  
 `compilerOptions="optimize+"`  
  
 Prawidłowe wartości:  
 Wszystkie prawidłowe opcje kompilatora. Aby uzyskać więcej informacji, zobacz [C# opcje kompilatora wymienione według kategorii](http://msdn.microsoft.com/library/96437ecc-6502-4cd3-b070-e9386a298e83) i [Visual Basic opcje kompilatora wymienione według kategorii](http://msdn.microsoft.com/library/fbe36f7a-7cfa-4f77-a8d4-2be5958568e3).  
  
 Ignorowane dla szablonów w czasie wykonywania (wstępnie przetworzonych).  
  
 Te opcje są stosowane, gdy szablon został przekształcony w [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)], a kod wynikowy jest kompilowany.  
  
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
 `true, false`. Wartość domyślna to false.  
  
 Jeśli `debug` atrybut jest `true`, plik kodu pośredniego będzie zawierać informacje, które umożliwiają debugerowi dokładne określenie pozycji w szablonie, gdzie wystąpiło przerwanie lub wyjątek.  
  
 Dla szablonów czasu projektowania plik kodu pośredniego zostanie zapisany z **% TEMP %** katalogu.  
  
 Aby uruchomić szablon czasu projektowania w debugerze, Zapisz szablon tekstowy, a następnie otwórz menu skrótów szablonu tekstu w Eksploratorze rozwiązań i wybierz **Debuguj szablon T4**.  
  
## <a name="hostspecific-attribute"></a>Atrybut hostspecific  
 Przykład:  

```  
hostspecific="true"  
```  
  
 Prawidłowe wartości:  
 `true, false, trueFromBase`. Wartość domyślna to false.  
  
 Jeśli wartość tego atrybutu zostanie ustawiona `true`, właściwość o nazwie `Host` jest dodawana do klasy generowanej przez szablon tekstowy. Właściwość jest odwołaniem do hosta silnika transformacji i jest zadeklarowana jako <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Jeśli został zdefiniowany niestandardowy host, można go rzutować na niestandardowy typ hosta.  
  
 Ponieważ typ tej właściwości zależy od typu hosta, jest to przydatne wyłącznie podczas pisania szablonu tekstu, który działa tylko z określonym hostem. Ma zastosowanie do [szablonów czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ale nie [szablonów czasu wykonywania](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Gdy `hostspecific` jest `true` i używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], można rzutować `this.Host` na IServiceProvider, aby uzyskać dostęp do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funkcji. Można również użyć `Host.ResolvePath(filename)` uzyskać ścieżkę bezwzględną pliku w projekcie. Na przykład:  
  
```csharp  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#@ import namespace="System.IO" #>  
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
  
 Jeśli używasz `inherits` i `hostspecific` atrybuty razem, określ host = "trueFromBase" w klasie pochodnej i host = "true" w klasie bazowej. Pozwala to uniknąć podwójnej definicji `Host` właściwość w wygenerowanym kodzie.  
  
## <a name="language-attribute"></a>Atrybut language  
 Przykład:  
 `language="VB"`  
  
 Prawidłowe wartości:  
 `C#` (ustawienie domyślne)  
  
 `VB`  
  
 Atrybut language określa język ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../includes/csprcs-md.md)]) na potrzeby kodu źródłowego w blokach instrukcji i wyrażeń. Pliku kodu pośredniego, z którego jest generowane wyjście, użyje tego języka. Język ten nie jest powiązany z językiem generowanym przez szablon, który może być dowolnym rodzajem tekstu.  
  
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
 Można użyć dziedziczenia między szablonami tekstowymi czasu wykonywania, aby utworzyć podstawowy szablon, który ma kilka wariantów pochodnych. Szablony czasu wykonywania to te, które mają **narzędzie niestandardowe** właściwością **TextTemplatingFilePreprocessor**. Szablon czasu wykonywania generuje kod, który można wywoływać w aplikacji, aby tworzyć tekst zdefiniowany w szablonie. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Jeśli nie określisz `inherits` atrybut, klasa bazowa i Klasa pochodna są generowane na podstawie szablonu tekstu. Po określeniu `inherits` atrybutu, tylko klasa pochodna jest generowana. Klasa bazowa może być napisana odręcznie, ale musi mieć metody, które są używane w klasie pochodnej.  
  
 Zazwyczaj można określić inny wstępnie przetworzony szablon jako klasę bazową. Szablon podstawowy dostarcza wspólne bloki tekstu, które mogą się przeplatać z tekstem z szablonów pochodnych. Można użyć bloków funkcji klasy `<#+ ... #>` do definiowania metod, które zawierają fragmenty tekstu. Na przykład można umieścić strukturę tekstu wyjściowego w szablonie podstawowym, zapewniającym wirtualne metody, które mogą zostać zastąpione w szablonach pochodnych:  
  
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
  
 Można utworzyć klasy podstawowe i pochodne w różnych projektach. Pamiętaj o dodaniu projektu bazowego lub zestawu do odwołań projektu pochodnego.  
  
 Można również użyć zwykłej klasy odręcznej jako klasy bazowej. Klasa bazowa musi dostarczać metody stosowane w klasie pochodnej.  
  
> [!WARNING]
> Jeśli używasz `inherits` i `hostspecific` atrybuty razem, określ hostspecific = "trueFromBase" w klasie pochodnej i host = "true" w klasie bazowej. Pozwala to uniknąć podwójnej definicji `Host` właściwość w wygenerowanym kodzie.  
  
### <a name="inheritance-in-a-design-time-text-template"></a>Dziedziczenie w szablonie tekstowym czasu projektowania  
 Szablon tekstowy czasu projektowania jest plikiem, dla którego **narzędzie niestandardowe** ustawiono **TextTemplatingFileGenerator**. Szablon generuje plik wyjściowy kodu lub tekstu, który stanowi część sieci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Aby wygenerować plik wyjściowy, szablon najpierw jest tłumaczony na plik kodu programu pośredniego, którego zwykle nie widać. `inherits` Atrybut określa klasę bazową dla tego kodu pośredniego.  
  
 Dla szablonu tekstu czasu projektowania można określić klasę bazową, która jest pochodną <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Użyj `<#@assembly#>` dyrektywy, aby załadować zestaw lub projekt, który zawiera klasę bazową.  
  
 Aby uzyskać więcej informacji, zobacz ["Dziedziczenie w szablonów tekstowych" w blogu Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
## <a name="linepragmas-attribute"></a>Atrybut LinePragmas  
 Przykład:  
 `linePragmas="false"`  
  
 Prawidłowe wartości:  
 `true` (ustawienie domyślne)  
  
 `false`  
  
 Ustawienie tego atrybutu na false powoduje usunięcie znaczników, które identyfikują numery wierszy w wygenerowanym kodzie. Oznacza to, że kompilator będzie zgłaszał błędy, używając numerów wierszy wygenerowanego kodu. Daje to więcej opcji debugowania, ponieważ można wybrać debugowanie szablonu tekstu lub wygenerowanego kodu.  
  
 Ten atrybut może także pomóc, jeśli bezwzględne nazwy plików w wyrażeniach pragma powodują rozpraszanie scalania pod kontrolą kodu źródłowego.  
  
## <a name="visibility-attribute"></a>Atrybut Visibility  
 Przykład:  
 `visibility="internal"`  
  
 Prawidłowe wartości:  
 `public` (ustawienie domyślne)  
  
 `internal`  
  
 W szablonie tekstowym czasu wykonywania, ustawia atrybut widoczności wygenerowanej klasy. Domyślnie klasa jest częścią publicznego API kodu, ale przez ustawienie `visibility="internal"` możesz upewnić się, że tylko kod użytkownika może używać klasy generującej tekst.
