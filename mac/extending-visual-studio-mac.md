---
title: Rozszerzanie programu Visual Studio dla komputerów Mac
description: Program Visual Studio dla komputerów Mac funkcje i możliwości można rozszerzyć za pomocą modułów o nazwie pakiety rozszerzeń. Pierwsza część tego przewodnika tworzy prosty programu Visual Studio pakiet rozszerzeń dla komputerów Mac do wstawienia datę i godzinę do dokumentu. Drugiej części tego przewodnika przedstawiono podstawy system pakietu rozszerzeń i niektóre z podstawowych interfejsów API, które stanowią podstawę programu Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 3465ef29ca732cd26c03919082052d8b26a83ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983166"
---
# <a name="extending-visual-studio-for-mac"></a>Rozszerzanie programu Visual Studio dla komputerów Mac

Program Visual Studio for Mac zawiera zestaw modułów o nazwie *pakiety rozszerzeń*. Pakiety rozszerzeń umożliwia wprowadzenie nowych funkcji programu Visual Studio dla komputerów Mac, takie jak obsługa dodatkowych języków lub nowego szablonu projektu.

Pakiety rozszerzeń opracowano na podstawie *rozszerzenia* punktów inne pakiety rozszerzeń. Punkty rozszerzenia symboli zastępczych dla obszarów, które można rozwijać, takich jak menu lub listę poleceń środowiska IDE. Pakiet rozszerzenia można tworzyć z punktu rozszerzenia, rejestrując węzła danych ze strukturą, nazywana rozszerzeniem, takie jak nowy element menu lub nowego polecenia. Każdy punkt rozszerzenia akceptuje niektórych rodzajów rozszerzeń, takich jak *polecenia*, *konsola*, lub *FileTemplate*. Moduł, który zawiera punkty rozszerzenia jest wywoływana *dodatku hosta*, jak można rozszerzyć przez inne pakiety rozszerzeń.

Aby dostosować Visual Studio dla komputerów Mac, można utworzyć pakietu rozszerzenia, która sprawia, że z punktów rozszerzenia zawarte w dodatku do hostów w ramach istniejących bibliotek w programie Visual Studio dla komputerów Mac, jak pokazano na poniższym diagramie:

![Architektura dodatków](media/extending-visual-studio-mac-addin1.png)

Aby pakiet rozszerzenia do tworzenia w programie Visual Studio dla komputerów Mac musi mieć rozszerzenia, które opracowano na podstawie istniejące punkty rozszerzenia programu Visual Studio dla komputerów Mac środowiska IDE. Gdy pakiet rozszerzenia opiera się na punkt rozszerzenia zdefiniowane na hoście dodatek, jest nazywany ma _zależności_ korzystać z tego pakietu rozszerzenia.

Zaletą ten projekt jest, czy Visual Studio for Mac jest rozszerzalny — istnieje wiele punktów rozszerzenia, które mogą być wbudowane w system za pomocą niestandardowego rozszerzenia pakietów. Bieżące pakiety rozszerzeń przykłady obsługi C# i F#debugera narzędzia i szablony projektów.

