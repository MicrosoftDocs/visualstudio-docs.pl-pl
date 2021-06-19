---
title: 'Wskazówki: generowanie kodu przy użyciu szablonów tekstowych'
description: Dowiedz się, że generowanie kodu umożliwia tworzenie silnie typowego kodu programu, który można łatwo zmienić po zmianie modelu źródłowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 22940fb86ab0cfd7262a3ca7845521847add2dff
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388129"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Przewodnik: generowanie kodu przy użyciu szablonów tekstowych

Generowanie kodu umożliwia tworzenie silnie typowego kodu programu, który można łatwo zmienić po zmianie modelu źródłowego. Porównaj to z alternatywną techniką pisania całkowicie ogólnego programu, który akceptuje plik konfiguracji, który jest bardziej elastyczny, ale skutkuje kodem, który nie jest tak łatwy do odczytania i zmiany ani nie ma tak dobrej wydajności. W tym przewodniku pokazano tę korzyść.

## <a name="typed-code-for-reading-xml"></a>Wpisany kod do odczytywania kodu XML

Przestrzeń nazw System.Xml udostępnia kompleksowe narzędzia do ładowania dokumentu XML, a następnie swobodnego nawigowania po nim w pamięci. Niestety wszystkie węzły mają ten sam typ, XmlNode. W związku z tym bardzo łatwo jest popełnić błędy programistyczne, takie jak oczekiwanie nieprawidłowego typu węzła podrzędnego lub nieprawidłowych atrybutów.

W tym przykładowym projekcie szablon odczytuje przykładowy plik XML i generuje klasy odpowiadające każdemu typowi węzła. W kodzie napisanym ręcznie można użyć tych klas do nawigowania po pliku XML. Aplikację można również uruchamiać na innych plikach, które używają tych samych typów węzłów. Przykładowy plik XML ma na celu podanie przykładów wszystkich typów węzłów, z których aplikacja ma się zajmować.

> [!NOTE]
> Aplikacja [xsd.exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe), która jest zawarta w Visual Studio, może generować silnie typowane klasy z plików XML. Jako przykład podano przedstawiony tutaj szablon.

Oto przykładowy plik:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<catalog>
  <artist id ="Mike%20Nash" name="Mike Nash Quartet">
    <song id ="MikeNashJazzBeforeTeatime">Jazz Before Teatime</song>
    <song id ="MikeNashJazzAfterBreakfast">Jazz After Breakfast</song>
  </artist>
  <artist id ="Euan%20Garden" name="Euan Garden">
    <song id ="GardenScottishCountry">Scottish Country Garden</song>
  </artist>
