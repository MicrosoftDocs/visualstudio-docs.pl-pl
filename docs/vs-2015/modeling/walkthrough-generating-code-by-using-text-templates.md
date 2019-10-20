---
title: 'Przewodnik: generowanie kodu przy użyciu szablonów tekstowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
ms.assetid: 24602ade-baca-425e-a6ce-be09a2c7f7e1
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 29a455194e64ee30186941cb67b014170426cce0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659252"
---
# <a name="walkthrough-generating-code-by-using-text-templates"></a>Wskazówki: generowanie kodu przy użyciu szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generowanie kodu pozwala utworzyć kod programu, który jest silnie określony, i można go łatwo zmienić, gdy zmieni się model źródłowy. Różni się to za pomocą alternatywnej techniki pisania całkowicie ogólnego programu, który akceptuje plik konfiguracji, który jest bardziej elastyczny, ale powoduje, że nie jest to łatwe do odczytania i zmiany, ani nie ma takiej dobrej wydajności. Ten przewodnik przedstawia tę korzyść.

## <a name="typed-code-for-reading-xml"></a>Kod typu do odczytu XML
 Przestrzeń nazw System. xml zawiera kompleksowe narzędzia do ładowania dokumentu XML, a następnie swobodne nawigowanie w pamięci. Niestety wszystkie węzły mają ten sam typ, XmlNode. W związku z tym bardzo łatwo jest wprowadzić błędy programowania, takie jak oczekiwanie niewłaściwego typu węzła podrzędnego lub nieprawidłowe atrybuty.

 W tym przykładowym projekcie szablon odczytuje przykładowy plik XML i generuje klasy odpowiadające każdemu typowi węzła. W kodzie ręcznym można użyć tych klas do nawigowania w pliku XML. Możesz również uruchomić aplikację na innych plikach, które używają tych samych typów węzłów. Przykładowy plik XML ma dostarczyć przykłady wszystkich typów węzłów, z którymi aplikacja ma się zająć.

