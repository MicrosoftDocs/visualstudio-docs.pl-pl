---
title: Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a145907ad76016802e0547fc251b929b913253d5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945680"
---
# <a name="accessing-models-from-text-templates"></a>Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu
Przy użyciu szablonów tekstowych, można utworzyć raport plików, pliki kodu źródłowego i inne pliki tekstowe, które są oparte na modelach języka specyficznego dla domeny. Aby uzyskać podstawowe informacje na temat szablonów tekstu, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Szablonów tekstowych będzie działać w trybie doświadczalnym podczas debugowania DSL, a także będą działać na komputerze, na którym wdrożono język DSL.

> [!NOTE]
>  Po utworzeniu rozwiązania DSL, przykładowy szablon tekstu  **\*.tt** pliki są generowane w projekcie debugowania. Po zmianie nazwy klas domeny, te szablony nie będą już działać. Niemniej jednak zawierają one podstawowe dyrektyw, które są potrzebne i zawierają przykłady, które można zaktualizować, aby dopasować DSL.

 Dostęp do modelu z szablonu tekstu:

- Ustaw właściwość Dziedzicz — dyrektywa szablonu do <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. To zapewnia dostęp do Store.

- Określ procesory dyrektyw dla języka DSL, który chcesz uzyskać dostęp. Ładuje zestawy dla DSL, tak, aby można było używać jej klas domeny, właściwości i relacje w kodzie szablon tekstowy. Powoduje ono również pobieranie pliku modelu, który określisz.

  A `.tt` podobny do poniższego przykładu utworzony zostanie plik w projekcie debugowania podczas tworzenia nowego rozwiązania programu Visual Studio z szablonu minimalnego języka DSL.

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

- Szablon można użyć klas domeny, właściwości i relacje, które są zdefiniowane w definicji DSL.

- Szablon ładuje plik modelu, który określisz w `requires` właściwości.

- Właściwość `this` zawiera element główny. W efekcie kodu można przejść do innych elementów modelu. Nazwa właściwości jest zwykle taka sama jak klasa domeny katalogu głównego DSL. W tym przykładzie jest to `this.ExampleModel`.

- Mimo że język, w którym zapisywane są fragmenty kodu C#, można wygenerować tekstu dowolnego rodzaju. Można także napisać kod w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] przez dodanie właściwości `language="VB"` do `template` dyrektywy.