</catalog>
```

W projekcie, który konstruuje ten przewodnik, możesz napisać kod, taki jak poniższy, a funkcja IntelliSense wyświetla monit o poprawny atrybut i nazwy podrzędne podczas wpisywania:

```csharp
Catalog catalog = new Catalog(xmlDocument);
foreach (Artist artist in catalog.Artist)
{
  Console.WriteLine(artist.name);
  foreach (Song song in artist.Song)
  {
    Console.WriteLine("   " + song.Text);
  }
}
```

Porównaj to z nietypiowym kodem, który możesz napisać bez szablonu:

```csharp
XmlNode catalog = xmlDocument.SelectSingleNode("catalog");
foreach (XmlNode artist in catalog.SelectNodes("artist"))
{
    Console.WriteLine(artist.Attributes["name"].Value);
    foreach (XmlNode song in artist.SelectNodes("song"))
    {
         Console.WriteLine("   " + song.InnerText);
     }
}
```

W silnie typie wersji zmiana schematu XML powoduje zmiany w klasach. Kompilator wyróżnia części kodu aplikacji, które należy zmienić. W nietypiowej wersji, która używa ogólnego kodu XML, nie ma takiej obsługi.

W tym projekcie pojedynczy plik szablonu jest używany do generowania klas, które sprawiają, że typowana wersja jest możliwa.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

### <a name="create-or-open-a-c-project"></a>Tworzenie lub otwieranie projektu w języku C#

Tę technikę można zastosować do dowolnego projektu kodu. W tym przewodniku jest używany projekt w języku C#, a na potrzeby testowania używamy aplikacji konsolowej.

1. W menu **File (Plik)** kliknij pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

2. Kliknij węzeł **Visual C#,** a następnie w **okienku Szablony** kliknij pozycję **Aplikacja konsolowa.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Dodawanie prototypowego pliku XML do projektu

Celem tego pliku jest dostarczenie przykładów typów węzłów XML, które aplikacja ma mieć możliwość odczytu. Może to być plik, który będzie używany do testowania aplikacji. Szablon będzie tworzyć klasę języka C# dla każdego typu węzła w tym pliku.

Plik powinien być częścią projektu, aby szablon był w stanie go odczytać, ale nie będzie wbudowany w skompilowaną aplikację.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj,** a następnie kliknij **pozycję Nowy element.**

2. W **oknie dialogowym Dodawanie** nowego elementu wybierz pozycję **Plik XML** w **okienku** Szablony.

3. Dodaj przykładową zawartość do pliku.

4. W tym przewodniku nadaj plikowi nazwę `exampleXml.xml` . Ustaw zawartość pliku na xml pokazaną w poprzedniej sekcji.

### <a name="add-a-test-code-file"></a>Dodawanie pliku kodu testowego

Dodaj plik C# do projektu i zapisz w nim przykładowy kod, który chcesz mieć możliwość zapisu. Na przykład:

```csharp
using System;
namespace MyProject
{
  class CodeGeneratorTest
  {
    public void TestMethod()
    {
      Catalog catalog = new Catalog(@"..\..\exampleXml.xml");
      foreach (Artist artist in catalog.Artist)
      {
        Console.WriteLine(artist.name);
        foreach (Song song in artist.Song)
        {
          Console.WriteLine("   " + song.Text);
} } } } }
```

Na tym etapie kompilacja tego kodu nie powiedzie się. Podczas pisania szablonu wygeneruje się klasy, które umożliwią mu powodzenie.

Bardziej kompleksowy test może sprawdzić dane wyjściowe tej funkcji testowej względem znanej zawartości przykładowego pliku XML. Jednak w tym przewodniku będziemy zadowoleni, gdy zostanie skompilowana metoda testowa.

### <a name="add-a-text-template-file"></a>Dodawanie pliku szablonu tekstowego

Dodaj plik szablonu tekstowego i ustaw rozszerzenie wyjściowe *na cs.*

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy element**.

2. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję Szablon **tekstowy** w **okienku** Szablony.

    > [!NOTE]
    > Upewnij się, że dodasz szablon tekstowy, a nie wstępnie przetworzony szablon tekstowy.

3. W pliku w dyrektywie template zmień atrybut `hostspecific` na `true` .

     Ta zmiana umożliwi kodowi szablonu uzyskanie dostępu do Visual Studio usług.

4. W dyrektywie output zmień atrybut rozszerzenia na ".cs", aby szablon wygenerował plik C#. W Visual Basic projektu zmień go na ".vb".

5. Zapisz plik. Na tym etapie plik szablonu tekstowego powinien zawierać następujące wiersze:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Zwróć uwagę, że plik cs pojawia się Eksplorator rozwiązań jako podmiot zależny pliku szablonu. Możesz go wyświetlić, klikając pozycję [+] obok nazwy pliku szablonu. Ten plik jest generowany na podstawie pliku szablonu za każdym razem, gdy zapisujesz lub przenosisz fokus z pliku szablonu. Wygenerowany plik zostanie skompilowany w ramach projektu.

Dla wygody podczas opracowywania pliku szablonu rozmieść okna pliku szablonu i wygenerowanego pliku, aby można było je zobaczyć obok siebie. Dzięki temu natychmiast zobaczysz dane wyjściowe szablonu. Zauważysz również, że gdy szablon wygeneruje nieprawidłowy kod C#, błędy pojawią się w oknie komunikatu o błędzie.

Wszelkie zmiany, które wykonujesz bezpośrednio w wygenerowanym pliku, zostaną utracone przy każdym zapisaniu pliku szablonu. W związku z tym należy unikać edytowania wygenerowanego pliku lub edytować go tylko w przypadku krótkich eksperymentów. Czasami warto wypróbować krótki fragment kodu w wygenerowanym pliku, w którym działa funkcja IntelliSense, a następnie skopiować go do pliku szablonu.

## <a name="develop-the-text-template"></a>Opracowywanie szablonu tekstowego

Zgodnie z najlepszymi poradami na temat projektowania zwinnego opracujemy szablon w małych krokach, usuwając niektóre błędy z każdym przyrostem, dopóki kod testowy nie zostanie skompilowany i uruchomiony prawidłowo.

### <a name="prototype-the-code-to-be-generated"></a>Prototyp kodu do wygenerowania

Kod testowy wymaga klasy dla każdego węzła w pliku. W związku z tym niektóre błędy kompilacji utkną, jeśli dołączysz następujące wiersze do szablonu, a następnie zapiszemy go:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Dzięki temu można zobaczyć, co jest wymagane, ale deklaracje powinny być generowane na podstawie typów węzłów w przykładowym pliku XML. Usuń te eksperymentalne wiersze z szablonu.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generowanie kodu aplikacji na podstawie pliku XML modelu

Aby odczytać plik XML i wygenerować deklaracje klas, zastąp zawartość szablonu następującym kodem szablonu:

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#
 XmlDocument doc = new XmlDocument();
 // Replace this file path with yours:
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
#>
  public partial class <#= node.Name #> {}
<#
 }
#>
```

