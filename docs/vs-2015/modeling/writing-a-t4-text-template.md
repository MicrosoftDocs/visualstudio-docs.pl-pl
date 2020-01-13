---
title: Pisanie szablonu tekstowego T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
ms.assetid: 94328da7-953b-4e92-9587-648543d1f732
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c3e970ac2d6f7de86908a88aff6235c598ead810
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918477"
---
# <a name="writing-a-t4-text-template"></a>Pisanie szablonu tekstowego T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Szablon tekstu zawiera tekst, który zostanie z niego wygenerowany. Na przykład szablon, który tworzy stronę sieci Web, będzie zawierał "\<HTML >..." i wszystkie inne standardowe części strony HTML. Wstawione do szablonu są *blokami sterowania*, które są fragmentami kodu programu. Bloki sterujące zawierają zmienne wartości i umożliwiają warunkowość oraz powtarzalność części tekstu.

 Ta struktura ułatwia tworzenie szablonu, ponieważ można zacząć od prototypu wygenerowanego pliku, po czym stopniowo wstawiać bloki sterujące, które różnicują wynik.

 Szablony tekstu składają się z następujących elementów:

- **Dyrektywy** — elementy kontrolujące sposób przetwarzania szablonu.

- **Bloki tekstu** — zawartość, która jest kopiowana bezpośrednio do danych wyjściowych.

