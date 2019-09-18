---
title: Dołączanie pakietu NuGet do projektu
description: W tym dokumencie opisano sposób dołączania pakietu NuGet w projekcie przy użyciu Visual Studio dla komputerów Mac. Przeprowadza on wyszukiwanie i pobieranie pakietu, a także przedstawia funkcje integracji IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/17/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 22b2e07509403d8e19e3a3e920d45b064c2e51c0
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079494"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Instalowanie pakietów NuGet i zarządzanie nimi w Visual Studio dla komputerów Mac

Interfejs użytkownika Menedżera pakietów NuGet w Visual Studio dla komputerów Mac umożliwia łatwe instalowanie, Odinstalowywanie i aktualizowanie pakietów NuGet w projektach i rozwiązaniach. Można wyszukiwać i dodawać pakiety do projektów .NET Core, ASP.NET Core i Xamarin.

W tym artykule opisano sposób dołączania pakietu NuGet do projektu i zademonstrowania łańcucha narzędzi, który sprawia, że proces jest płynny.

Aby zapoznać się z wprowadzeniem do korzystania z narzędzia [NuGet w Visual Studio dla komputerów Mac, zobacz Szybki Start: Instalowanie i używanie pakietu w Visual Studio dla komputerów Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Znajdowanie i instalowanie pakietu

1. Mając otwarty projekt w Visual Studio dla komputerów Mac, kliknij prawym przyciskiem myszy folder **zależności** (**pakiety** , jeśli używasz projektu Xamarin) w **okienko rozwiązania** i wybierz polecenie **Dodaj pakiety**.

    ![Dodaj nową akcję kontekstu pakietu NuGet](media/nuget-walkthrough-PackagesMenu.png)

2. Spowoduje to uruchomienie okna **Dodaj pakiety** . Upewnij się, że lista rozwijana źródła w lewym górnym rogu okna dialogowego ma ustawioną `nuget.org`wartość.

    ![Wyświetl listę pakietów NuGet](media/nuget-walkthrough-AddPackages1.png)

3. Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć konkretny pakiet, na przykład `EntityFramework`. Po znalezieniu pakietu, którego chcesz użyć, zaznacz go, a następnie kliknij przycisk **Dodaj pakiet** , aby rozpocząć instalację.

    ![Dodaj pakiet NuGet platformy Azure](media/nuget-walkthrough-AddPackages2.png)

4. Po pobraniu pakietu zostanie on dodany do projektu. Rozwiązanie zmieni się w zależności od typu edytowanego projektu:

    **Projekty platformy Xamarin**
    * Węzeł **References** będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
    * Węzeł **pakiety** wyświetla każdy pobrany pakiet NuGet. Możesz zaktualizować lub usunąć pakiet z tej listy.
    
    **Projekty .NET Core**

    **Zależności > węźle NuGet** wyświetla każdy pobrany pakiet NuGet. Możesz zaktualizować lub usunąć pakiet z tej listy.

## <a name="using-nuget-packages"></a>Korzystanie z pakietów NuGet

Po dodaniu pakietu NuGet wraz z aktualizacją projektu można programować względem interfejsów API, tak jak w przypadku dowolnego odwołania do projektu.

Upewnij się, że wszystkie wymagane `using` dyrektywy zostały dodane na początku pliku:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aktualizowanie pakietów

Aktualizacje pakietu można wykonać wszystkie naraz, klikając prawym przyciskiem myszy węzeł **zależności** (lub węzeł **pakiety** dla projektów platformy Xamarin) lub pojedynczo dla każdego składnika.

Kliknij prawym przyciskiem myszy **zależności** , aby uzyskać dostęp do menu kontekstowego:

![Menu pakiety](media/nuget-walkthrough-PackagesMenu.png)

* **Zarządzanie pakietami NuGet** — otwiera okno w celu dodania kolejnych pakietów do projektu.
* **Update** — sprawdza serwer źródłowy dla każdego pakietu i pobiera nowsze wersje.
* **Restore** — pobiera wszystkie brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Opcje aktualizacji i przywracania są również dostępne na poziomie rozwiązania i wpływają na wszystkie projekty w rozwiązaniu.

W konsoli rozwiązania możesz zobaczyć, która wersja pakietu jest aktualnie zainstalowana, a następnie kliknij prawym przyciskiem myszy pakiet, który chcesz zaktualizować.

![Menu pakiety z opcjami do zaktualizowania, usunięcia, odświeżenia](media/nuget-walkthrough-PackageMenu.png)

Po udostępnieniu nowej wersji pakietu zobaczysz powiadomienie obok nazwy pakietu, dzięki czemu możesz zdecydować, czy chcesz ją zaktualizować.

![Powiadomienie wyświetlane, gdy dostępna jest nowa wersja pakietu](media/nuget-walkthrough-package-update-available.png)

W wyświetlonym menu są dostępne dwie opcje:

* **Update** — sprawdza serwer źródłowy i pobiera nowszą wersję (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołań projektu.

## <a name="adding-package-sources"></a>Dodawanie źródeł pakietów

Pakiety dostępne do instalacji są początkowo pobierane z nuget.org. Można jednak dodać inne lokalizacje pakietu do Visual Studio dla komputerów Mac. Może to być przydatne do testowania własnych pakietów NuGet w środowisku deweloperskim lub do korzystania z prywatnego serwera NuGet w firmie lub organizacji.

W Visual Studio dla komputerów Mac przejdź do **okna preferencje > programu Visual Studio, > źródła > NuGet** , aby wyświetlić i edytować listę źródeł pakietów. Należy pamiętać, że źródła mogą być serwerem zdalnym (określonym za pomocą adresu URL) lub katalogiem lokalnym.

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij przycisk **Dodaj** , aby skonfigurować nowe źródło. Wprowadź przyjazną nazwę i adres URL (lub ścieżkę pliku) do źródła pakietu. Jeśli źródłem jest bezpieczny serwer sieci Web, wprowadź nazwę użytkownika i hasło. w przeciwnym razie pozostaw te wpisy puste:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource2.png)

Podczas wyszukiwania pakietów można wybrać różne źródła:

![Dodawanie źródeł pakietów](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

Dokumentacja programu NuGet omawia [Korzystanie z programu NuGet bez zatwierdzania pakietów do kontroli źródła](/nuget/consume-packages/packages-and-source-control). Jeśli wolisz, aby nie przechowywać plików binarnych i nieużywanych informacji w kontroli źródła, możesz skonfigurować Visual Studio dla komputerów Mac, aby automatycznie przywracać pakiety z serwera. Oznacza to, że gdy deweloper pobiera projekt z kontroli źródła po raz pierwszy, program Visual Studio dla komputerów Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatycznie Przywróć pakiety](media/nuget-walkthrough-AutoRestore.png)

Zapoznaj się z określoną dokumentacją kontroli źródła, aby uzyskać szczegółowe informacje na `packages` temat wykluczania śledzenia katalogu.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie pakietu w programie Visual Studio (w systemie Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
