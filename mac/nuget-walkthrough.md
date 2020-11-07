---
title: Dołączanie pakietu NuGet do projektu
description: W tym dokumencie opisano sposób dołączania pakietu NuGet w projekcie przy użyciu Visual Studio dla komputerów Mac. Przeprowadza on wyszukiwanie i pobieranie pakietu, a także przedstawia funkcje integracji IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/04/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: e361a1a0fba05a6fdabc66b03008049dfa34784f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349340"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalowanie pakietów NuGet i zarządzanie nimi w Visual Studio dla komputerów Mac

Interfejs użytkownika Menedżera pakietów NuGet w Visual Studio dla komputerów Mac umożliwia łatwe instalowanie, Odinstalowywanie i aktualizowanie pakietów NuGet w projektach i rozwiązaniach. Można wyszukiwać i dodawać pakiety do projektów .NET Core, ASP.NET Core i Xamarin.

W tym artykule opisano sposób dołączania pakietu NuGet do projektu i zademonstrowania łańcucha narzędzi, który sprawia, że proces jest płynny.

Aby zapoznać się z wprowadzeniem do korzystania z narzędzia NuGet w Visual Studio dla komputerów Mac, zobacz [Szybki Start: Instalowanie i używanie pakietu w programie Visual Studio dla komputerów Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Znajdowanie i instalowanie pakietu

1. Gdy projekt jest otwarty w Visual Studio dla komputerów Mac, kliknij prawym przyciskiem myszy folder **zależności** ( **pakiety** , jeśli używany jest projekt Xamarin) w **okienko rozwiązania** i wybierz pozycję **Zarządzaj pakietami NuGet..**..

    ![Dodaj nową akcję kontekstu pakietu NuGet](media/nuget-walkthrough-packages-menu.png)

2. Spowoduje to uruchomienie okna **Zarządzanie pakietami NuGet** . Upewnij się, że lista rozwijana źródła w lewym górnym rogu okna dialogowego jest ustawiona na `nuget.org` , aby przeszukać centralne repozytorium pakietów NuGet.

    ![Wyświetl listę pakietów NuGet](media/nuget-walkthrough-add-packages1.png)

3. Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć konkretny pakiet, na przykład `EntityFramework` . Po znalezieniu pakietu, którego chcesz użyć, zaznacz go, a następnie kliknij przycisk **Dodaj pakiet** , aby rozpocząć instalację.

    ![Dodaj pakiet NuGet EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Po pobraniu pakietu zostanie on dodany do projektu. Rozwiązanie zmieni się w zależności od typu edytowanego projektu:

    **Projekty platformy Xamarin**
    * Węzeł **References** będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
    * Węzeł **pakiety** wyświetla każdy pobrany pakiet NuGet. Możesz zaktualizować lub usunąć pakiet z tej listy.
    
    **Projekty .NET Core**

    * **Zależności > węźle NuGet** wyświetla każdy pobrany pakiet NuGet. Możesz zaktualizować lub usunąć pakiet z tej listy.

## <a name="using-nuget-packages"></a>Korzystanie z pakietów NuGet

Po dodaniu pakietu NuGet wraz z aktualizacją projektu można programować względem interfejsów API, tak jak w przypadku dowolnego odwołania do projektu.

Upewnij się, że wszystkie wymagane `using` dyrektywy zostały dodane na początku pliku:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualizowanie pakietów

Aktualizacje pakietu można wykonać wszystkie naraz, klikając prawym przyciskiem myszy węzeł **zależności** (węzeł **pakiety** dla projektów platformy Xamarin) lub indywidualnie dla każdego pakietu. Gdy dostępna jest nowa wersja pakietu NuGet, ikona aktualizacji zostanie wyświetlona ![ strzałka z kółkiem ](media/nuget-walkthrough-update-icon.png) .

Kliknij prawym przyciskiem myszy pozycję **zależności** , aby uzyskać dostęp do menu kontekstowego, a następnie wybierz polecenie **Aktualizuj** , aby zaktualizować wszystkie pakiety:

![Menu kontekstowe zależności z wyróżnionym menu Aktualizuj](media/nuget-walkthrough-packages-menu-update.png)

* **Zarządzanie pakietami NuGet** — otwiera okno w celu dodania kolejnych pakietów do projektu.
* **Update** — sprawdza serwer źródłowy dla każdego pakietu i pobiera nowsze wersje.
* **Restore** — pobiera wszystkie brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Opcje aktualizacji i przywracania są również dostępne na poziomie rozwiązania i wpływają na wszystkie projekty w rozwiązaniu.

### <a name="updating-to-pre-release-versions-of-packages"></a>Aktualizowanie do wersji wstępnych pakietów
Aby zaktualizować do nowszej wersji wstępnej pakietu, kliknij prawym przyciskiem myszy pozycję **zależności** , aby otworzyć menu kontekstowe i wybierz polecenie **Zarządzaj pakietami NuGet...** .

![Menu kontekstowe zależności z Zarządzaj pakietami NuGet... menu wyróżnione](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

Zaznacz pole wyboru **Pokaż pakiety w wersji wstępnej** w dolnej części okna dialogowego.

![Otwarto okno dialogowe zarządzania pakietami NuGet z zaznaczoną opcją "Pokaż pakiety wersji wstępnej"](media/nuget-walkthrough-show-pre-release-packages.png)

Na koniec na karcie **aktualizacje** okna dialogowego wybierz pakiet, który chcesz zaktualizować, a następnie wybierz nową wersję wstępną z listy rozwijanej **Nowa wersja** i kliknij pozycję **Aktualizuj pakiet**.

![Zostanie otwarte okno dialogowe Zarządzanie pakietami NuGet z zainstalowaną kartą z wybranym pakietem i otwartą listą rozwijaną Nowa wersja.](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>Lokalizowanie nieaktualnych pakietów
W konsoli rozwiązania możesz zobaczyć, która wersja pakietu jest aktualnie zainstalowana, a następnie kliknij prawym przyciskiem myszy pakiet, który chcesz zaktualizować.

![Menu pakiety z opcjami do zaktualizowania, usunięcia, odświeżenia](media/nuget-walkthrough-PackageMenu.png)

Po udostępnieniu nowej wersji pakietu zobaczysz powiadomienie obok nazwy pakietu, dzięki czemu możesz zdecydować, czy chcesz ją zaktualizować.

![Powiadomienie wyświetlane, gdy dostępna jest nowa wersja pakietu](media/nuget-walkthrough-package-update-available.png)

W wyświetlonym menu są dostępne dwie opcje:

* **Update** — sprawdza serwer źródłowy i pobiera nowszą wersję (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołań projektu.

## <a name="manage-packages-for-the-solution"></a>Zarządzaj pakietami dla rozwiązania

Zarządzanie pakietami dla rozwiązania jest wygodnym sposobem pracy z wieloma projektami jednocześnie.

1. Kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Zarządzaj pakietami NuGet...** :

    ![Zarządzaj pakietami NuGet dla rozwiązania](media/nuget-walkthrough-manage-packages-solution.png)

1. Podczas zarządzania pakietami dla rozwiązania interfejs użytkownika umożliwia wybranie projektów, na które mają wpływ operacje:

    ![Selektor projektu podczas zarządzania pakietami dla rozwiązania](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Karta konsolidowanie

W przypadku pracy w rozwiązaniu z wieloma projektami uważa się, że najlepszym rozwiązaniem jest upewnienie się, że każdy z nich korzysta z tego samego pakietu NuGet w każdym projekcie, ale również korzysta z tego samego numeru wersji tego pakietu. Visual Studio dla komputerów Mac pomaga to ułatwić, dostarczając kartę **konsolidacji** w interfejsie użytkownika Menedżera pakietów, gdy zdecydujesz się na zarządzanie pakietami dla rozwiązania. Za pomocą tej karty można łatwo zobaczyć, gdzie pakiety z unikatowymi numerami wersji są używane przez różne projekty w rozwiązaniu:

![Karta konsolidacja interfejsu użytkownika Menedżera pakietów](media/nuget-walkthrough-consolidate-tab.png)

W tym przykładzie projekt NuGetDemo korzysta z Microsoft. EntityFrameworkCore 2,20, natomiast NuGetDemo. Shared jest używany przez Microsoft. EntityFrameworkCore 2.2.6. Aby skonsolidować wersje pakietów, wykonaj następujące czynności:

- Wybierz projekty do zaktualizowania na liście projektów.
- Wybierz wersję, która ma być używana we wszystkich projektach z listy **nowej wersji** , np. Microsoft. EntityFrameworkCore 3.0.0.
- Wybierz przycisk **Konsoliduj pakiet** .

Menedżer pakietów instaluje wybraną wersję pakietu we wszystkich wybranych projektach, po upływie których pakiet nie jest już wyświetlany na karcie **konsolidowanie** .

## <a name="adding-package-sources"></a>Dodawanie źródeł pakietów

Pakiety dostępne do instalacji są początkowo pobierane z nuget.org. Można jednak dodać inne lokalizacje pakietu do Visual Studio dla komputerów Mac. Może to być przydatne do testowania własnych pakietów NuGet w środowisku deweloperskim lub do korzystania z prywatnego serwera NuGet w firmie lub organizacji.

W Visual Studio dla komputerów Mac przejdź do **okna preferencje > programu Visual Studio, > źródła > NuGet** , aby wyświetlić i edytować listę źródeł pakietów. Należy pamiętać, że źródła mogą być serwerem zdalnym (określonym za pomocą adresu URL) lub katalogiem lokalnym.

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij przycisk **Dodaj** , aby skonfigurować nowe źródło. Wprowadź przyjazną nazwę i adres URL (lub ścieżkę pliku) do źródła pakietu. Jeśli źródłem jest bezpieczny serwer sieci Web, wprowadź nazwę użytkownika i hasło. w przeciwnym razie pozostaw te wpisy puste:

![Okno dialogowe Dodawanie źródła pakietu z monitem o nazwę, adres URL lokalizacji, nazwę użytkownika i hasło.](media/nuget-walkthrough-PackageSource2.png)

Podczas wyszukiwania pakietów można wybrać różne źródła:

![Okno dialogowe Dodawanie źródła pakietu zawierające listę źródeł pakietów.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

Dokumentacja programu NuGet omawia [Korzystanie z programu NuGet bez zatwierdzania pakietów do kontroli źródła](/nuget/consume-packages/packages-and-source-control). Jeśli wolisz, aby nie przechowywać plików binarnych i nieużywanych informacji w kontroli źródła, możesz skonfigurować Visual Studio dla komputerów Mac, aby automatycznie przywracać pakiety z serwera. Oznacza to, że gdy deweloper pobiera projekt z kontroli źródła po raz pierwszy, program Visual Studio dla komputerów Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatycznie Przywróć pakiety](media/nuget-walkthrough-AutoRestore.png)

Zapoznaj się z określoną dokumentacją kontroli źródła, aby uzyskać szczegółowe informacje na temat wykluczania `packages` śledzenia katalogu.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Zobacz też

* [Instalowanie i używanie pakietu w programie Visual Studio (w systemie Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
