---
title: Rozszerzanie programu Visual Studio dla komputerów Mac
description: Funkcje i możliwości Visual Studio dla komputerów Mac można rozszerzyć za pomocą modułów o nazwie pakiety rozszerzeń. Pierwsza część tego przewodnika tworzy prosty pakiet rozszerzenia Visual Studio dla komputerów Mac, aby wstawić datę i godzinę do dokumentu. W drugiej części tego przewodnika przedstawiono podstawy systemu rozszerzenia oraz niektóre podstawowe interfejsy API, które tworzą podstawę Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/20/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 10beb7e95807a098cbe6efa89d02fdfa866bc2b8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583986"
---
# <a name="extending-visual-studio-for-mac"></a>Rozszerzanie programu Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac składa się z zestawu modułów o nazwie *pakiety rozszerzenia*. Za pomocą pakietów rozszerzeń można wprowadzać nowe funkcje do Visual Studio dla komputerów Mac, takie jak obsługa dodatkowego języka lub nowego szablonu projektu.

Pakiety rozszerzeń kompilują się z punktów *rozszerzenia* innych pakietów rozszerzenia. Punkty rozszerzenia to symbole zastępcze dla obszarów, które mogą być rozwinięte, na przykład menu lub listę poleceń IDE. Pakiet rozszerzeń można skompilować z punktu rozszerzenia, rejestrując węzeł danych strukturalnych nazywany rozszerzeniem, takim jak nowy element menu lub nowe polecenie. Każdy punkt rozszerzenia akceptuje pewne typy rozszerzeń, takie jak *Command*, *pad*lub *FileTemplate*. Moduł, który zawiera punkty rozszerzenia, jest nazywany *hostem dodatku*, ponieważ może zostać rozszerzony przez inne pakiety rozszerzeń.

Aby dostosować Visual Studio dla komputerów Mac, można utworzyć pakiet rozszerzenia, który kompiluje się z punktów rozszerzenia zawartych w hostach dodatków znajdujących się w istniejących już bibliotekach w Visual Studio dla komputerów Mac, jak pokazano na poniższym diagramie:

![Architektura dodatku](media/extending-visual-studio-mac-addin1.png)

Aby pakiet rozszerzenia mógł kompilować Visual Studio dla komputerów Mac, musi mieć rozszerzenia, które kompilują ze wstępnie istniejących punktów rozszerzenia w ramach Visual Studio dla komputerów Mac IDE. Gdy pakiet rozszerzenia jest oparty na punkcie rozszerzenia zdefiniowanym w hoście dodatków, jest on określany jako _zależność_   od tego pakietu rozszerzenia.

Zaletą tego projektu modularnego jest to, że Visual Studio dla komputerów Mac jest rozszerzalna — istnieje wiele punktów rozszerzenia, które można skompilować przy użyciu niestandardowych pakietów rozszerzeń. Przykłady bieżących pakietów rozszerzeń obejmują obsługę języków C# i F #, narzędzi debugera i szablonów projektów.