> [!NOTE]
> **Uwaga**: Jeśli masz projekt dodatku producent, który został utworzony przed Maker dodatek 1.2, chcesz przeprowadzić migrację projektu, co zostało opisane w krokach [tutaj](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

W tej sekcji omówiono różne pliki, generowane przez twórcę dodatku i wymaga dane rozszerzenie polecenia.

## <a name="attribute-files"></a>Atrybut plików

Pakiety rozszerzeń są przechowywane metadane dotyczące ich nazwy, wersji, zależności i inne informacje w języku C# atrybutów. Twórca dodatku tworzy dwa pliki `AddinInfo.cs` i `AssemblyInfo.cs` przechowywać i organizować te informacje. Pakiety rozszerzeń musi mieć unikatowy identyfikator i przestrzeń nazw określona w ich *atrybutu Addin*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Pakiety rozszerzeń również zadeklarować zależności na pakietów rozszerzeń, których właścicielem punktów rozszerzeń, które są podłączane. Te są automatycznie określane w czasie kompilacji.

Ponadto dodatkowe informacje można dodać za pomocą dodatku węzeł odniesienia w konsoli rozwiązania dla projektu, jak pokazano w poniższej ilustracji:

![Wstaw datę zrzut ekranu](media/extending-visual-studio-mac-addin13.png)

Mają również odpowiadające im `assembly:AddinDependency` atrybuty dodawane w czasie kompilacji. Po deklaracji metadanych i zależności w miejscu, można skoncentrować się na podstawowe bloki konstrukcyjne pakietu rozszerzenia.

## <a name="extensions-and-extension-points"></a>Rozszerzenia i punkty rozszerzenia

Punkt rozszerzenia jest symbolem zastępczym, który definiuje strukturę danych (typ), podczas rozszerzenie definiuje danych, który jest zgodny do struktury, określony przez punkt określonego rozszerzenia. Punkty rozszerzenia Określ, jaki typ rozszerzenia mogą akceptować w jego deklaracji. Rozszerzenia są zadeklarowane za pomocą nazwy typu lub ścieżki rozszerzenia. Zobacz [odwołania punktu rozszerzenia](https://github.com/mono/mono-addins/wiki/Extension-Points) dla uzyskać szczegółowe informacje na temat tworzenia punktu rozszerzenia, które są potrzebne.

Architektura punktu rozszerzenia/rozszerzenia przechowuje rozwoju Visual Studio dla komputerów Mac, szybka, modularna.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozszerzenia poleceń

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Rozszerzenia poleceń są rozszerzenia, które wskazują na metody, które są wywoływane za każdym razem, gdy jest ono wykonywane.

Rozszerzenia poleceń są definiowane przez dodawanie wpisów do `/MonoDevelop/Ide/Commands` punktu rozszerzenia. Zdefiniowaliśmy nasze rozszerzenie w `Manifest.addin.xml` następującym kodem:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Atrybut ścieżki, która określa punkt rozszerzenia, że jest ona w tym przypadku podłączania, zawiera węzeł rozszerzenia `/MonoDevelop/Ide/Commands/Edit`. Ponadto działa jako węzeł nadrzędny węzła do polecenia. Węzeł polecenie ma następujące atrybuty:

* **Identyfikator** — Określa identyfikator dla tego polecenia. Identyfikatory poleceń musi być zadeklarowany jako elementy członkowskie wyliczenia i służą do łączenia poleceń do CommandItems.
* **_etykieta** — tekst, który ma być wyświetlany w menu.
* **_opis** — tekst, który ma być wyświetlany jako etykietka narzędzia dla przycisków paska narzędzi.
* **defaultHandler** -Określa `CommandHandler` klasę, która obsługuje polecenie

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Rozszerzenie CommandItem, które podłącza się do `/MonoDevelop/Ide/MainMenu/Edit` punktu rozszerzenia przedstawionej w poniższym fragmencie kodu:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem umieszcza polecenie określonego w atrybucie jego identyfikator do menu. Rozszerza to CommandItem `/MonoDevelop/Ide/MainMenu/Edit` punktu rozszerzenia, co sprawia, że etykieta polecenia pojawiają się w **Menu Edycja**. Należy pamiętać, że **identyfikator** CommandItem odpowiada identyfikator węzła polecenia `InsertDate`. Jeśli masz zamiar usunąć CommandItem **Wstaw datę** znikała opcję z Menu Edycja.

### <a name="command-handlers"></a>Programy obsługi poleceń

`InsertDateHandler` Jest rozszerzeniem `CommandHandler` klasy. Zastępuje ona dwie metody `Update` i `Run`. `Update` Metody jest wykonywane zapytanie zawsze, gdy polecenie jest wyświetlane w menu lub wykonywane przy użyciu klawiszy. Zmieniając obiekt informacji, można wyłączyć polecenie lub je ukryć, wypełnianie tablicy polecenia i nie tylko. To `Update` metoda wyłącza polecenie, jeśli nie można odnaleźć aktywnego *dokumentu* z *TextEditor* umożliwia wstawianie tekstu do:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Wystarczy zastąpić `Update` metody, gdy masz logikę specjalną, włączanie lub ukrywania polecenia. `Run` Metoda jest wykonywana w każdym przypadku, gdy użytkownik wykonuje polecenie, które występuje w tym przypadku, gdy użytkownik wybierze polecenie menu Edycja. Ta metoda wstawia daty i godziny w karetki w edytorze tekstu:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Zadeklaruj typ polecenia jako element członkowski wyliczenia w ramach `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

To wiąże ze sobą, polecenie i CommandItem — CommandItem wywołuje polecenie, w przypadku wybrania CommandItem z **Menu Edycja**.

## <a name="ide-apis"></a>Interfejsy API w środowisku IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Aby uzyskać informacji na temat zakresu obszarów, które są dostępne dla rozwoju, zobacz [odwołanie do rozszerzenia drzewa](http://monodevelop.com/Developers/Articles/Extension_Tree_Reference) i [omówienie interfejsu API](http://monodevelop.com/Developers/Articles/API_Overview). Podczas tworzenia pakietów rozszerzeń zaawansowanej, również dotyczyć [artykułów dla deweloperów](http://monodevelop.com/Developers/Articles). Poniżej przedstawiono skróconą listę obszarów do dostosowywania:

* Okienka
* Schematy powiązań klawiszy
* Zasady
* Programy formatujące kodu
* Formaty plików projektu
* Preferencje paneli
* Opcje paneli
* Protokoły debugera
* Wizualizatory debugera
* Układ obszaru roboczego
* Węzły drzewa konsoli rozwiązania
* Marginesy Edytor źródła
* Aparaty testów jednostkowych
* Generatory kodu
* Fragmenty kodu
* Platformy docelowe
* Docelowe środowisko uruchomieniowe
* Klastry Wirtualne zaplecza
* Refaktoryzacja
* Wykonanie procedury obsługi
* Wyróżnianie składni

## <a name="additional-information"></a>Dodatkowe informacje

> [!NOTE]
> Obecnie pracujemy nad ulepszaniem scenariuszy rozszerzalności programu Visual Studio dla komputerów Mac. Jeśli tworzysz rozszerzeń i uzyskać dodatkowe informacje lub chcesz przekazać opinię, wypełnij [programu Visual Studio do tworzenia rozszerzenia Mac](https://aka.ms/vsmac-extensions-survey) formularza.

## <a name="see-also"></a>Zobacz także

- [Programowanie rozszerzeń programu Visual Studio (na Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)