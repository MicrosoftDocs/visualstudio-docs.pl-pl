---
title: Rozszerzanie programu Visual Studio dla komputerów Mac
description: Funkcje i funkcje programu Visual Studio for Mac można rozszerzyć o moduły o nazwie pakiety rozszerzeń. Pierwsza część tego przewodnika tworzy prosty pakiet rozszerzenia programu Visual Studio dla komputerów Mac, aby wstawić datę i godzinę do dokumentu. W drugiej części tego przewodnika przedstawiono podstawy systemu pakietów rozszerzeń i niektóre podstawowe interfejsy API, które tworzą podstawę programu Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/20/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: dd4db2502c65e9330bde5f475fc97b2e86a49e4a
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544026"
---
# <a name="extending-visual-studio-for-mac"></a>Rozszerzanie programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac składa się z zestawu modułów o nazwie *Pakiety rozszerzeń*. Pakiety rozszerzeń można użyć, aby wprowadzić nowe funkcje do programu Visual Studio dla komputerów Mac, takie jak obsługa dodatkowego języka lub nowego szablonu projektu.

Pakiety rozszerzeń kompilacji z punktów *rozszerzenia* innych pakietów rozszerzenia. Punkty rozszerzenia są symbolami zastępczymi dla obszarów, które można rozwinąć, takich jak menu lub lista poleceń IDE. Pakiet rozszerzenia można tworzyć z punktu rozszerzenia, rejestrując węzeł danych strukturalnych o nazwie rozszerzenie, takie jak nowy element menu lub nowe polecenie. Każdy punkt rozszerzenia akceptuje pewne typy rozszerzeń, takie jak *Command*, *Pad*lub *FileTemplate*. Moduł, który zawiera punkty rozszerzenia jest nazywany *hostem dodatku,* ponieważ może zostać rozszerzony o inne pakiety rozszerzeń.

Aby dostosować program Visual Studio dla komputerów Mac, można utworzyć pakiet rozszerzenia, który jest kompilacji z punktów rozszerzenia zawartych w hostach dodatków w istniejących bibliotekach w programie Visual Studio dla komputerów Mac, jak pokazano na poniższym diagramie:

![Architektura dodatku](media/extending-visual-studio-mac-addin1.png)

Aby pakiet rozszerzenia do kompilacji z programu Visual Studio dla komputerów Mac, musi mieć rozszerzenia, które kompilacji z istniejących punktów rozszerzenia w programie Visual Studio dla komputerów Mac IDE. Gdy pakiet rozszerzenia opiera się na punkt rozszerzenia zdefiniowane w hosta dodatku, mówi się, że _zależność_ od tego pakietu rozszerzenia.

Zaletą tej modułowej konstrukcji jest to, że visual studio dla komputerów Mac jest rozszerzalny — istnieje wiele punktów rozszerzenia, które mogą być oparte na niestandardowych pakietach rozszerzeń. Przykłady bieżących pakietów rozszerzenia obejmują obsługę języka C# i F#, narzędzia debugera i szablony projektu.