> [!NOTE]
> Aplikacja [XSD. exe](http://go.microsoft.com/fwlink/?LinkId=178765), która jest dołączona do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], może generować klasy z jednoznacznie określonymi typami z plików XML. Szablon przedstawiony tutaj jest podany jako przykład.

 Oto przykładowy plik:

```
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

 W projekcie, który to konstrukcje instruktażowe, można napisać kod, taki jak poniższy, a funkcja IntelliSense poprosi o poprawne nazwy atrybutu i elementów podrzędnych podczas wpisywania:

```
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

 Z kolei niewpisany kod, który można napisać bez szablonu:

```
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

 W przypadku silnie wpisanej wersji zmiany w schemacie XML spowodują zmiany w klasach. Kompilator podświetla części kodu aplikacji, które muszą zostać zmienione. W niewpisanej wersji, która używa ogólnego kodu XML, nie ma takiego wsparcia.

 W tym projekcie pojedynczy plik szablonu jest używany do generowania klas, które wprowadzają możliwej wersji.

## <a name="setting-up-the-project"></a>Konfigurowanie projektu

### <a name="create-or-open-a-c-project"></a>Utwórz lub Otwórz C# projekt
 Tę technikę można zastosować do dowolnego projektu kodu. W tym instruktażu C# jest używany projekt, a na potrzeby testowania używamy aplikacji konsolowej.

##### <a name="to-create-the-project"></a>Aby utworzyć projekt

1. W menu **plik** kliknij pozycję **Nowy** , a następnie kliknij pozycję **projekt**.

2. Kliknij węzeł  **C# wizualizacji** , a następnie w okienku **Szablony** kliknij pozycję **Aplikacja konsolowa.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Dodawanie prototypowego pliku XML do projektu
 Celem tego pliku jest dostarczenie próbek typów węzłów XML, które aplikacja ma mieć możliwość odczytywania. Może to być plik, który będzie używany do testowania aplikacji. Szablon spowoduje utworzenie C# klasy dla każdego typu węzła w tym pliku.

 Plik powinien być częścią projektu, dzięki czemu szablon może go odczytać, ale nie zostanie skompilowany do skompilowanej aplikacji.

##### <a name="to-add-an-xml-file"></a>Aby dodać plik XML

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj** , a następnie kliknij pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik XML** w okienku **Szablony** .

3. Dodaj przykładową zawartość do pliku.

4. W tym instruktażu Nazwij plik `exampleXml.xml`. Ustaw zawartość pliku jako plik XML przedstawiony w poprzedniej sekcji.

   .

### <a name="add-a-test-code-file"></a>Dodaj plik kodu testu
 Dodaj C# plik do projektu i napisz go jako przykładowy kod, który chcesz mieć możliwość zapisu. Na przykład:

```
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

 Na tym etapie ten kod nie zostanie skompilowany. Podczas pisania szablonu zostaną wygenerowane klasy, które umożliwią pomyślne zakończenie.

 Bardziej kompleksowy test może sprawdzić dane wyjściowe tej funkcji testowej względem znanej zawartości przykładowego pliku XML. Jednak w tym instruktażu zostanie spełnione, gdy metoda testowa zostanie skompilowana.

### <a name="add-a-text-template-file"></a>Dodaj plik szablonu tekstu
 Dodaj plik szablonu tekstu i ustaw rozszerzenie danych wyjściowych na ". cs".

##### <a name="to-add-a-text-template-file-to-your-project"></a>Aby dodać plik szablonu tekstu do projektu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz **szablon tekstowy** z okienka **Szablony** .

   > [!NOTE]
   > Upewnij się, że dodano szablon tekstu, a nie szablon wstępnie przetworzonych tekstu.

3. W pliku w dyrektywie szablonu Zmień atrybut `hostspecific`, aby `true`.

    Ta zmiana spowoduje, że kod szablonu uzyska dostęp do usług [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. W dyrektywie Output Zmień atrybut Extension na "CS", aby szablon generował C# plik. W projekcie Visual Basic należy zmienić go na ". vb".

5. Zapisz plik. Na tym etapie plik szablonu tekstu powinien zawierać następujące wiersze:

   ```
   <#@ template debug="false" hostspecific="true" language="C#" #>
   <#@ output extension=".cs" #>
   ```

   .

   Należy zauważyć, że plik. cs pojawia się w Eksplorator rozwiązań jako zależna część pliku szablonu. Zobaczysz ją, klikając [+] obok nazwy pliku szablonu. Ten plik jest generowany na podstawie pliku szablonu za każdym razem, gdy zapisujesz lub przenosisz fokus z pliku szablonu. Wygenerowany plik zostanie skompilowany w ramach projektu.

   Dla wygody podczas tworzenia pliku szablonu należy rozmieścić okna pliku szablonu i wygenerowanego pliku, aby można było zobaczyć je obok siebie. Pozwala to na natychmiastowe wyświetlenie danych wyjściowych szablonu. Zauważ również, że gdy szablon generuje nieprawidłowy C# kod, w oknie komunikatu o błędzie zostaną wyświetlone błędy.

   Wszelkie zmiany wykonywane bezpośrednio w wygenerowanym pliku zostaną utracone po każdym zapisaniu pliku szablonu. W związku z tym należy unikać edytowania wygenerowanego pliku lub edytować go tylko w przypadku krótkich eksperymentów. Czasami warto wypróbować krótki fragment kodu w wygenerowanym pliku, w którym funkcja IntelliSense jest w użyciu, a następnie skopiować ją do pliku szablonu.

## <a name="developing-the-text-template"></a>Programowanie szablonu tekstu
 Postępując zgodnie z najlepszymi wskazówkami dotyczącymi programowania Agile, opracujemy szablon w małych krokach, co spowoduje wyczyszczenie niektórych błędów w każdym przyrostie, aż kod testowy zostanie skompilowany i uruchomiony prawidłowo.

### <a name="prototype-the-code-to-be-generated"></a>Prototyp kodu do wygenerowania
 Kod testu wymaga klasy dla każdego węzła w pliku. W związku z tym niektóre błędy kompilacji zostaną dołączone do szablonu, a następnie zapisane:

```
class Catalog {}
class Artist {}
class Song {}
```

 Dzięki temu można zobaczyć, co jest wymagane, ale deklaracje powinny być generowane na podstawie typów węzłów w przykładowym pliku XML. Usuń te wiersze eksperymentalne z szablonu.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generuj kod aplikacji na podstawie pliku XML modelu
 Aby odczytać plik XML i wygenerować deklaracje klas, Zastąp zawartość szablonu następującym kodem szablonu:

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

 Zwróć uwagę na ograniczniki bloków kodu `<#...#>`. Te ograniczniki przenoszą fragment kodu programu, który generuje tekst. Ograniczniki bloku wyrażenia `<#=...#>` nawiasy w wyrażeniu, które może być oceniane jako ciąg.

 Podczas pisania szablonu, który generuje kod źródłowy aplikacji, użytkownik ma dwie osobne teksty programu. Program wewnątrz ograniczników bloków kodu jest uruchamiany za każdym razem, gdy zapisujesz szablon lub przenosisz fokus do innego okna. Wygenerowany tekst, który pojawia się poza ogranicznikami, jest kopiowany do wygenerowanego pliku i jest częścią kodu aplikacji.

 Dyrektywa `<#@assembly#>` zachowuje się jak odwołanie, co sprawia, że zestaw jest dostępny dla kodu szablonu. Lista zestawów widzianych przez szablon jest oddzielona od listy odwołań w projekcie aplikacji.

 Dyrektywa `<#@import#>` zachowuje się jak instrukcja `using`, co pozwala na używanie krótkich nazw klas w zaimportowanej przestrzeni nazw.

 Niestety, chociaż ten szablon generuje kod, generuje deklarację klasy dla każdego węzła w przykładowym pliku XML, tak że jeśli istnieje kilka wystąpień węzła `<song>`, zostanie wyświetlona kilka deklaracji utworu klasy.

### <a name="read-the-model-file-then-generate-the-code"></a>Odczytaj plik modelu, a następnie Wygeneruj kod
 Wiele szablonów tekstowych jest zgodnych ze wzorcem, w którym pierwsza część szablonu odczytuje plik źródłowy, a druga część generuje szablon. Musimy przeczytać cały przykładowy plik w celu podsumowania typów węzłów, które zawiera, a następnie wygenerowania deklaracji klas. Wymagana jest inna `<#@import#>`, aby można było używać `Dictionary<>:`

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

### <a name="add-an-auxiliary-method"></a>Dodaj metodę pomocniczą
 Blok sterowania funkcją klasy to blok, w którym można zdefiniować metody pomocnicze. Blok jest rozdzielony przez `<#+...#>` i musi znajdować się jako ostatni blok w pliku.

 Jeśli wolisz używać nazw klas zaczynających się wielką literą, możesz zastąpić ostatnią część szablonu następującym kodem szablonu:

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

 Na tym etapie wygenerowany plik CS zawiera następujące deklaracje:

```
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

 Więcej szczegółów, takich jak właściwości węzłów podrzędnych, atrybutów i tekstu wewnętrznego, można dodać przy użyciu tego samego podejścia.

### <a name="accessing-the-visual-studio-api"></a>Uzyskiwanie dostępu do interfejsu API programu Visual Studio
 Ustawienie atrybutu `hostspecific` dyrektywy `<#@template#>` umożliwia szablonowi uzyskanie dostępu do interfejsu API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Szablon może służyć do uzyskania lokalizacji plików projektu, aby uniknąć użycia bezwzględnej ścieżki pliku w kodzie szablonu.

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

## <a name="completing-the-text-template"></a>Wykonywanie szablonu tekstu
 Następująca zawartość szablonu generuje kod, który umożliwia kompilowanie i uruchamianie kodu testowego.

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

### <a name="running-the-test-program"></a>Uruchamianie programu testowego
 W głównej części aplikacji konsolowej w poniższych wierszach zostanie wykonana metoda testowa. Naciśnij klawisz F5, aby uruchomić program w trybie debugowania:

```
using System;
namespace MyProject
{ class Program
  { static void Main(string[] args)
    { new CodeGeneratorTest().TestMethod();
      // Allow user to see the output:
      Console.ReadLine();
} } }
```

### <a name="writing-and-updating-the-application"></a>Pisanie i aktualizowanie aplikacji
 Aplikację można teraz napisać w stylu o jednoznacznie określonym typie, używając wygenerowanych klas zamiast używać ogólnego kodu XML.

 Po zmianie schematu XML nowe klasy mogą być łatwo generowane. Kompilator przekaże deweloperowi, w którym należy zaktualizować kod aplikacji.

 Aby ponownie wygenerować klasy po zmianie przykładowego pliku XML, kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

## <a name="conclusion"></a>Wniosek
 W tym instruktażu przedstawiono kilka technik i korzyści wynikające z generowania kodu:

- *Generowanie kodu* to tworzenie części kodu źródłowego aplikacji z *modelu*. Model zawiera informacje w postaci dopasowanej do domeny aplikacji i może ulec zmianie w okresie istnienia aplikacji.

- Silne pisanie jest jedną z zalet generowania kodu. Chociaż model reprezentuje informacje w postaci bardziej odpowiednie dla użytkownika, wygenerowany kod umożliwia innym częściom aplikacji zaradzenie sobie z informacjami przy użyciu zestawu typów.

- Funkcja IntelliSense i kompilator ułatwiają tworzenie kodu, który jest zgodny ze schematem modelu, zarówno podczas pisania nowego kodu, jak i gdy schemat jest aktualizowany.

- Dodanie pojedynczego nieskomplikowanego pliku szablonu do projektu może zapewnić te korzyści.

- Szablon tekstowy można opracowywać i przetestować szybko i przyrostowo.

  W tym instruktażu kod programu jest faktycznie generowany na podstawie wystąpienia modelu, reprezentatywnego przykładu plików XML, które aplikacja będzie przetwarzać. W bardziej formalnym podejściu schemat XML będzie danymi wejściowymi szablonu w postaci pliku XSD lub definicji języka specyficznego dla domeny. Takie podejście ułatwia szablonowi określenie właściwości, takich jak liczebność relacji.

## <a name="troubleshooting-the-text-template"></a>Rozwiązywanie problemów z szablonem tekstu
 Jeśli widzisz błędy transformacji szablonu lub kompilacji w **Lista błędów**lub jeśli plik wyjściowy nie został prawidłowo wygenerowany, możesz rozwiązać problem z szablonem tekstu przy użyciu technik opisanych w temacie [generowanie plików przy użyciu TextTransform Narzędzie](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>Zobacz też
 [Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)