Zastąp ścieżkę pliku poprawną ścieżką dla projektu.

Zwróć uwagę na ograniczniki bloków kodu `<#...#>` . Te ograniczniki oddzielają fragment kodu programu, który generuje tekst. Ograniczniki bloków `<#=...#>` wyrażeń nawiasują wyrażenie, które może zostać ocenione jako ciąg.

Podczas pisania szablonu, który generuje kod źródłowy aplikacji, masz do czynienia z dwoma oddzielnymi tekstami programu. Program wewnątrz ograniczników bloku kodu jest uruchamiany za każdym razem, gdy zapisujesz szablon lub przenosisz fokus do innego okna. Wygenerowany tekst, który pojawia się poza ogranicznikami, jest kopiowany do wygenerowanego pliku i staje się częścią kodu aplikacji.

Dyrektywa zachowuje się jak odwołanie, dzięki `<#@assembly#>` czemu zestaw jest dostępny dla kodu szablonu. Lista zestawów widocznych w szablonie jest oddzielona od listy odwołań w projekcie aplikacji.

Dyrektywa działa jak instrukcja , umożliwiająca używanie krótkich nazw klas `<#@import#>` `using` w zaimportowanych przestrzeniach nazw.

Niestety, mimo że ten szablon generuje kod, tworzy deklarację klasy dla każdego węzła w przykładowym pliku XML, więc jeśli istnieje kilka wystąpień węzła, zostanie wyświetlonych kilka deklaracji utworu `<song>` klasy.

### <a name="read-the-model-file-then-generate-the-code"></a>Odczytaj plik modelu, a następnie wygeneruj kod

Wiele szablonów tekstowych jest zgodne ze wzorcem, w którym pierwsza część szablonu odczytuje plik źródłowy, a druga część generuje szablon. Musimy odczytać cały przykładowy plik, aby podsumować typy węzłów, które zawiera, a następnie wygenerować deklaracje klas. Potrzebny `<#@import#>` jest kolejny, aby można było użyć `Dictionary<>:`

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml"#>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
<#
 // Read the model file
 XmlDocument doc = new XmlDocument();
 doc.Load(@"C:\MySolution\MyProject\exampleXml.xml");
 Dictionary <string, string> nodeTypes =
        new Dictionary<string, string>();
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   nodeTypes[node.Name] = "";
 }
 // Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= nodeName #> {}