- Aby debugować szablonu, należy dodać `debug="true"` do `template` dyrektywy. Szablon zostanie otwarty w innym wystąpieniu programu Visual Studio, jeśli wystąpi wyjątek. Jeśli chcesz przerwać działanie debugera w określonym miejscu w kodzie, instrukcji insert `System.Diagnostics.Debugger.Break();`

   Aby uzyskać więcej informacji, zobacz [debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Procesor dyrektywy języka DSL — informacje
 Szablon można użyć klas domeny, które są zdefiniowane w definicji DSL. To jest spowodowanym ulepszonym dyrektywy, który zwykle pojawia się bliżej początku tego szablonu. W poprzednim przykładzie jest następująca.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Nazwa dyrektywy ( `MyLanguage`, w tym przykładzie) jest tworzony na podstawie nazwy DSL. Wywołuje *procesora dyrektywy* , zostanie wygenerowany jako część DSL. Można znaleźć jego kod źródłowy w **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Procesor dyrektywy DSL wykonuje dwa główne zadania:

-   Wstawia skutecznie dyrektywach zestawu i importowania do szablonu, który odwołuje się do DSL. Dzięki temu można użyć klasy usługi domeny w kod szablonu.

-   Ładuje plik który określisz w `requires` parametru i ustawia właściwość `this` odwołujący się do elementu głównego załadować modelu.

## <a name="validating-the-model-before-running-the-template"></a>Sprawdzanie poprawności modelu przed uruchomieniem tego szablonu
 Może spowodować modelu zostanie wykonane sprawdzanie poprawności, zanim zostanie wykonany szablonu.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Należy zauważyć, że:

1. `filename` i `validation` parametry są rozdzielane ";" oraz nie może być nie separatorów ani spacji.

2. Lista kategorii weryfikacji określa metody sprawdzania poprawności, które zostaną wykonane. Wiele kategorii powinny być rozdzielone za pomocą "&#124;" oraz nie może być nie separatorów ani spacji.

   Jeśli zostanie znaleziony błąd, będą raportowane w oknie błędów, a plik wynik będzie zawierać komunikat o błędzie.

## <a name="Multiple"></a> Uzyskiwanie dostępu do wielu modeli z szablonu tekstowego

> [!NOTE]
>  Ta metoda umożliwia odczyt wiele modeli, w tym samym szablonie, ale nie obsługuje odwołań ModelBus. Modele, które są powiązane przez odwołania ModelBus zamieszczono [przy użyciu programu Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Jeśli chcesz uzyskać dostęp do więcej niż jednego modelu z tego samego szablonu tekstu, należy wywołać generowanym procesorem dyrektywy jeden raz dla każdego modelu. Należy określić nazwę pliku każdego modelu w `requires` parametru. Należy określić nazwy, które chcesz użyć dla klasy domeny katalogu głównego w `provides` parametru. Należy określić różne wartości `provides` parametrom poszczególnych wywołań dyrektywy. Na przykład załóżmy, że masz trzy pliki modelu o nazwie Library.xyz School.xyz i Work.xyz. Aby uzyskiwać do nich dostęp z tego samego szablonu tekstu, należy napisać trzech wywołań dyrektywy, podobne do poniższych.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Ten przykładowy kod jest dla języka, który jest oparty na szablonie rozwiązania minimalny języka.

 Aby uzyskać dostęp do modeli w szablonie tekstowym, można teraz napisać kod podobny do kodu, w poniższym przykładzie.

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
 Jeśli chcesz określić, w czasie wykonywania, modeli, które można załadować pliku modelu można załadować dynamicznie w kodzie programu, a nie za pomocą dyrektywy specyficzne dla języka DSL.

 Jednak jedna z funkcji specyficznych dla języka DSL — dyrektywa jest zaimportowanie przestrzeń nazw DSL, tak aby kod szablonu mógł używać klas domeny zdefiniowane w tym DSL. Ponieważ nie jest używany dyrektywy, należy dodać  **\<zestawu >** i  **\<importowanie >** dyrektywy dla wszystkich modeli, które mogą być ładowane. Jest to łatwe w przypadku różnych modeli, które może ładować wszystkich wystąpień tego samego języka DSL.

 Aby załadować plik, najbardziej efektywną metodę jest za pomocą programu Visual Studio ModelBus. W typowym scenariuszu szablon tekstowy użyje dyrektywy specyficzne dla języka DSL załadować pierwszy model w zwykły sposób. Ten model zawiera ModelBus odwołania do innego modelu. ModelBus służy do otwierania przywoływanym modelem i dostęp do konkretnego elementu. Aby uzyskać więcej informacji, zobacz [przy użyciu programu Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 W przypadku mniej zwykle możesz chcieć Otwórz plik modelu, do której masz tylko nazwę pliku, który może nie być w bieżącym projekcie programu Visual Studio. W takim przypadku można otworzyć pliku przy użyciu techniki opisanej w [jak: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generowanie wielu plików na podstawie szablonu
 Jeśli chcesz wygenerować kilka plików — na przykład, aby wygenerować osobny plik dla każdego elementu w modelu, istnieje kilka możliwych rozwiązań. Domyślnie tylko jeden plik jest generowany dla każdego pliku szablonu.

### <a name="splitting-a-long-file"></a>Podział pliku długi
 W przypadku tej metody używasz szablonu do wygenerowania pojedynczego pliku, oddzielonych ogranicznikiem. Następnie plik zostanie podzielony na części. Istnieją dwa szablony, jeden można wygenerować pojedynczy plik, a druga podziału.

 **LoopTemplate.t4** generuje długie pojedynczy plik. Zauważ, że rozszerzenie pliku ".t4", ponieważ mają być przetwarzane nie, bezpośrednio po kliknięciu **Przekształć wszystkie szablony**. Ten szablon przyjmuje parametr, który określa ciąg ogranicznik, który oddziela segmenty:

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

 `LoopSplitter.tt` wywołuje `LoopTemplate.t4`, a następnie dzieli wynikowy plik na jego segmentów. Należy zauważyć, że ten szablon nie ma być szablonem modelowania, ponieważ nie odczytuje model.

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