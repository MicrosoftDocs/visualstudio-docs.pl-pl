---
title: 'Przewodnik: Generowanie kodu przy użyciu szablonów tekstowych'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], generating application code
- walkthroughs [text templates]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5785dee0da189da4db7aad15ee8eff18b20ee49a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898089"
---
# <a name="walkthrough-generate-code-by-using-text-templates"></a>Przewodnik: Generowanie kodu przy użyciu szablonów tekstowych

Generowanie kodu można wygenerować kodu programu, która jest jednoznacznie określone i jeszcze można łatwo zmienić po zmianie modelu źródłowego. Kontrastu to przy użyciu alternatywnych techniki pisania absolutnie ogólny program, który akceptuje w pliku konfiguracji, który jest bardziej elastyczna, ale wyniki w kodzie, który nie jest tak łatwe do odczytu i zmienić, ani nie ma takich dobrą wydajność. W tym instruktażu pokazano tej korzyści.

## <a name="typed-code-for-reading-xml"></a>Kod maszynowy odczytywania pliku XML

Przestrzeń nazw System.Xml zawiera wszechstronne narzędzia dla ładowania dokumentu XML oraz kierując się go swobodnie w pamięci. Niestety wszystkie węzły mają tego samego typu XmlNode. W związku z tym jest bardzo proste popełnione programowania, takich jak oczekiwano niewłaściwy typ węzła podrzędnego lub nieprawidłowe atrybuty.

W tym przykładowym projekcie szablon odczytuje przykładowy plik XML i generuje klasy, które odpowiadają każdy typ węzła. W kodzie odręcznej można użyć w ramach tych zajęć, przejdź do pliku XML. Aplikację można również uruchomić na innych plików, które korzystają z tych samych typów węzła. Celem przykładowy plik XML ma zawierają przykłady wszystkie typy węzłów, które mają do czynienia z aplikacji.