> [!NOTE]
> Jeśli masz projekt programu Add-in Maker, który został utworzony przed programem Add-in Maker 1.2, musisz przeprowadzić migrację projektu zgodnie z [poniższymi](https://mhut.ch/addinmaker/1.2)krokami.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

W tej sekcji omówiono różne pliki generowane przez program Add-in Maker i dane, które wymaga rozszerzenia polecenia.

## <a name="attribute-files"></a>Pliki atrybutów

Pakiety rozszerzeń przechowują metadane dotyczące ich nazwy, wersji, zależności i innych informacji w atrybutach języka C#. Program Add-in Maker tworzy `AddinInfo.cs` `AssemblyInfo.cs` dwa pliki oraz przechowuje i organizuje te informacje. Pakiety rozszerzeń muszą mieć unikatowy identyfikator i obszar nazw określony w ich * `Addin` atrybucie:*

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Pakiety rozszerzeń należy również zadeklarować zależności na pakiety rozszerzenia, które są właścicielami punktów rozszerzenia, które są podłączane do, które są automatycznie odwoływane w czasie kompilacji.

Ponadto dodatkowe odwołania można dodać za pośrednictwem węzła odwołania dodatku w konsoli rozwiązania dla projektu, jak pokazano na poniższej ilustracji:

![Wstaw datę zrzutu ekranu](media/extending-visual-studio-mac-addin13.png)

Mają również ich `assembly:AddinDependency` odpowiednie atrybuty dodane w czasie kompilacji. Po usunięciu metadanych i deklaracji zależności można skupić się na podstawowych blokach konstrukcyjnych pakietu rozszerzeń.

## <a name="extensions-and-extension-points"></a>Rozszerzenia i punkty rozszerzeń

Punkt rozszerzenia jest symbolem zastępczym, który definiuje strukturę danych (typ), podczas gdy rozszerzenie definiuje dane, które są zgodne ze strukturą określoną przez określony punkt rozszerzenia. Punkty rozszerzeń określają, jakiego typu rozszerzenia mogą zaakceptować w swojej deklaracji. Rozszerzenia są deklarowane przy użyciu nazw typów lub ścieżek rozszerzenia. Zobacz [odwołanie do punktu rozszerzenia,](https://github.com/mono/mono-addins/wiki/Extension-Points) aby uzyskać bardziej szczegółowe wyjaśnienie dotyczące tworzenia punktu rozszerzenia, którego potrzebujesz.

Architektura punktu rozszerzenia/rozszerzenia zapewnia szybki i modułowy rozwój programu Visual Studio dla komputerów Mac.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozszerzenia poleceń

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Rozszerzenia poleceń są rozszerzeniami, które wskazują na metody, które są wywoływane za każdym razem, gdy jest wykonywane.

Rozszerzenia poleceń są definiowane przez `/MonoDevelop/Ide/Commands` dodanie wpisów do punktu rozszerzenia. Zdefiniowaliśmy nasze `Manifest.addin.xml` rozszerzenie za pomocą następującego kodu:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <Command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaultHandler="DateInserter.InsertDateHandler" />
</Extension>
```

Węzeł rozszerzenia zawiera atrybut ścieżki, który określa punkt rozszerzenia, do który jest `/MonoDevelop/Ide/Commands/Edit`w tym przypadku podłączany. Ponadto działa jako węzeł nadrzędny do polecenia. Węzeł Polecenia ma następujące atrybuty:

* `id`- Określa identyfikator tego polecenia. Identyfikatory poleceń muszą być zadeklarowane jako elementy członkowskie wyliczenia i są używane do łączenia poleceń z commanditems.
* `_label`- Tekst, który ma być wyświetlany w menu.
* `_description`- Tekst, który ma być wyświetlany jako etykietka narzędzia dla przycisków paska narzędzi.
* `defaultHandler`- Określa `CommandHandler` klasę, która zasila polecenie

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Rozszerzenie CommandItem, które podłącza się do punktu `/MonoDevelop/Ide/MainMenu/Edit` rozszerzenia, jest zademonstrowane w następującym fragmentze kodu:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

A CommandItem umieszcza Command `id` określony w jego atrybut w menu. Ten element commanditem `/MonoDevelop/Ide/MainMenu/Edit` rozszerza punkt rozszerzenia, co sprawia, że etykieta polecenia pojawia się w **menu edycji**. Należy zauważyć, że identyfikator w CommandItem odpowiada identyfikatorowi węzła Command, `InsertDate`. Jeśli usuniesz CommandItem, opcja **Wstaw datę** zniknie z menu edycji.

### <a name="command-handlers"></a>Programy obsługi poleceń

Jest `InsertDateHandler` rozszerzeniem `CommandHandler` klasy. Zastępuje dwie metody `Update` i `Run`. Metoda `Update` jest wyszukiwana za każdym razem, gdy polecenie jest wyświetlane w menu lub wykonywane za pomocą powiązań kluczy. Zmieniając obiekt informacji, można wyłączyć polecenie lub uczynić go niewidocznym, wypełnić polecenia tablicowe i nie tylko. Ta `Update` metoda wyłącza polecenie, jeśli nie można znaleźć aktywnego *dokumentu* z *programem TextEditor,* do wstawiania tekstu do:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Wystarczy zastąpić metodę tylko `Update` wtedy, gdy masz specjalną logikę włączania lub ukrywania polecenia. Metoda `Run` jest wykonywana za każdym razem, gdy użytkownik wykonuje polecenie, które w tym przypadku występuje, gdy użytkownik wybierze polecenie z menu edycji. Ta metoda wstawia datę i godzinę w daszniku w edytorze tekstu:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Zadeklaruj typ polecenia jako `DateInserterCommands`element członkowski wyliczenia w obrębie:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Command i CommandItem są teraz powiązane ze sobą - CommandItem wywołuje polecenie, gdy commanditem jest zaznaczone z **menu edycji**.

## <a name="ide-apis"></a>Interfejsy API IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Aby uzyskać informacje na temat zakresu obszarów, które są dostępne do programowania, zobacz [odwołanie do drzewa rozszerzeń](https://www.monodevelop.com/developers/articles/extension-tree-reference/) i [omówienie interfejsu API](https://www.monodevelop.com/developers/articles/api-overview/). Podczas tworzenia zaawansowanych pakietów rozszerzeń, należy również zapoznać się z [artykułami deweloperów](https://www.monodevelop.com/developers/articles/). Poniżej znajduje się częściowa lista obszarów do dostosowania:

* Klocki
* Kluczowe schematy powiązania
* Zasady
* Formaty kodu
* Formaty plików projektu
* Panele preferencji
* Panele opcji
* Protokoły debugera
* Wizualizatory debugera
* Układy obszarów roboczych
* Węzły drzewa podkładek rozwiązania
* Marginesy edytora źródłowego
* Silniki testowe jednostkowe
* Generatory kodu
* Fragmenty kodu
* Platformy docelowe
* Docelowy czas wykonywania
* Tylne końcówki VCS
* Refaktoryzacja
* Programy obsługi wykonania
* Wyróżnianie składni

## <a name="extending-the-new-editor"></a>Rozszerzenie nowego edytora

Visual Studio dla komputerów Mac [wprowadza nowy natywny interfejs użytkownika edytora tekstu cocoa](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes) zbudowany na tych samych warstwach edytora z programu Visual Studio w systemie Windows.

Jedną z wielu zalet udostępniania edytora między programami Visual Studio i Visual Studio dla komputerów Mac jest to, że kod przeznaczony dla edytora Visual Studio można dostosować do uruchamiania w programie Visual Studio dla komputerów Mac.

> [!NOTE]
> Nowy edytor obsługuje tylko pliki języka C# w tej chwili. Inne języki i formaty plików zostaną otwarte w edytorze starszej wersji. Edytor starszej wersji implementuje jednak niektóre interfejsy API edytora Visual Studio opisane poniżej.

### <a name="visual-studio-editor-overview"></a>Omówienie edytora programu Visual Studio

![Architektura edytora programu Visual Studio](media/vs-editor-architecture.png)

Przed dotknięciem szczegółów rozszerzenia określonych w programie Visual Studio dla komputerów Mac, warto dowiedzieć się więcej o samym edytorze udostępnionym. Poniżej znajduje się kilka zasobów, które mogą pogłębić to zrozumienie:

* [Zarządzane ramy rozszerzalności](/dotnet/framework/mef/index)
* [MEF w redakcji](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [Wewnątrz edytora](/visualstudio/extensibility/inside-the-editor)
* [Punkty rozszerzeń usługi językowej i edytora](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [Wprowadzenie wideo do architektury edytora](https://www.youtube.com/watch?v=PkYVztKjO9A)

Z tych zasobów w ręku, podstawowe pojęcia, które [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) musisz [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview)znać są i:

* An `ITextBuffer` jest w pamięci reprezentacji tekstu, który można zmienić w czasie. Właściwość `CurrentSnapshot` `ITextBuffer` na zwraca *niezmienną* reprezentację bieżącej zawartości buforu, wystąpienie `ITextSnapshot`. Po dokonaniu edycji w buforze, CurrentSnapshot właściwość jest aktualizowana do najnowszej wersji. Analizatory można sprawdzić migawkę tekstu w dowolnym wątku i jego zawartość jest gwarantowana nigdy się nie zmieniać.

* Jest `ITextView` reprezentacją interfejsu użytkownika, jak `ITextBuffer` jest renderowany na ekranie w formancie edytora. Ma odwołanie do buforu tekstu, `Caret`a `Selection`także , i innych pojęć związanych z interfejsem użytkownika.

Dla danego [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5), można pobrać skojarzone `ITextBuffer` `ITextView` podstawowej i za pośrednictwem `Document.GetContent<ITextBuffer>()` i `Document.GetContent<ITextView>()` odpowiednio.

## <a name="additional-information"></a>Dodatkowe informacje

> [!NOTE]
> Obecnie pracujemy nad poprawą scenariuszy rozszerzalności programu Visual Studio dla komputerów Mac. Jeśli tworzysz rozszerzenia i potrzebujesz dodatkowej pomocy lub informacji lub chcesz przekazać opinię, wypełnij formularz [tworzenia rozszerzeń programu Visual Studio dla komputerów Mac.](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u)

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozszerzeń programu Visual Studio (w systemie Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