<#
 }
#>
```

### <a name="add-an-auxiliary-method"></a>Dodawanie metody pomocniczej

Blok sterowania cechami klas to blok, w którym można zdefiniować metody pomocnicze. Blok jest rozdzielany i `<#+...#>` musi być wyświetlany jako ostatni blok w pliku.

Jeśli wolisz, aby nazwy klas zaczynały się od wielkich liter, możesz zastąpić ostatnią część szablonu następującym kodem szablonu:

```
// Generate the code
 foreach (string nodeName in nodeTypes.Keys)
 {
#>
  public partial class <#= UpperInitial(nodeName) #> {}
<#
 }
#>
<#+
 private string UpperInitial(string name)
 { return name[0].ToString().ToUpperInvariant() + name.Substring(1); }
#>
```

Na tym etapie wygenerowany plik *cs* zawiera następujące deklaracje:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Więcej szczegółów, takich jak właściwości węzłów podrzędnych, atrybuty i tekst wewnętrzny, można dodać przy użyciu tej samej metody.

### <a name="access-the-visual-studio-api"></a>Uzyskiwanie dostępu do Visual Studio API

Ustawienie `hostspecific` atrybutu dyrektywy umożliwia szablonowi uzyskanie dostępu do Visual Studio `<#@template#>` API. Za pomocą tego szablonu można uzyskać lokalizację plików projektu, aby uniknąć używania bezwzględnej ścieżki pliku w kodzie szablonu.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
...
<#@ assembly name="EnvDTE" #>
...
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
// Open the prototype document.
XmlDocument doc = new XmlDocument();
doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
```

## <a name="complete-the-text-template"></a>Wypełnij szablon tekstowy

Następująca zawartość szablonu generuje kod, który umożliwia skompilowanie i uruchomienie kodu testowego.

```
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="System.Xml" #>
<#@ import namespace="System.Collections.Generic" #>
using System;using System.Collections.Generic;using System.Linq;using System.Xml;namespace MyProject{
<#
 // Map node name --> child name --> child node type
 Dictionary<string, Dictionary<string, XmlNodeType>> nodeTypes = new Dictionary<string, Dictionary<string, XmlNodeType>>();

 // The Visual Studio host, to get the local file path.
 EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
 // Open the prototype document.
 XmlDocument doc = new XmlDocument();
 doc.Load(System.IO.Path.Combine(dte.ActiveDocument.Path, "exampleXml.xml"));
 // Inspect all the nodes in the document.
 // The example might contain many nodes of the same type,
 // so make a dictionary of node types and their children.
 foreach (XmlNode node in doc.SelectNodes("//*"))
 {
   Dictionary<string, XmlNodeType> subs = null;
   if (!nodeTypes.TryGetValue(node.Name, out subs))
   {
     subs = new Dictionary<string, XmlNodeType>();
     nodeTypes.Add(node.Name, subs);
   }
   foreach (XmlNode child in node.ChildNodes)
   {
     subs[child.Name] = child.NodeType;
   }
   foreach (XmlNode child in node.Attributes)
   {
     subs[child.Name] = child.NodeType;
   }
 }
 // Generate a class for each node type.
 foreach (string className in nodeTypes.Keys)
 {
    // Capitalize the first character of the name.
#>
    partial class <#= UpperInitial(className) #>
    {      private XmlNode thisNode;      public <#= UpperInitial(className) #>(XmlNode node)       { thisNode = node; }

<#
    // Generate a property for each child.
    foreach (string childName in nodeTypes[className].Keys)
    {
      // Allow for different types of child.
      switch (nodeTypes[className][childName])
      {
         // Child nodes:
         case XmlNodeType.Element:
#>
      public IEnumerable<<#=UpperInitial(childName)#>><#=UpperInitial(childName) #>      {         get         {            foreach (XmlNode node in                thisNode.SelectNodes("<#=childName#>"))              yield return new <#=UpperInitial(childName)#>(node);       } }
<#
         break;
         // Child attributes:
         case XmlNodeType.Attribute:
#>
      public string <#=childName #>      { get { return thisNode.Attributes["<#=childName#>"].Value; } }
<#
         break;
         // Plain text:
         case XmlNodeType.Text:
#>
      public string Text  { get { return thisNode.InnerText; } }
<#
         break;
       } // switch
     } // foreach class child
  // End of the generated class:
#>
   }
<#
 } // foreach class

   // Add a constructor for the root class
   // that accepts an XML filename.
   string rootClassName = doc.SelectSingleNode("*").Name;
#>
   partial class <#= UpperInitial(rootClassName) #>   {      public <#= UpperInitial(rootClassName) #>(string fileName){        XmlDocument doc = new XmlDocument();        doc.Load(fileName);        thisNode = doc.SelectSingleNode("<#=rootClassName#>");}   }}
<#+
   private string UpperInitial(string name)
   {
      return name[0].ToString().ToUpperInvariant() + name.Substring(1);
   }
#>
```

### <a name="run-the-test-program"></a>Uruchamianie programu testowego

W głównej części aplikacji konsolowej następujące wiersze wykonają metodę testową. Naciśnij klawisz F5, aby uruchomić program w trybie debugowania:

```csharp
using System;
namespace MyProject
{
  class Program
  {
    static void Main(string[] args)
    {
      new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
    }
  }
}
```

### <a name="write-and-update-the-application"></a>Pisanie i aktualizowanie aplikacji

Aplikacja może być teraz napisana w silnie typicznym stylu przy użyciu wygenerowanych klas zamiast ogólnego kodu XML.

Po zmianie schematu XML można łatwo wygenerować nowe klasy. Kompilator poinformuj dewelopera, gdzie należy zaktualizować kod aplikacji.

Aby ponownie wygenerować klasy po zmianie przykładowego pliku XML, kliknij pozycję Przekształć wszystkie szablony na pasku **Eksplorator rozwiązań** narzędzi. 

## <a name="conclusion"></a>Podsumowanie

W tym przewodniku pokazano kilka technik i zalet generowania kodu:

- *Generowanie* kodu to tworzenie części kodu źródłowego aplikacji z *modelu*. Model zawiera informacje w formularzu dostosowanym do domeny aplikacji i może ulec zmianie w okresie istnienia aplikacji.

- Silne wpisywanie jest jedną z zalet generowania kodu. Chociaż model reprezentuje informacje w formularzu bardziej odpowiednim dla użytkownika, wygenerowany kod umożliwia innym częściom aplikacji radzenie sobie z informacjami przy użyciu zestawu typów.

- Funkcja IntelliSense i kompilator ułatwiają tworzenie kodu zgodnego ze schematem modelu, zarówno podczas pisania nowego kodu, jak i podczas aktualizowania schematu.

- Dodanie pojedynczego nieskomplikowanego pliku szablonu do projektu może zapewnić te korzyści.

- Szablon tekstowy może być szybko i przyrostowo opracowywany i testowany.

W tym przewodniku kod programu jest faktycznie generowany na podstawie wystąpienia modelu, reprezentatywnego przykładu plików XML, które aplikacja będzie przetwarzać. W bardziej formalnym podejściu schemat XML będzie danymi wejściowymi szablonu w postaci pliku xsd lub definicji języka specyficznego dla domeny. Takie podejście ułatwi szablonowi określenie właściwości, takich jak liczebność relacji.

## <a name="troubleshoot-the-text-template"></a>Rozwiązywanie problemów z szablonem tekstowym

Jeśli na liście błędów występują błędy przekształcania lub kompilacji szablonu lub **jeśli** plik wyjściowy nie został wygenerowany poprawnie, możesz rozwiązać problemy z szablonem tekstowym za pomocą technik opisanych w tece Generowanie plików za pomocą narzędzia [TextTransform.](../modeling/generating-files-with-the-texttransform-utility.md)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