> [!NOTE]
> Aplikacja [xsd.exe](http://go.microsoft.com/fwlink/?LinkId=178765), który jest dołączony do programu Visual Studio można wygenerować silnie typizowanych klas z plików XML. Szablon pokazany w tym miejscu jest dostarczany jako przykład.

Poniżej przedstawiono przykładowy plik:

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

W projekcie, tworzy w tym instruktażu, można napisać następujący kod i IntelliSense monituje o poprawne nazwy atrybutu i podrzędnych podczas wpisywania:

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

Natomiast to z kodem bez typu, który może zapisać bez szablonu:

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

Zmiany schematu XML powoduje w silnie typizowanej wersji zmiany do klas. Kompilator podświetla części kodu aplikacji, które należy zmienić. W wersji bez typu ogólnego kod XML jest używany Brak takiego obsługi.

W tym projekcie jednego pliku szablonu służy do generowania klasy, które umożliwiają typizowanej wersji.

## <a name="set-up-the-project"></a>Konfigurowanie projektu

### <a name="create-or-open-a-c-project"></a>Utwórz lub Otwórz projekt C#

Tej techniki można zastosować do dowolnego projektu kodu. W tym instruktażu wykorzystano projektu C# i na potrzeby testowania używamy aplikacji konsoli.

1.  Na **pliku** kliknij menu **New** a następnie kliknij przycisk **projektu**.

2.  Kliknij przycisk **Visual C#** węzła, a następnie w polu **szablony** okienku kliknij **aplikacji konsoli.**

### <a name="add-a-prototype-xml-file-to-the-project"></a>Dodaj plik XML prototypu do projektu

Celem tego pliku jest zapewnienie przykłady typy węzłów XML, które aplikację, aby można było odczytać. Może to być plik, który będzie używany na potrzeby testowania aplikacji. Szablon generuje klasy C# dla każdego typu węzła, w tym pliku.

Plik powinien być częścią projektu, tak aby można go odczytać szablonu, ale nie można zbudować w skompilowanej aplikacji.

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj** a następnie kliknij przycisk **nowy element**.

2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku XML** z **szablony** okienka.

3.  Dodaj zawartość próbki do pliku.

4.  W ramach tego przewodnika nadaj plikowi nazwę `exampleXml.xml`. Ustaw zawartość pliku do pliku XML, pokazano w poprzedniej sekcji.

### <a name="add-a-test-code-file"></a>Dodaj plik kodu testu

Dodaj plik języka C# do projektu i zapisać w nim próbki kodu, który chcesz mieć możliwość zapisywania. Na przykład:

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

Na tym etapie ten kod zakończy się niepowodzeniem skompilować. Podczas pisania szablonu spowoduje wygenerowanie klas, które umożliwiają go zakończyło się sukcesem.

Bardziej szczegółowe badania można sprawdzić wynik działania tej funkcji badania w znanych zawartości przykładowy plik XML. Ale w ramach tego przewodnika firma Microsoft będzie spełniony gdy kompiluje metody testowej.

### <a name="add-a-text-template-file"></a>Dodaj plik szablonu tekstu

Dodaj plik szablonu tekstu i Ustaw rozszerzenie danych wyjściowych *.cs*.

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy element**.

2.  W **Dodaj nowy element** wybierz okno dialogowe **szablon tekstowy** z **szablony** okienka.

    > [!NOTE]
    > Upewnij się, że dodano szablonu tekstu, a nie wstępnie przetworzony szablon tekstu.

3.  W pliku, w dyrektywie szablonu, należy zmienić `hostspecific` atrybutu `true`.

     Ta zmiana spowoduje włączenie kod szablonu w celu uzyskania dostępu do usług Visual Studio.

4.  W dyrektywie wyjścia Zmień rozszerzenie atrybut "CS", tak, aby szablon generuje plik języka C#. W projekcie języka Visual Basic może go zmienić na ".vb".

5.  Zapisz plik. Na tym etapie pliku szablonu tekstu powinien zawierać następujące wiersze:

    ```
    <#@ template debug="false" hostspecific="true" language="C#" #>
    <#@ output extension=".cs" #>
    ```

Należy zauważyć, że pliku CS pojawia się w Eksploratorze rozwiązań jako podmiot zależny firmy pliku szablonu. Można go było wyświetlić, klikając przycisk [+] obok nazwy pliku szablonu. Ten plik jest generowany na podstawie pliku szablonu Zapisz lub zespół odbiegać od pliku szablonu. Wygenerowany plik zostanie skompilowany w ramach projektu.

Dla wygody, podczas tworzenia pliku szablonu, Rozmieść okna tak, plik szablonu i pliku wygenerowanego, dzięki czemu można je wyświetlić obok siebie. Dzięki temu można natychmiast zobaczyć dane wyjściowe szablonu. Zauważysz również, czy gdy szablon generuje nieprawidłowy kod C#, błędy pojawią się w oknie komunikat o błędzie.

Wszelkie zmiany, które wykonać bezpośrednio w wygenerowanym pliku zostaną utracone przy każdym zapisaniu pliku szablonu. Użytkownik powinien w związku z tym należy unikać edytowania wygenerowany plik albo go edytować tylko w przypadku krótkich eksperymentów. Czasami warto spróbuj krótki fragment kodu w wygenerowanym pliku, w którym IntelliSense jest używany w operacji, a następnie skopiuj go do pliku szablonu.

## <a name="develop-the-text-template"></a>Tworzenie szablonu tekstowego

Następujące najlepsze porad na programowanie metodą agile firma Microsoft opracuje szablonu w proces na niewielkie etapy, niektóre błędy na każdy przyrost czyszczenie, dopóki nie kompiluje kod testu i działa poprawnie.

### <a name="prototype-the-code-to-be-generated"></a>Prototyp generowania kodu

Kod testu wymaga klasy dla każdego węzła w pliku. W związku z tym niektóre błędy kompilacji znikną Jeśli Dołącz te wiersze do szablonu, a następnie zapisz go:

```csharp
class Catalog {}
class Artist {}
class Song {}
```

Dzięki temu można zobaczyć, co jest wymagane, ale deklaracje powinny być generowane z typy węzłów w przykładowym pliku XML. Usuń te eksperymentalne wiersze z szablonu.

### <a name="generate-application-code-from-the-model-xml-file"></a>Generowanie kodu aplikacji na podstawie pliku XML modelu

Do odczytywania pliku XML i wygenerować deklaracje klas, Zastąp zawartość następującym kodem szablonu szablonu:

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

Zastąp ścieżkę pliku poprawną ścieżkę do projektu.

Zwróć uwagę, ograniczniki blok kodu `<#...#>`. Te ograniczniki dopasowywanie fragmentu kodu programu, która generuje tekst. Ograniczniki blok wyrażenia `<#=...#>` dopasowywanie wyrażenie, które mogą być obliczane na ciąg.

Podczas pisania szablonu, który generuje kod źródłowy aplikacji, masz do czynienia z tymi dokumentami oddzielnego programu. Program wewnątrz ograniczniki blok kodu jest uruchamiany przy każdej Zapisz szablon, lub Przenieś fokus do innego okna. Tekst, który generuje i pojawia się poza ograniczników, jest kopiowany do wygenerowanego pliku i staje się częścią kodu aplikacji.

`<#@assembly#>` Dyrektywy zachowuje się jak odwołanie, udostępniając zestaw kod szablonu. Lista zestawów widzianych przez szablon jest niezależna od listy odwołań w projekcie aplikacji.

`<#@import#>` Dyrektywy zachowuje się jak `using` instrukcji, co pozwala na wykorzystanie krótkich nazw klas importowanych przestrzeni nazw.

Niestety, mimo że ten szablon generuje kod, generuje deklarację klasy dla każdego węzła w przykładowy plik XML, aby w przypadku kilka wystąpień `<song>` węzła, pojawi się kilka deklaracji utworu klasy.

### <a name="read-the-model-file-then-generate-the-code"></a>Odczytywanie pliku modelu, a następnie generowania kodu

Wiele szablonów tekstowych postępuj zgodnie z wzorcem, w którym pierwsza część szablonu odczytuje plik źródłowy, a druga część generuje szablon. Należy odczytać całej przykładowy plik, aby podsumować typy węzłów, które zawiera, a następnie wygeneruj deklaracji klasy. Inny `<#@import#>` jest wymagana, dzięki czemu możemy użyć `Dictionary<>:`

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

### <a name="add-an-auxiliary-method"></a>Dodawanie metody pomocnicze

Blok sterowania cechami klasy to blok w którym można zdefiniować metody pomocnicze. Blok sterujący jest ujęty w `<#+...#>` i musi ona występować jako ostatniego bloku w pliku.

Jeśli wolisz nazwy klas zaczynać się wielką literą, można zastąpić ostatnią część szablonu poniższym kodem szablonu:

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

Na tym etapie wygenerowany *.cs* plik zawiera następujące deklaracje:

```csharp
public partial class Catalog {}
public partial class Artist {}
public partial class Song {}
```

Przy użyciu tej samej metody można dodać więcej szczegółów, takich jak właściwości dla węzłów podrzędnych, atrybuty i tekst wewnętrzny.

### <a name="access-the-visual-studio-api"></a>Dostęp do interfejsu API programu Visual Studio

Ustawienie `hostspecific` atrybutu `<#@template#>` dyrektywy umożliwia szablonu w celu uzyskania dostępu do interfejsu API programu Visual Studio. Ten szablon umożliwia to uzyskanie dostępu lokalizację plików projektu, aby unikać bezwzględną ścieżkę do pliku w kodzie szablonu.

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

## <a name="complete-the-text-template"></a>Wykonaj szablonu tekstowego

Następująca zawartość szablon generuje kod, który umożliwia kodu testu skompilować i uruchomić.

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

### <a name="run-the-test-program"></a>Uruchom test program

W oknie głównym aplikacji konsoli następujące wiersze wykona metody testowej. Naciśnij klawisz F5, aby uruchomić program w trybie debugowania:

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

### <a name="write-and-update-the-application"></a>Pisanie i zaktualizuj aplikację

Teraz można pisać aplikacji w stylu silnie typizowane przy użyciu wygenerowane klasy zamiast ogólnych kod XML.

Po zmianie schematu XML, można łatwo generować nowe klasy. Kompilator informuje dewelopera, gdzie należy zaktualizować kod aplikacji.

Aby ponownie wygenerować klas, gdy przykładowy plik XML zostanie zmieniony, kliknij przycisk **Przekształć wszystkie szablony** w **Eksploratora rozwiązań** paska narzędzi.

## <a name="conclusion"></a>Wniosek

W tym instruktażu przedstawiono kilka technik i korzyści wynikające z generowania kodu:

-   *Generowanie kodu* jest tworzenie części kodu źródłowego aplikacji *modelu*. Model zawiera informacje w postaci nadaje się do domeny aplikacji i mogą ulec zmianie w okresie istnienia aplikacji.

-   Silne wpisywanie jest jedną z zalet generowania kodu. Gdy model reprezentuje informacje w postaci bardziej odpowiednie dla użytkownika, wygenerowany kod umożliwia innych części aplikacji, aby poradzić sobie z informacjami o przy użyciu zestawu typów.

-   Funkcja IntelliSense i kompilator pomocne podczas tworzenia kodu, który jest zgodna ze schematem modelu, i kiedy piszesz nowy kod po zaktualizowaniu schematu.

-   Dodanie jednego prostotę pliku szablonu projektu może zapewnić te korzyści.

-   Szablon tekstowy można opracowany i przetestowany szybko i przyrostowo.

W tym instruktażu kodu programu faktycznie jest generowany z wystąpienia modelu reprezentatywna próbka pliki XML, które aplikacja może przetworzyć. W podejściu bardziej formalne schematu XML jest wprowadzanie do szablonu w postaci pliku XSD lub definicji języka specyficznego dla domeny. Takie podejście może ułatwić szablonu określić właściwości, takie jak liczebność relacji.

## <a name="troubleshoot-the-text-template"></a>Rozwiązywanie problemów z szablonu tekstowego

Jeśli wiesz już błędy kompilacji lub przekształcania szablonu w **lista błędów**, lub jeśli plik wyjściowy nie został poprawnie wygenerowany, można rozwiązać szablon tekstowy, za pomocą metod opisanych w [wygenerowany Pliki za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)