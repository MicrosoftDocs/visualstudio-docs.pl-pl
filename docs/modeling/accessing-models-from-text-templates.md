---
title: Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu
description: Dowiedz się, jak używać szablonów tekstowych do tworzenia plików raportów, plików kodu źródłowego i innych plików tekstowych, które są oparte na modelach języka właściwych dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64d937f9a63207e16664bbd9254ae60470caeb41
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362291"
---
# <a name="access-models-from-text-templates"></a>Dostęp do modeli z szablonów tekstowych

Za pomocą szablonów tekstowych można tworzyć pliki raportów, pliki kodu źródłowego i inne pliki tekstowe, które są oparte na modelach języka właściwych dla domeny. Aby uzyskać podstawowe informacje na temat szablonów tekstowych, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Szablony tekstowe będą działały w trybie eksperymentalnym podczas debugowania DSL, a także będą działały na komputerze, na którym wdrożono DSL.

> [!NOTE]
> Podczas tworzenia rozwiązania DSL, **\* przykładowy szablon tekstowy** jest generowany w projekcie debugowania. Zmiany nazw klas domen nie będą już działać. Jednak zawierają one wymagane dyrektywy podstawowe i zawierają przykłady, które można zaktualizować w celu dopasowania do języka DSL.

 Aby uzyskać dostęp do modelu z szablonu tekstu:

