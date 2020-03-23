---
title: Dołączanie pakietu NuGet do projektu
description: W tym dokumencie opisano, jak dołączyć pakiet NuGet w projekcie przy użyciu programu Visual Studio dla komputerów Mac. Przechodzi przez znajdowanie i pobieranie pakietu, a także wprowadzenie funkcji integracji IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74127238"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalowanie pakietów NuGet i zarządzanie nimi w programie Visual Studio dla komputerów Mac

Interfejs użytkownika Menedżera pakietów NuGet w programie Visual Studio dla komputerów Mac umożliwia łatwe instalowanie, odinstalowywanie i aktualizowanie pakietów NuGet w projektach i rozwiązaniach. Można wyszukiwać i dodawać pakiety do projektów .NET Core, ASP.NET Core i Xamarin.

W tym artykule opisano, jak dołączyć pakiet NuGet w projekcie i demonstruje łańcuch narzędzi, który sprawia, że proces bezproblemowe.

Aby uzyskać wprowadzenie do korzystania z programu NuGet w programie Visual Studio dla komputerów Mac, zobacz [Szybki start: Instalowanie i używanie pakietu w programie Visual Studio dla komputerów Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Znajdowanie i instalowanie pakietu

1. Po otwarciu projektu w programie Visual Studio dla **komputerów** Mac kliknij prawym przyciskiem myszy folder Zależności **(Folder Pakiety,** jeśli używasz projektu platformy Xamarin) w **panelu rozwiązania** i wybierz pozycję **Zarządzaj pakietami NuGet...**.

    ![Dodawanie nowej akcji kontekstu pakietu NuGet](media/nuget-walkthrough-packages-menu.png)

2. Spowoduje to uruchomienie okna **Zarządzanie pakietami NuGet.** Upewnij się, że źródło listy rozwijanej w lewym `nuget.org`górnym rogu okna dialogowego jest ustawiona na , tak aby przeszukiwać centralne repozytorium pakietów NuGet.

    ![Lista pakietów NuGet](media/nuget-walkthrough-add-packages1.png)

3. Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć `EntityFramework`określony pakiet, na przykład . Po znalezieniu pakietu, którego chcesz użyć, zaznacz go i kliknij przycisk **Dodaj pakiet,** aby rozpocząć instalację.

    ![Dodaj pakiet NuGet entityframework](media/nuget-walkthrough-add-packages2.png)

4. Po pobraniu pakietu zostanie on dodany do projektu. Rozwiązanie zmieni się w zależności od typu edytowanego projektu:

    **Projekty platformy Xamarin**
    * **Węzeł Odwołania** będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
    * Węzeł **Pakiety** wyświetla każdy pobrany pakiet NuGet. Pakiet można zaktualizować lub usunąć z tej listy.
    
    **Podstawowe projekty platformy .NET**

    * **Zależności > węzła NuGet** wyświetla każdy pobrany pakiet NuGet. Pakiet można zaktualizować lub usunąć z tej listy.

## <a name="using-nuget-packages"></a>Korzystanie z pakietów NuGet

Po dodaniu pakietu NuGet i zaktualizowano odwołania do projektu, można programować względem interfejsów API, tak jak w przypadku dowolnego odwołania do projektu.

Upewnij się, że `using` dodasz wszystkie wymagane dyrektywy do górnej części pliku:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualizowanie pakietów

Aktualizacje pakietu można wykonać wszystkie na raz, klikając prawym przyciskiem myszy węzeł **zależności** **(węzeł Pakiety** dla projektów platformy Xamarin) lub indywidualnie w każdym pakiecie. Gdy dostępna jest nowa wersja pakietu NuGet, ![pojawi się](media/nuget-walkthrough-update-icon.png)ikona aktualizacji w górę z kółkiem .

Kliknij prawym przyciskiem myszy **zależności,** aby uzyskać dostęp do menu kontekstowego i wybierz **pozycję Aktualizuj,** aby zaktualizować wszystkie pakiety:

![Menu Pakiety](media/nuget-walkthrough-packages-menu-update.png)

* **Zarządzanie pakietami NuGet** — otwiera okno, aby dodać więcej pakietów do projektu.
* **Aktualizacja** — sprawdza serwer źródłowy dla każdego pakietu i pobiera wszystkie nowsze wersje.
* **Przywracanie** — pobiera brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Opcje aktualizacji i przywracania są również dostępne na poziomie rozwiązania i mają wpływ na wszystkie projekty w rozwiązaniu.

### <a name="locating-outdated-packages"></a>Lokalizowanie nieaktualnych pakietów
Z konsoli rozwiązania można wyświetlić, jaka wersja pakietu jest aktualnie zainstalowana i kliknąć prawym przyciskiem myszy pakiet do aktualizacji.

![Menu Pakiety z opcjami Aktualizacji, Usuń, Odśwież](media/nuget-walkthrough-PackageMenu.png)

Zostanie również wyświetlone powiadomienie obok nazwy pakietu, gdy dostępna jest nowa wersja pakietu, więc możesz zdecydować, czy możesz go zaktualizować.

![Powiadomienie wyświetlane, gdy dostępna jest nowa wersja pakietu](media/nuget-walkthrough-package-update-available.png)

W wyświetlonym menu dostępne są dwie opcje:

* **Aktualizacja** — sprawdza serwer źródłowy i pobiera nowszą wersję (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołania projektu.

## <a name="manage-packages-for-the-solution"></a>Zarządzanie pakietami dla rozwiązania

Zarządzanie pakietami dla rozwiązania jest wygodnym sposobem pracy z wieloma projektami jednocześnie.

1. Kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Zarządzaj pakietami NuGet...**:

    ![Zarządzanie pakietami NuGet dla rozwiązania](media/nuget-walkthrough-manage-packages-solution.png)

1. Podczas zarządzania pakietami dla rozwiązania interfejsu użytkownika pozwala wybrać projekty, których dotyczą operacje:

    ![Selektor projektu podczas zarządzania pakietami dla rozwiązania](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Karta Konsolidacja

Podczas pracy w rozwiązaniu z wieloma projektami, jest uważane za najlepsze rozwiązanie, aby upewnić się, że w dowolnym miejscu używasz tego samego pakietu NuGet w każdym projekcie, używasz również tego samego numeru wersji tego pakietu. Program Visual Studio dla komputerów Mac ułatwia to, udostępniając kartę **Konsolidacja** w interfejsie użytkownika Menedżera pakietów, gdy użytkownik zdecyduje się zarządzać pakietami dla rozwiązania. Za pomocą tej karty można łatwo zobaczyć, gdzie pakiety z odrębnymi numerami wersji są używane przez różne projekty w rozwiązaniu:

![Karta Konsolidacja interfejsu użytkownika menedżera pakietów](media/nuget-walkthrough-consolidate-tab.png)

W tym przykładzie projekt NuGetDemo używa microsoft.EntityFrameworkCore 2.20, podczas gdy NuGetDemo.Shared używa microsoft.EntityFrameworkCore 2.2.6. Aby skonsolidować wersje pakietów, wykonaj następujące czynności:

- Wybierz projekty, które mają być aktualizowane na liście projektów.
- Wybierz wersję, która ma być używana we wszystkich tych projektach na liście **Nowa wersja,** na przykład Microsoft.EntityFrameworkCore 3.0.0.
- Wybierz przycisk **Konsolidacja pakietu.**

Menedżer pakietów instaluje wybraną wersję pakietu we wszystkich wybranych projektach, po czym pakiet nie jest już wyświetlany na karcie **Konsolidacja.**

## <a name="adding-package-sources"></a>Dodawanie źródeł pakietów

Pakiety dostępne do instalacji są początkowo pobierane z nuget.org. Można jednak dodać inne lokalizacje pakietów do programu Visual Studio dla komputerów Mac. Może to być przydatne do testowania własnych pakietów NuGet w trakcie opracowywania lub do korzystania z prywatnego serwera NuGet wewnątrz firmy lub organizacji.

W programie Visual Studio dla komputerów Mac przejdź do **programu Visual Studio > preferencje > Źródła > NuGet,** aby wyświetlić i edytować listę źródeł pakietów. Należy zauważyć, że źródłem może być serwer zdalny (określony przez adres URL) lub katalog lokalny.

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij **przycisk Dodaj,** aby skonfigurować nowe źródło. Wprowadź przyjazną nazwę i adres URL (lub ścieżkę pliku) do źródła pakietu. Jeśli źródłem jest bezpieczny serwer www, wprowadź nazwę użytkownika i hasło, w przeciwnym razie pozostaw te wpisy puste:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource2.png)

Podczas wyszukiwania pakietów można wybrać różne źródła:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

Dokumentacja NuGet omówiono [przy użyciu NuGet bez zatwierdzania pakietów do kontroli źródła.](/nuget/consume-packages/packages-and-source-control) Jeśli wolisz nie przechowywać plików binarnych i nieużywanych informacji w formancie źródła, można skonfigurować visual studio dla komputerów Mac, aby automatycznie przywracać pakiety z serwera. Oznacza to, że gdy deweloper pobiera projekt z kontroli źródła po raz pierwszy, Visual Studio dla komputerów Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatyczne przywracanie pakietów](media/nuget-walkthrough-AutoRestore.png)

Szczegółowe informacje na temat wykluczania śledzonego `packages` katalogu można znaleźć w dokumentacji kontroli określonego źródła.

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Zobacz też

* [Instalowanie i używanie pakietu w programie Visual Studio (w systemie Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