- **Bloki kontroli** — kod programu, który wstawia wartości zmiennej do tekstu i kontroluje warunkowe lub powtórzone fragmenty tekstu.

  Aby wypróbować przykłady w tym temacie, skopiuj je do pliku szablonu zgodnie z opisem w części [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Po przeprowadzeniu edycji pliku szablonu Zapisz go, a następnie sprawdź plik Output **. txt** .

## <a name="directives"></a>Dyrektyw
 Dyrektywy szablonów tekstu przekazują do silnika tworzenia szablonów tekstu ogólne instrukcje o sposobach generowania kodu przekształcenia oraz pliku wyjściowego.

 Na przykład następująca dyrektywa określa, że plik wyjściowy powinien mieć rozszerzenie .txt:

```

<#@ output extension=".txt" #>
```

 Aby uzyskać więcej informacji na temat dyrektyw, zobacz [dyrektywy dotyczące szablonów tekstowych T4](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Bloki tekstu
 Blok tekstu wstawia tekst bezpośrednio do pliku wyjściowego. Nie istnieje żadne specjalne formatowanie bloków tekstu. Na przykład następujący szablon tekstu będzie generował plik tekstowy zawierający wyraz „Hello”:

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Bloki sterujące
 Bloki sterujące to sekcje kodu programu służące do przekształcania szablonów. Domyślnym językiem jest C#. Chcąc używać języka [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], można napisać następującą dyrektywę na początku pliku:

```
<#@ template language="VB" #>
```

 Język, w którym jest pisany kod źródłowy bloków sterujących, nie ma związku z językiem generowanego tekstu.

### <a name="standard-control-blocks"></a>Standardowe bloki sterujące
 Standardowy blok sterujący to sekcja kodu programu, która generuje część pliku wyjściowego.

 W pliku szablonu można połączyć dowolną liczbę bloków tekstu i standardowych bloków sterujących . Nie można jednak umieścić jednego bloku sterującego w innym. Każdy blok sterujący jest ujęty w symbole `<# ... #>`.

 Na przykład następujące bloki sterujący i tekstu spowodują, że plik wyjściowy będzie zawierał wiersz „0, 1, 2, 3, 4 Hello!”:

```

      <#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Zamiast używać jawnych instrukcji `Write()`, można przeplatać tekst i kod. Poniższy przykład drukuje "Hello!" cztery razy:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Blok tekstu można wstawić w każdym miejscu kodu, gdzie jest dozwolona instrukcja `Write();`.

> [!NOTE]
> Po osadzeniu bloku tekstu w instrukcji złożonej, takiej jak pętla lub warunkowe, zawsze używaj nawiasów klamrowych {...} Aby można było zawierać blok tekstu.

### <a name="expression-control-blocks"></a>Bloki sterowania wyrażeniami
 Blok sterowania wyrażeniem oblicza wartość wyrażenia i konwertuje ją na ciąg. Powstały ciąg jest wstawiany do pliku wyjściowego.

 Bloki sterowania wyrażeniami są ujmowane w symbole `<#= ... #>`.

 Na przykład następujący blok sterujący spowoduje, że plik wyjściowy będzie zawierał cyfrę „5”:

```
<#= 2 + 3 #>
```

 Należy zauważyć, że symbol otwierający ma trzy znaki "< # =".

 Wyrażenie może zawierać dowolną zmienną znajdującą się w jego zakresie. Na przykład ten blok spowoduje wyświetlanie wierszy z następującymi liczbami:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Bloki sterowania cechami klas
 Blok sterowania cechami klasy definiuje właściwości, metody i wszelki inny kod, który nie powinien być objęty głównym przekształceniem. Bloki cech klas są często używane do funkcji pomocników.  Zazwyczaj bloki funkcji klasy są umieszczane w oddzielnych plikach, dzięki czemu mogą być [uwzględniane](#Include) przez więcej niż jeden szablon tekstowy.

 Bloki sterowania cechami klas są ujęte w symbole `<#+ ... #>`.

 Na przykład następujący plik szablonu deklaruje i wykorzystuje metodę:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Cechy klas muszą być umieszczone na końcu pliku, w którym są zapisywane. Można jednak dołączyć (`<#@include#>`) plik, który zawiera cechę klasy, nawet jeśli po dyrektywie `include` następują standardowe bloki i tekst.

 Aby uzyskać więcej informacji na temat bloków sterujących, zobacz [bloki kontrolne szablonu tekstu](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>Bloki cech klas mogą zawierać bloki tekstu
 Można napisać metodę, która generuje tekst. Na przykład:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 Szczególnie przydatne jest umieszczenie metody generującej tekst w oddzielnym pliku, który może być dołączony przez więcej niż jeden szablon.

## <a name="using-external-definitions"></a>Używanie zewnętrznych definicji

### <a name="assemblies"></a>Zestawy
 Bloki kodu szablonu mogą wykorzystywać typy zdefiniowane w najczęściej używanych zestawach środowiska .NET, takich jak System.dll. Ponadto mogą się odwoływać do innych zestawów środowiska .NET oraz zestawów utworzonych przez użytkownika. Jako lokalizację zestawu można podać ścieżkę albo silną nazwę:

```
<#@ assembly name="System.Xml" #>
```

 W nazwach ścieżek należy używać ich bezwzględnych nazw lub standardowych nazw makr. Na przykład:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 Listę makr można znaleźć w temacie [Common MACROS for Build Commands and Properties](https://msdn.microsoft.com/library/239bd708-2ea9-4687-b264-043f1febf98b).

 Dyrektywa zestawu nie ma wpływu na [wstępnie przetworzony szablon tekstu](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Aby uzyskać więcej informacji, zobacz [Dyrektywa zestawu T4](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>{1&gt;Przestrzenie nazw&lt;1}
 Dyrektywa „import” działa tak samo jak klauzula `using` w języku C# lub klauzula `imports` w języku Visual Basic. Umożliwia odwoływanie się z kodu do typów bez podawania w pełni kwalifikowanej nazwy:

```
<#@ import namespace="System.Xml" #>
```

 Można użyć tylu dyrektyw `assembly` i `import`, ilu trzeba. Trzeba je umieścić przed blokami tekstu i sterującymi.

 Aby uzyskać więcej informacji, zobacz [dyrektywa importowania T4](../modeling/t4-import-directive.md).

### <a name="Include"></a>Dołączanie kodu i tekstu
 Dyrektywa `include` wstawia tekst z innego pliku szablonu. Na przykład poniższa dyrektywa spowoduje wstawienie zawartości pliku `test.txt`.

 `<#@ include file="c:\test.txt" #>`

 Dołączona zawartość jest przetwarzana prawie tak, jakby była częścią dołączającego szablonu tekstu. Można jednak dołączyć plik, który zawiera blok cech klasy `<#+...#>`, nawet jeśli po dyrektywie „include” następuje zwykły tekst i standardowe bloki sterujące.

 Aby uzyskać więcej informacji, zobacz [T4 include dyrektywy](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Metody narzędziowe
 Istnieją różne metody, np. `Write()`, które są zawsze dostępne w bloku sterującym. Są wśród nich m.in. metody do stosowania wcięć w danych wyjściowych oraz zgłaszania błędów.

 Można także napisać własny zestaw metod narzędziowych.

 Aby uzyskać więcej informacji, zobacz [metody narzędziowe szablonu tekstu](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Przekształcanie danych i modeli
 Najbardziej przydatnym zastosowaniem szablonu tekstu jest generowanie materiału na podstawie zawartości źródła takiego jak model, baza danych lub plik danych. Szablon wyodrębnia i reformatuje dane. Kolekcja szablonów może przekształcić takie źródło w wiele plików.

 Istnieją różne techniki odczytywania pliku źródłowego.

 **Odczytaj plik w szablonie tekstowym**. Jest to najprostszy sposób wprowadzenia danych do szablonu:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Załaduj plik jako model nawigacji**. Bardziej zaawansowaną metodą jest odczyt danych jako modelu, po którym może się poruszać kod źródłowy szablonu tekstu. Na przykład można wczytać plik XML i nawigować po nim przy użyciu wyrażeń XPath. Można również użyć [XSD. exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) , aby utworzyć zestaw klas, za pomocą których można odczytywać dane XML.

 **Edytuj plik modelu w diagramie lub formularzu.** [!INCLUDE[dsl](../includes/dsl-md.md)] udostępnia narzędzia, które pozwalają edytować model jako diagram lub formularz systemu Windows. Ułatwia to przedyskutowanie modelu z użytkownikami wygenerowanej aplikacji. [!INCLUDE[dsl](../includes/dsl-md.md)] tworzy również zestaw klas o jednoznacznie określonym typie, które odzwierciedlają strukturę modelu. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

 **Użyj modelu UML**. Kod można wygenerować z modelu UML. Rozwiązanie ma tę zaletę, że model można edytować jako diagram w znanej notacji. Ponadto nie trzeba projektować diagramu. Aby uzyskać więcej informacji, zobacz [generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Względne ścieżki plików w szablonach czasu projektowania
 Jeśli chcesz odwołać się do pliku w lokalizacji względem szablonu tekstu, w [szablonie tekstu czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md)Użyj `this.Host.ResolvePath()`. Ponadto w dyrektywie `hostspecific="true"` trzeba ustawić wartość `template`:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>

```

 Można również wykorzystywać inne usługi udostępniane przez hosta. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu Visual Studio lub innych hostów z szablonu](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Szablony tekstu czasu projektowania uruchamiane w oddzielnej domenie aplikacji
 Należy pamiętać, że [szablon tekstu czasu projektowania](../modeling/design-time-code-generation-by-using-t4-text-templates.md) działa w domenie aplikacji, która jest oddzielona od głównej aplikacji. W większości przypadków nie ma to znaczenia, jednak w pewnych skomplikowanych przypadkach mogą wystąpić ograniczenia. Na przykład aby można było przekazać dane między szablonem a osobną usługą, usługa musi udostępniać interfejs API obsługujący serializację.

 (To nie jest prawdą od [szablonu tekstu w czasie wykonywania](../modeling/run-time-text-generation-with-t4-text-templates.md), który zawiera kod, który jest kompilowany wraz z resztą kodu).

## <a name="editing-templates"></a>Edytowanie szablonów
 Z internetowej galerii menedżera rozszerzeń można pobrać wyspecjalizowane edytory szablonów tekstu. W menu **Narzędzia** kliknij pozycję **Menedżer rozszerzeń**. Kliknij pozycję **Galeria online**, a następnie użyj narzędzia wyszukiwania.

## <a name="related-topics"></a>Tematy pokrewne

|Zadanie|Temat|
|----------|-----------|
|Pisanie szablonu.|[Zalecenia dotyczące pisania szablonów tekstowych T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Generowanie tekstu przy użyciu kodu programu.|[Struktura szablonu tekstu](../modeling/writing-a-t4-text-template.md)|
|Generowanie plików w rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Uruchom Generowanie tekstu poza [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Przekształć dane w postaci języka specyficznego dla domeny.|[Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)|
|Napisz dyrektywy procesorów, którą należy przekształcić źródła danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|
