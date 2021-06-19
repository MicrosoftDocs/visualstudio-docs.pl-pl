---
title: Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu
description: Dowiedz się, jak za pomocą szablonów tekstowych tworzyć pliki raportu, pliki kodu źródłowego i inne pliki tekstowe oparte na modelach językowych specyficznych dla domeny.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, accessing models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05e21dacfe56f41f1d2c0da51659ab55203db1a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389166"
---
# <a name="access-models-from-text-templates"></a>Uzyskiwanie dostępu do modeli z szablonów tekstowych

Za pomocą szablonów tekstowych można tworzyć pliki raportów, pliki kodu źródłowego i inne pliki tekstowe, które są oparte na modelach językowych specyficznych dla domeny. Aby uzyskać podstawowe informacje na temat szablonów tekstowych, zobacz [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Szablony tekstu będą działać w trybie eksperymentalnym podczas debugowania DSL, a także będzie działać na komputerze, na którym wdrożono DSL.

> [!NOTE]
> Podczas tworzenia rozwiązania DSL w projekcie debugowania są generowane pliki **\* tt przykładowego** szablonu tekstowego. Po zmianie nazw klas domeny te szablony nie będą już działać. Niemniej jednak zawierają podstawowe dyrektywy, które są potrzebne, i zawierają przykłady, które można zaktualizować, aby dopasować dsl.

 Aby uzyskać dostęp do modelu z szablonu tekstowego:

- Ustaw właściwość inherit dyrektywy template na [Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation](/previous-versions/bb893209(v=vs.140)). Zapewnia to dostęp do sklepu.

- Określ procesory dyrektyw dla DSL, do którego chcesz uzyskać dostęp. To ładuje zestawy dla DSL, aby można było używać jego klas domeny, właściwości i relacji w kodzie szablonu tekstu. Ładuje również określony plik modelu.

  Plik podobny do poniższego przykładu jest tworzony w projekcie Debugowanie podczas tworzenia nowego Visual Studio z szablonu `.tt` języka minimalnego DSL.

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

- Szablon może używać klas domeny, właściwości i relacji zdefiniowanych w definicji DSL.

- Szablon ładuje plik modelu określony we właściwości `requires` .

- Właściwość w `this` elemencie zawiera element główny. W tym miejscu kod może przejść do innych elementów modelu. Nazwa właściwości jest zwykle taka sama jak główna klasa domeny DSL. W tym przykładzie jest to `this.ExampleModel`.

- Chociaż język, w którym są zapisywane fragmenty kodu, to C#, można wygenerować tekst dowolnego rodzaju. Możesz też napisać kod w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] obiekcie, dodając właściwość `language="VB"` do dyrektywy `template` .

- Aby debugować szablon, dodaj `debug="true"` do `template` dyrektywy . Szablon zostanie otwarty w innym wystąpieniu Visual Studio, jeśli wystąpi wyjątek. Jeśli chcesz włamać się do debugera w określonym punkcie w kodzie, wstaw instrukcje `System.Diagnostics.Debugger.Break();`

   Aby uzyskać więcej informacji, zobacz [Debugowanie szablonu tekstowego T4.](../modeling/debugging-a-t4-text-template.md)

## <a name="about-the-dsl-directive-processor"></a>Informacje o procesorze dyrektywy DSL
 Szablon może używać klas domen zdefiniowanych w definicji DSL. Jest to prowadzeni przez dyrektywę, która zazwyczaj pojawia się w pobliżu początku szablonu. W poprzednim przykładzie jest to następujące.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Nazwa dyrektywy `MyLanguage` (, w tym przykładzie) pochodzi od nazwy DSL. Wywołuje procesor *dyrektywy,* który jest generowany jako część DSL. Kod źródłowy tego kodu można znaleźć w pliku **Dsl\GeneratedCode\DirectiveProcessor.cs.**

 Procesor dyrektywy DSL wykonuje dwa podstawowe zadania:

- Efektywnie wstawia dyrektywy zestawu i importu do szablonu, który odwołuje się do DSL. Dzięki temu można używać klas domeny w kodzie szablonu.

- Ładuje plik określony w parametrze i ustawia właściwość w elemencie , która odwołuje się do elementu głównego `requires` `this` załadowanego modelu.

## <a name="validating-the-model-before-running-the-template"></a>Sprawdzania poprawności modelu przed uruchomieniem szablonu
 Możesz spowodować weryfikację modelu przed wykonaniem szablonu.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Zwróć uwagę, że:

1. Parametry `filename` i są oddzielone znakiem "; " i nie mogą zawierać żadnych innych `validation` separatorów ani spacji.

2. Lista kategorii weryfikacji określa, które metody weryfikacji zostaną wykonane. Wiele kategorii należy rozdzielać znakami "&#124;" i nie może być żadnych innych separatorów ani spacji.

   Jeśli błąd zostanie znaleziony, zostanie zgłoszony w oknie błędów, a plik wyników będzie zawierać komunikat o błędzie.

## <a name="accessing-multiple-models-from-a-text-template"></a><a name="Multiple"></a> Uzyskiwanie dostępu do wielu modeli z szablonu tekstowego

> [!NOTE]
> Ta metoda umożliwia odczytywanie wielu modeli w tym samym szablonie, ale nie obsługuje odwołań ModelBus. Aby odczytać modele, które są połączone za pomocą odwołań ModelBus, zobacz Using Visual Studio ModelBus in a Text Template (Używanie Visual Studio ModelBus [w szablonie tekstowym).](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 Jeśli chcesz uzyskać dostęp do więcej niż jednego modelu z tego samego szablonu tekstu, musisz wywołać wygenerowany procesor dyrektywy jeden raz dla każdego modelu. Należy określić nazwę pliku każdego modelu w `requires` parametrze. W parametrze należy określić nazwy, których chcesz użyć dla głównej klasy `provides` domeny. Należy określić różne wartości parametrów `provides` w każdym wywołań dyrektywy. Załóżmy na przykład, że masz trzy pliki modelu o nazwach Library.xyz, School.xyz i Work.xyz. Aby uzyskać do nich dostęp z tego samego szablonu tekstowego, należy napisać trzy wywołania dyrektywy podobne do następujących.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
> Ten przykładowy kod dotyczy języka opartego na szablonie rozwiązania Minimalny język.

 Aby uzyskać dostęp do modeli w szablonie tekstowym, możesz teraz napisać kod podobny do kodu w poniższym przykładzie.

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
 Jeśli chcesz określić w czasie uruchamiania, które modele mają być ładowane, możesz dynamicznie załadować plik modelu w kodzie programu, zamiast używać dyrektywy specyficznej dla DSL.

 Jednak jedną z funkcji specyficzne dla DSL dyrektywy jest zaimportowanie przestrzeni nazw DSL, dzięki czemu kod szablonu może używać klas domen zdefiniowanych w tym DSL. Ponieważ nie używasz dyrektywy , musisz dodać dyrektywy i dla **\<assembly>** **\<import>** wszystkich modeli, które można załadować. Jest to łatwe, jeśli różne modele, które można załadować są wszystkie wystąpienia tego samego DSL.

 Aby załadować plik, najbardziej efektywną metodą jest użycie Visual Studio ModelBus. W typowym scenariuszu szablon tekstowy będzie używać dyrektywy specyficznej dla dsl, aby załadować pierwszy model w zwykły sposób. Ten model będzie zawierać odwołania ModelBus do innego modelu. Za pomocą elementu ModelBus można otworzyć model, do których się odwoływuje, i uzyskać dostęp do określonego elementu. Aby uzyskać więcej informacji, zobacz Using Visual Studio ModelBus in a Text Template (Używanie Visual Studio ModelBus [w szablonie tekstowym).](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

 W mniej zwykłym scenariuszu warto otworzyć plik modelu, dla którego masz tylko nazwę pliku i który może nie być w bieżącym Visual Studio projektu. W takim przypadku możesz otworzyć plik przy użyciu techniki opisanej w tece [How to: Open a Model from File in Program Code](../modeling/how-to-open-a-model-from-file-in-program-code.md)(Jak otworzyć model z pliku w kodzie programu ).

## <a name="generating-multiple-files-from-a-template"></a>Generowanie wielu plików na podstawie szablonu
 Jeśli chcesz wygenerować kilka plików — na przykład w celu wygenerowania oddzielnego pliku dla każdego elementu w modelu, istnieje kilka możliwych podejść. Domyślnie na podstawie każdego pliku szablonu jest wytwarzanych tylko jeden plik.

### <a name="splitting-a-long-file"></a>Dzielenie długiego pliku
 W tej metodzie użyjemy szablonu do wygenerowania pojedynczego pliku oddzielonego ogranicznikiem. Następnie podziel plik na jego części. Istnieją dwa szablony: jeden do wygenerowania pojedynczego pliku, a drugi do jego podziału.

 **LoopTemplate.t4** generuje długi pojedynczy plik. Zwróć uwagę, że jego rozszerzeniem pliku jest ".t4", ponieważ nie powinno ono być przetwarzane bezpośrednio po kliknięciu **przycisku Przekształć wszystkie szablony.** Ten szablon przyjmuje parametr określający ciąg ogranicznika oddzielające segmenty:

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

 `LoopSplitter.tt` Wywołuje `LoopTemplate.t4` , a następnie dzieli wynikowy plik na jego segmenty. Należy zauważyć, że ten szablon nie musi być szablonem modelowania, ponieważ nie odczytuje modelu.

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
