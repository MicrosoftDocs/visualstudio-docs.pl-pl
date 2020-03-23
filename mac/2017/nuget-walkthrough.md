---
title: Dołączanie pakietu NuGet do projektu
description: W tym dokumencie opisano, jak dołączyć pakiet NuGet w projekcie platformy Xamarin. Przechodzi przez znajdowanie i pobieranie pakietu, a także wprowadzenie funkcji integracji IDE.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.openlocfilehash: 728a225f4a1d14af986039cae7cb2fc8a493ecc9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983303"
---
# <a name="include-a-nuget-package-in-your-project"></a>Dołącz pakiet NuGet do projektu

NuGet jest najpopularniejszym menedżerem pakietów dla programu .NET development i jest wbudowany w program Visual Studio dla komputerów Mac i Visual Studio w systemie Windows. Możesz wyszukiwać i dodawać pakiety do projektów xamarin.iOS i Xamarin.Android przy użyciu ide.

W tym artykule opisano, jak dołączyć pakiet NuGet w projekcie i demonstruje łańcuch narzędzi, który sprawia, że proces bezproblemowe.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet w programie Visual Studio dla komputerów Mac

Aby zademonstrować funkcjonalność pakietu NuGet, najpierw przejdziemy przez tworzenie nowej aplikacji i dodawanie do niej pakietu. Następnie omówimy funkcje IDE, które pomagają zarządzać pakietami.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Najpierw utwórz projekt `HelloNuget` o nazwie, jak pokazano poniżej. W tym przykładzie pokazano szablon aplikacji pojedynczego widoku systemu iOS, ale każdy obsługiwany typ projektu będzie działać:

![Tworzenie nowego projektu systemu iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Dodawanie pakietu

Po otwarciu projektu w programie Visual Studio dla komputerów Mac kliknij prawym przyciskiem myszy folder **Pakiety** w **panelu rozwiązania** i wybierz pozycję Dodaj **pakiety:**

![Dodawanie nowej akcji kontekstu pakietu NuGet](media/nuget-walkthrough-PackagesMenu.png)

Spowoduje to uruchomienie okna **Dodaj pakiety.** Upewnij się, że z listy `nuget.org`rozwijanej Źródło jest ustawiona na:

![Lista źródeł rozwijana](media/nuget-walkthrough-Source.png)

Po otwarciu okna ładuje listę pakietów z domyślnego źródła pakietu: nuget.org. Wstępne wyniki wyglądają następująco:

![Lista pakietów NuGet](media/nuget-walkthrough-AddPackages1.png)

Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć `azure`określony pakiet, na przykład . Po znalezieniu pakietu, którego chcesz użyć, zaznacz go i kliknij przycisk **Dodaj pakiet,** aby rozpocząć instalację.

[Dodawanie pakietu NuGet platformy Azure](media/nuget-walkthrough-AddPackages2.png)

Po pobraniu pakietu zostanie on dodany do projektu. Rozwiązanie zmieni się w następujący sposób:

* **Węzeł Odwołania** będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
* Węzeł **Pakiety** wyświetla każdy pobrany pakiet NuGet. Pakiet można zaktualizować lub usunąć z tej listy.
* Plik **packages.config** zostanie dodany do projektu. Ten plik XML jest używany przez IDE do śledzenia, które wersje pakietu są przywoływać w tym projekcie. Ten plik nie powinien być ręcznie edytowany, ale należy go zachować w kontroli wersji. Należy zauważyć, że zamiast pliku packages.config można użyć pliku project.json. Plik project.json to nowy format pliku pakietu wprowadzony za pomocą NuGet 3, który obsługuje przywracanie przechodnie. Bardziej szczegółowe informacje na temat project.json można znaleźć w [dokumentacji NuGet](/NuGet/Schema/Project-Json). Plik project.json musi zostać dodany ręcznie, a projekt zamknięty i ponownie otwarty, zanim plik project.json zostanie użyty w programie Visual Studio dla komputerów Mac.

## <a name="using-nuget-packages"></a>Korzystanie z pakietów NuGet

Po dodaniu pakietu NuGet i zaktualizowano odwołania do projektu, można programować względem interfejsów API, tak jak w przypadku dowolnego odwołania do projektu.

Upewnij się, że `using` dodasz wszystkie wymagane dyrektywy do górnej części pliku:

```csharp
using Newtonsoft.Json;
```

Większość NuGet podać dodatkowe informacje, takie jak README lub łącze strony projektu do źródła Nuget. Zwykle można znaleźć link do tego w pakiecie blurb na stronie Dodawanie pakietów:

[Łącze Wyświetl stronę projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aktualizacje pakietów

Aktualizacje pakietu można wykonać wszystkie naraz, klikając prawym przyciskiem myszy węzeł **Pakiety** lub indywidualnie na każdy składnik.

Kliknij prawym przyciskiem myszy **pakiety,** aby uzyskać dostęp do menu kontekstowego:

![Menu Pakiety](media/nuget-walkthrough-PackagesMenu.png)

* **Dodaj pakiety** — otwiera okno, aby dodać więcej pakietów do projektu.
* **Aktualizacja** — sprawdza serwer źródłowy dla każdego pakietu i pobiera wszystkie nowsze wersje.
* **Przywracanie** — pobiera brakujące pakiety (bez aktualizowania istniejących pakietów do nowszych wersji).

Opcje aktualizacji i przywracania są również dostępne na poziomie rozwiązania i mają wpływ na wszystkie projekty w rozwiązaniu.

Możesz również kliknąć prawym przyciskiem myszy poszczególne pakiety, aby uzyskać dostęp do menu kontekstowego:

![Menu Pakiety](media/nuget-walkthrough-PackageMenu.png)

* **Numer wersji** — numer wersji jest wyłączonym elementem menu — jest on udostępniany wyłącznie w celach informacyjnych.
* **Aktualizacja** — sprawdza serwer źródłowy i pobiera nowszą wersję (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usuwa odpowiednie zestawy z odwołania projektu.

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
