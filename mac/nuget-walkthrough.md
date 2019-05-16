---
title: Dołączanie pakietu NuGet w projekcie
description: W tym dokumencie opisano, jak dołączyć pakietu NuGet w projekcie Xamarin. Jego przeprowadzi wyszukiwanie i pobieranie pakietu, a także wprowadzenie do funkcji integracji środowiska IDE.
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.openlocfilehash: 9f96354d9e460cebd81f52712f74dc6226f8706d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692326"
---
# <a name="include-a-nuget-package-in-your-project"></a>Uwzględnione pakietu NuGet w projekcie

NuGet jest najbardziej popularnych Menedżer pakietów dla programowania na platformie .NET i wbudowanej w program Visual Studio dla komputerów Mac i Visual Studio na Windows. Można wyszukiwać i dodawać pakiety do projektów Xamarin.iOS i Xamarin.Android przy użyciu dowolnego środowiska IDE.

W tym artykule opisano, jak dołączyć pakietu NuGet w projekcie i pokazuje łańcuch narzędzi, który sprawia, że proces jest bezproblemowe.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet w programie Visual Studio dla komputerów Mac

Aby zademonstrować funkcje pakietu NuGet, najpierw przeprowadzimy przez tworzenie nowej aplikacji i dodawanie pakietu do niego. Następnie omówimy funkcji środowiska IDE, które ułatwia zarządzanie pakietami.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Najpierw utwórz projekt o nazwie `HelloNuget` tak jak przedstawiono poniżej. W tym przykładzie przedstawiono szablon aplikacja pojedynczego widoku dla systemu iOS, ale będzie działać w dowolnym typem projektu obsługiwane:

![Tworzenie nowego projektu dla systemu iOS](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>Dodawanie pakietu

Otwórz w programie Visual Studio dla komputerów Mac projektu, kliknij prawym przyciskiem myszy **pakietów** folderu w **konsoli rozwiązania** i wybierz **Dodawanie pakietów**:

![Dodaj nową akcję kontekstu pakietu NuGet](media/nuget-walkthrough-PackagesMenu.png)

Spowoduje to uruchomienie **Dodawanie pakietów** okna. Upewnij się, że źródło listy rozwijanej, jest ustawiona na `nuget.org`:

![Źródło listy rozwijanej](media/nuget-walkthrough-Source.png)

Po otwarciu przez okna ładuje listę pakietów z domyślnego źródła pakietu: nuget.org. Początkowe wyniki wyglądać następująco:

![Lista pakietów NuGet](media/nuget-walkthrough-AddPackages1.png)

Użyj pola wyszukiwania w prawym górnym rogu, aby znaleźć określony pakiet, na przykład `azure`. Po znalezieniu pakietu, który chcesz użyć, zaznacz go i kliknij **Dodaj pakiet** przycisk, aby rozpocząć instalację.

[Dodaj pakiet NuGet platformy Azure](media/nuget-walkthrough-AddPackages2.png)

Po pobraniu pakietu zostanie dodany do projektu. Rozwiązanie zmieni się w następujący sposób:

* **Odwołania** węzeł będzie zawierać listę wszystkich zestawów, które są częścią pakietu NuGet.
* **Pakietów** węzła wyświetla każdego pakietu NuGet, które zostały pobrane. Można zaktualizować lub usunąć pakiet z tej listy.
* A **packages.config** plik zostanie dodany do projektu. Ten plik XML jest używany przez środowisko IDE do śledzenia wersji pakietu, które są określone w tym projekcie. Ten plik nie powinien być ręcznie edytowany, ale należy go przechowywać w kontroli wersji. Należy pamiętać, że plik project.json mogą być używane zamiast pliku packages.config. Plik project.json jest nowym formacie plików pakietu wprowadzone w programie NuGet 3, która obsługuje Przywracanie przechodnie. Bardziej szczegółowe informacje o pliku project.json znajdują się w [dokumentacja programu NuGet](https://docs.microsoft.com/NuGet/Schema/Project-Json). Plik project.json musi zostać dodane ręcznie, a projekt zamknięciu i ponownym otwarciu przed pliku project.json jest używany w programie Visual Studio dla komputerów Mac.

## <a name="using-nuget-packages"></a>Za pomocą pakietów NuGet

Po dodaniu pakietu NuGet i odwołania do projektu, zaktualizowany, można programować względem interfejsy API, co w przypadku dowolnego odwołania do projektu.

Upewnij się, Dodaj wymagane `using` dyrektywy na początku pliku:

```csharp
using Newtonsoft.Json;
```

Większość NuGet zawierają dodatkowe informacje, takie jak plik README lub projektu łącze strony do źródła pakietów Nuget. Zwykle znajduje się łącze do tego w notka pakietu na stronie Dodawanie pakietów:

[Link do wyświetlenia strony projektu](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Pakiet aktualizacji

Pakiet aktualizacji może się to odbywać wszystko naraz, klikając prawym przyciskiem myszy **pakietów** węzła, lub osobno dla każdego składnika.

Kliknij prawym przyciskiem myszy **pakietów** dostęp do menu kontekstowego:

![Menu pakietów](media/nuget-walkthrough-PackagesMenu.png)

* **Dodaj pakiety** — powoduje otwarcie okna, aby dodać więcej pakietów do projektu.
* **Aktualizacja** — sprawdza, czy serwer źródłowy dla każdego pakietu i pobiera wszystkie nowsze wersje.
* **Przywróć** — pliki do pobrania wszystkie brakujące pakiety (bez aktualizowania istniejące pakiety do nowszych wersji).

Aktualizacja opcje przywracania są również dostępne na poziomie rozwiązania i wpływają na wszystkie projekty w rozwiązaniu.

Użytkownik może również kliknij prawym przyciskiem myszy poszczególnych pakietów na dostęp do menu kontekstowego:

![Menu pakietów](media/nuget-walkthrough-PackageMenu.png)

* **Numer wersji** — numer wersji jest wyłączonego elementu menu — jest ona udostępniana tylko w celach informacyjnych.
* **Aktualizacja** — sprawdza, czy serwer źródłowy i pliki do pobrania jest nowsza wersja (jeśli istnieje).
* **Usuń** — usuwa pakiet z tego projektu i usunięcie odpowiednich zestawów z odwołaniami do projektów.

## <a name="adding-package-sources"></a>Dodawanie źródła pakietów

Dostępne do zainstalowania pakietów początkowo są pobierane z witryny nuget.org. Jednak dodać inne lokalizacje pakietu programu Visual Studio dla komputerów Mac. Może to być przydatne w przypadku testowania pakietów NuGet w fazie projektowania lub użyć prywatny serwer NuGet wewnątrz firmy lub organizacji.

W programie Visual Studio dla komputerów Mac, przejdź do **programu Visual Studio > Preferencje > NuGet > źródeł** do wyświetlania i edytowania listy źródeł pakietów. Należy pamiętać, że źródła może być (określone za pomocą adresu URL) serwera zdalnego lub katalogu lokalnego.

![Źródła pakietów](media/nuget-walkthrough-PackageSource.png)

Kliknij przycisk **Dodaj** do konfiguracji nowego źródła. Wprowadź przyjazną nazwę i adres URL (lub ścieżka do pliku) do źródła pakietu. Jeśli źródło jest zabezpieczonym serwerze sieci web, wprowadź nazwę użytkownika i hasło, a także, w przeciwnym razie pozostaw puste następujące wpisy:

![Dodawanie źródła pakietów](media/nuget-walkthrough-PackageSource2.png)

Następnie można wybrać różnych źródeł, aby wyszukać pakiety:

![Dodawanie źródła pakietów](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Kontrola wersji

W tym artykule omówiono dokumentacji NuGet [za pomocą narzędzia NuGet nie poświęcając pakietów do kontroli źródła](/nuget/consume-packages/packages-and-source-control). Jeśli nie chcesz przechowywać pliki binarne i nieużywanych informacji w kontroli źródła, można skonfigurować program Visual Studio for Mac automatycznie przywrócić pakiety z serwera. Oznacza to, że kiedy Deweloper pobiera projektu z kontroli źródła po raz pierwszy, Visual Studio dla komputerów Mac automatycznie pobierze i zainstaluje wymagane pakiety.

![Automatycznie przywracanie pakietów](media/nuget-walkthrough-AutoRestore.png)

Można znaleźć w dokumentacji kontroli konkretnego źródła, aby uzyskać szczegółowe informacje na temat wykluczania `packages` katalogu z są śledzone.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Zobacz także

* [Instalowanie i używanie pakietu w programie Visual Studio (na Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