> [!NOTE]
> Jeśli masz projekt dodatku, który został utworzony przed dodatkiem Maker 1,2, należy przeprowadzić migrację projektu zgodnie z instrukcjami w [tym miejscu](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Ta sekcja analizuje różne pliki wygenerowane przez twórcę dodatku oraz dane wymagane przez rozszerzenie polecenia.

## <a name="attribute-files"></a>Pliki atrybutów

Pakiety rozszerzeń przechowują metadane dotyczące ich nazwy, wersji, zależności i innych informacji w atrybutach języka C#. Producent dodatku tworzy dwa pliki `AddinInfo.cs` i `AssemblyInfo.cs` zapisuje i organizuje te informacje. Pakiety rozszerzeń muszą mieć unikatowy identyfikator i przestrzeń nazw określone w ich * `Addin` atrybucie*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Pakiety rozszerzeń muszą również deklarować zależności w pakietach rozszerzeń, które są właścicielami punktów rozszerzenia, które są do nich przywoływane w czasie kompilacji.

Ponadto dodatkowe odwołania można dodać za pośrednictwem węzła odwołania dodatku w konsoli rozwiązania dla projektu, jak przedstawiono na poniższej ilustracji:

![Wstaw zrzut ekranu daty](media/extending-visual-studio-mac-addin13.png)

Mają także odpowiednie `assembly:AddinDependency` atrybuty dodawane w czasie kompilacji. Po umieszczeniu deklaracji metadanych i zależności można skoncentrować się na istotnych blokach konstrukcyjnych pakietu rozszerzenia.

## <a name="extensions-and-extension-points"></a>Rozszerzenia i punkty rozszerzenia

Punkt rozszerzenia jest symbolem zastępczym, który definiuje strukturę danych (typ), podczas gdy rozszerzenie definiuje dane, które są zgodne ze strukturą określoną przez określony punkt rozszerzenia. Punkty rozszerzenia określają typ rozszerzenia, które mogą być akceptowane w swojej deklaracji. Rozszerzenia są deklarowane przy użyciu nazw typów lub ścieżek rozszerzeń. Więcej szczegółowych informacji na temat tworzenia potrzebnych punktów rozszerzenia znajduje się w [dokumentacji punktu rozszerzenia](https://github.com/mono/mono-addins/wiki/Extension-Points) .

Architektura rozszerzenia/punktu rozszerzenia pozwala na szybkie i modularnie opracowywanie Visual Studio dla komputerów Mac.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozszerzenia poleceń

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Rozszerzenia poleceń to rozszerzenia wskazujące metody, które są wywoływane za każdym razem, gdy jest wykonywane.

Rozszerzenia poleceń są definiowane przez dodanie wpisów do `/MonoDevelop/Ide/Commands` punktu rozszerzenia. Nasze rozszerzenie zostało zdefiniowane w programie `Manifest.addin.xml` przy użyciu następującego kodu:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <Command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaultHandler="DateInserter.InsertDateHandler" />
</Extension>
```

Węzeł rozszerzenia zawiera atrybut Path, który określa punkt rozszerzenia, do którego jest podłączany, w tym przypadku `/MonoDevelop/Ide/Commands/Edit` . Ponadto działa jako węzeł nadrzędny polecenia. Węzeł polecenia ma następujące atrybuty:

* `id` -Określa identyfikator dla tego polecenia. Identyfikatory poleceń muszą być zadeklarowane jako elementy członkowskie wyliczenia i są używane do łączenia poleceń z CommandItems.
* `_label` — Tekst, który ma być wyświetlany w menu.
* `_description` -Tekst, który będzie wyświetlany jako etykietka narzędzia przycisków paska narzędzi.
* `defaultHandler` -Określa `CommandHandler` klasę, która umożliwia polecenie

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Rozszerzenie CommandItem, które jest podłączane do `/MonoDevelop/Ide/MainMenu/Edit` punktu rozszerzenia, przedstawiono w poniższym fragmencie kodu:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem umieszcza polecenie określone w jego atrybucie w `id` menu. CommandItem rozszerza `/MonoDevelop/Ide/MainMenu/Edit` punkt rozszerzenia, dzięki czemu etykieta polecenia pojawia się w **menu Edycja**. Należy zauważyć, że identyfikator w CommandItem odpowiada IDENTYFIKATORowi węzła polecenia, `InsertDate` . Po usunięciu CommandItem, opcja **Wstaw datę** zniknie z menu Edycja.

### <a name="command-handlers"></a>Programy obsługi poleceń

`InsertDateHandler`Jest to rozszerzenie `CommandHandler` klasy. Zastępuje dwie metody, `Update` i `Run` . `Update`Metoda jest wysyłana za każdym razem, gdy polecenie jest wyświetlane w menu lub wykonywane za pośrednictwem powiązań klucza. Zmieniając obiekt info, można wyłączyć polecenie lub uczynić go niewidocznym, wypełnić polecenia tablicowe i inne. Ta `Update` Metoda wyłącza polecenie, jeśli nie może znaleźć aktywnego *dokumentu* ze *textredaktorem* , aby wstawić tekst do:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Aby można było włączyć lub ukryć polecenie, wystarczy przesłonić `Update` metodę. `Run`Metoda jest wykonywana za każdym razem, gdy użytkownik wykonuje polecenie, co w tym przypadku ma miejsce, gdy użytkownik wybierze polecenie z menu Edycja. Ta metoda wstawia datę i godzinę do karetki w edytorze tekstu:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Zadeklaruj Typ polecenia jako element członkowski wyliczenia w `DateInserterCommands` :

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Polecenie i CommandItem są teraz powiązane ze sobą — CommandItem wywołuje polecenie, gdy CommandItem jest zaznaczone z **menu Edycja**.

## <a name="ide-apis"></a>Interfejsy API IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Aby uzyskać informacje na temat zakresu obszarów, które są dostępne do opracowania, zobacz [informacje dotyczące drzewa rozszerzeń](https://www.monodevelop.com/developers/articles/extension-tree-reference/) i [Omówienie interfejsu API](https://www.monodevelop.com/developers/articles/api-overview/). Podczas kompilowania pakietów rozszerzenia zaawansowanego należy również zapoznać się z [artykułami dla deweloperów](https://www.monodevelop.com/developers/articles/). Poniżej znajduje się częściowa lista obszarów do dostosowania:

* Konsol
* Schematy powiązań kluczy
* Zasady
* Elementy formatujące kod
* Formaty plików projektu
* Panele preferencji
* Panele opcji
* Protokoły debugera
* Wizualizatory debugera
* Układy obszarów roboczych
* Węzły drzewa konsoli rozwiązania
* Marginesy edytora źródła
* Silniki testów jednostkowych
* Generatory kodu
* Fragmenty kodu
* Platformy docelowe
* Docelowy środowisko uruchomieniowe
* Zaplecze OBWODu
* Refaktoryzacja
* Programy obsługi wykonywania
* Podświetlanie składni

## <a name="extending-the-new-editor"></a>Rozszerzanie nowego edytora

W Visual Studio dla komputerów Mac [wprowadzono nowy interfejs użytkownika natywnego edytora tekstu](/visualstudio/releasenotes/vs2019-mac-relnotes) w formacie kakao utworzony na podstawie tych samych warstw edytora z programu Visual Studio w systemie Windows.

Jedną z wielu zalet udostępniania edytora między programem Visual Studio i Visual Studio dla komputerów Mac jest ten, że kod przeznaczony dla edytora programu Visual Studio można dostosować do uruchamiania na Visual Studio dla komputerów Mac.

> [!NOTE]
> Nowy edytor obsługuje tylko pliki języka C#. Inne języki i formaty plików zostaną otwarte w starszym edytorze. Starsza wersja edytora implementuje jednak niektóre z opisanych poniżej interfejsów API edytora programu Visual Studio.

### <a name="visual-studio-editor-overview"></a>Przegląd edytora programu Visual Studio

![Architektura edytora programu Visual Studio](media/vs-editor-architecture.png)

Przed dotknięciem szczegółowych informacji o rozszerzeniu Visual Studio dla komputerów Mac, warto zapoznać się z bardziej szczegółowym edytorem udostępnionym. Poniżej przedstawiono kilka zasobów, które mogą pogłębić się w tym zrozumieniu:

* [Managed Extensibility Framework](/dotnet/framework/mef/index)
* [MEF w edytorze](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [Wewnątrz edytora](/visualstudio/extensibility/inside-the-editor)
* [Punkty rozszerzeń usługi językowej i edytora](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [Film wideo z wprowadzeniem do architektury edytora](https://www.youtube.com/watch?v=PkYVztKjO9A)

Dzięki tym zasobom podstawowe koncepcje, które należy znać, to [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview) :

* `ITextBuffer`Jest reprezentacją w pamięci tekstu, który można zmienić z upływem czasu. `CurrentSnapshot`Właściwość on `ITextBuffer` zwraca *niemodyfikowalną* reprezentację bieżącej zawartości buforu, wystąpienie elementu `ITextSnapshot` . Po dokonaniu edycji w buforze Właściwość CurrentSnapshot zostaje zaktualizowana do najnowszej wersji. Analizatory mogą sprawdzać migawkę tekstu w dowolnym wątku, a jej zawartość ma gwarancję, że nigdy nie ulegną zmianie.

* `ITextView`Jest reprezentacją interfejsu użytkownika, w jaki sposób `ITextBuffer` jest renderowany na ekranie w kontrolce edytora. Ma odwołanie do buforu tekstu, `Caret` `Selection` a także inne koncepcje związane z interfejsem użytkownika.

Dla danego elementu [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5) można pobrać powiązane z nim i `ITextBuffer` `ITextView` za pośrednictwem `Document.GetContent<ITextBuffer>()` i `Document.GetContent<ITextView>()` odpowiednio.

## <a name="additional-information"></a>Dodatkowe informacje

> [!NOTE]
> Obecnie pracujemy nad ulepszaniem scenariuszy rozszerzalności dla Visual Studio dla komputerów Mac. Jeśli tworzysz rozszerzenia i potrzebujesz dodatkowej pomocy lub informacji lub chcesz przekazać opinię, Wypełnij formularz [Visual Studio dla komputerów Mac tworzenia rozszerzenia](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) .

## <a name="see-also"></a>Zobacz też

- [Programowanie rozszerzeń programu Visual Studio (w systemie Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)