- Ustaw właściwość dziedziczenia dyrektywy Template na [Microsoft. VisualStudio. TextTemplating. vshost. ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Zapewnia to dostęp do sklepu.

- Określ procesory dyrektywy dla DSL, do których chcesz uzyskać dostęp. Spowoduje to załadowanie zestawów dla DSL, aby można było używać ich klas, właściwości i relacji w kodzie szablonu tekstu. Ładuje również określony plik modelu.

  `.tt`Plik podobny do poniższego przykładu jest tworzony w projekcie debugowania podczas tworzenia nowego rozwiązania programu Visual Studio z szablonu języka DSL minimalnego.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Zwróć uwagę na następujące kwestie dotyczące tego szablonu:

- Szablon może używać klas domen, właściwości i relacji zdefiniowanych w definicji DSL.

- Szablon ładuje plik modelu określony we `requires` właściwości.

- Właściwość w `this` zawiera element główny. Z tego miejsca kod może przechodzić do innych elementów modelu. Nazwa właściwości jest zwykle taka sama jak Klasa domeny głównej DSL. W tym przykładzie jest to `this.ExampleModel`.

- Chociaż język, w którym są zapisywane fragmenty kodu, jest w języku C#, można wygenerować tekst dowolnego rodzaju. Możesz Alternatywnie napisać kod w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , dodając Właściwość `language="VB"` do `template` dyrektywy.

- Aby debugować szablon, Dodaj `debug="true"` do `template` dyrektywy. Szablon zostanie otwarty w innym wystąpieniu programu Visual Studio, jeśli wystąpi wyjątek. Jeśli chcesz przerwać debuger w określonym punkcie kodu, Wstaw instrukcję `System.Diagnostics.Debugger.Break();`

   Aby uzyskać więcej informacji, zobacz [Debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Informacje o procesorze dyrektywy DSL
 Szablon może używać klas domen zdefiniowanych w definicji DSL. Jest to pożądane przez dyrektywę, która zwykle pojawia się blisko początku szablonu. W poprzednim przykładzie jest to następujące polecenie.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Nazwa dyrektywy ( `MyLanguage` w tym przykładzie) pochodzi od nazwy Twojego języka DSL. Wywołuje *procesor dyrektywy* , który jest generowany w ramach DSL. Kod źródłowy można znaleźć w **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Procesor dyrektywy DSL wykonuje dwa podstawowe zadania:

- Efektywnie dodaje dyrektywy Assembly i import do szablonu, który odwołuje się do języka DSL. Pozwala to na korzystanie z klas domeny w kodzie szablonu.

- Ładuje plik określony w `requires` parametrze i ustawia właściwość w `this` , która odwołuje się do elementu głównego załadowanego modelu.

## <a name="validating-the-model-before-running-the-template"></a>Sprawdzanie poprawności modelu przed uruchomieniem szablonu
 Można spowodować sprawdzenie poprawności modelu przed wykonaniem szablonu.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Zwróć uwagę, że:

1. `filename`Parametry i `validation` są rozdzielone znakami ";" i nie mogą zawierać innych separatorów ani spacji.

2. Lista kategorii walidacji określa, które metody walidacji zostaną wykonane. Wiele kategorii należy rozdzielić "&#124;" i nie może zawierać innych separatorów ani spacji.

   W przypadku znalezienia błędu zostanie on zgłoszony w oknie błędy, a plik wynikowy będzie zawierał komunikat o błędzie.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Uzyskiwanie dostępu do wielu modeli z szablonu tekstu

> [!NOTE]
> Ta metoda umożliwia odczytywanie wielu modeli w tym samym szablonie, ale nie obsługuje odwołań ModelBus. Aby odczytywać modele, które są połączone z odwołaniami ModelBus, zobacz [używanie Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Jeśli chcesz uzyskać dostęp do więcej niż jednego modelu z tego samego szablonu tekstu, należy wywołać wygenerowanego procesora dyrektywy jeden raz dla każdego modelu. Należy określić nazwę pliku każdego modelu w `requires` parametrze. Należy określić nazwy, które mają być używane dla klasy domeny głównej w `provides` parametrze. Należy określić różne wartości `provides` parametrów w poszczególnych wywołaniach dyrektywy. Załóżmy na przykład, że masz trzy pliki modelu o nazwie Library. xyz, szkoły. xyz i Work. xyz. Aby uzyskać dostęp do nich z tego samego szablonu tekstu, należy napisać trzy wywołania dyrektywy podobne do następujących.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Ten przykładowy kod dotyczy języka, który jest oparty na szablonie rozwiązania o minimalnym języku.

 Aby uzyskać dostęp do modeli w szablonie tekstowym, można teraz napisać kod podobny do kodu w poniższym przykładzie.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Dynamiczne ładowanie modeli
 Jeśli chcesz określić w czasie wykonywania modele do załadowania, możesz załadować plik modelu dynamicznie w kodzie programu, zamiast używać dyrektywy specyficznej dla DSL.

 Jednak jedna z funkcji dyrektywy specyficznej dla DSL polega na zaimportowaniu przestrzeni nazw DSL, aby kod szablonu mógł używać klas domeny zdefiniowanych w tym DSL. Ponieważ nie używasz dyrektywy, musisz dodać **\<assembly>** **\<import>** dyrektywy i dla wszystkich modeli, które mogą zostać załadowane. Jest to proste, jeśli różne modele, które można załadować, to wszystkie wystąpienia tego samego DSL.

 Aby załadować plik, najbardziej efektywna metoda polega na użyciu Visual Studio ModelBus. W typowym scenariuszu szablon tekstowy będzie używać dyrektywy specyficznej dla DSL do załadowania pierwszego modelu w zwykły sposób. Ten model będzie zawierać odwołania ModelBus do innego modelu. Możesz użyć ModelBus, aby otworzyć przywoływany model i uzyskać dostęp do określonego elementu. Aby uzyskać więcej informacji, zobacz [używanie Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 W mniej typowym scenariuszu możesz chcieć otworzyć plik modelu, dla którego masz tylko nazwę pliku, a który może nie znajdować się w bieżącym projekcie programu Visual Studio. W takim przypadku można otworzyć plik przy użyciu techniki opisanej w artykule [jak: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generowanie wielu plików z szablonu
 Jeśli chcesz wygenerować kilka plików — na przykład w celu wygenerowania osobnego pliku dla każdego elementu w modelu, istnieje kilka możliwych metod. Domyślnie tylko jeden plik jest tworzony z każdego pliku szablonu.

### <a name="splitting-a-long-file"></a>Dzielenie długiego pliku
 W tej metodzie należy użyć szablonu do wygenerowania pojedynczego pliku, oddzielonego ogranicznikiem. Następnie należy podzielić plik na jego części. Istnieją dwa szablony, jeden do wygenerowania pojedynczego pliku, a drugi do jego podzielenia.

 **LoopTemplate. T4** generuje długi pojedynczy plik. Należy zauważyć, że rozszerzenie pliku to ". T4", ponieważ nie powinno być przetwarzane bezpośrednio po kliknięciu przycisku **Przekształć wszystkie szablony**. Ten szablon przyjmuje parametr, który określa ciąg ogranicznika oddzielający segmenty:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` wywołuje `LoopTemplate.t4` , a następnie dzieli otrzymany plik na segmenty. Należy zauważyć, że ten szablon nie musi być szablonem modelowania, ponieważ nie odczytuje modelu.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```
