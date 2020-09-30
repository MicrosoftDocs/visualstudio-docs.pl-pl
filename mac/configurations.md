---
title: Ogólne informacje o konfiguracjach kompilacji
description: W tym artykule opisano różne konfiguracje kompilacji w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 911d8d3a65c414bc3c98494bda75c46b778e5b2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584025"
---
# <a name="understanding-build-configurations"></a>Ogólne informacje o konfiguracjach kompilacji

Można przechowywać różne konfiguracje rozwiązań i właściwości projektu do użycia w różnych rodzajach kompilacji podczas procesu tworzenia. Projekty utworzone przez Visual Studio dla komputerów Mac przy użyciu szablonu zwykle obejmują konfiguracje debugowania i wydania, które obsługują debugowanie aplikacji i wdrożenia aplikacji. 

Jeśli chcesz utworzyć niestandardowe konfiguracje, zobacz [Tworzenie i edytowanie konfiguracji kompilacji](./create-and-edit-configurations.md).

>[!NOTE]
>Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zobacz [Omówienie konfiguracji kompilacji](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Konfiguracje rozwiązań służą do określania konfiguracji dla wszystkich projektów w rozwiązaniu. Korzystając z karty **mapowania konfiguracji** w obszarze **konfiguracji > kompilacji** , można przypisać konfigurację docelową dla każdego elementu w otwartym rozwiązaniu. Jest to zademonstrowane na poniższej ilustracji:

![Opcje mapowania konfiguracji](media/projects-and-solutions-image3.png)

Aby uzyskać więcej informacji o konfiguracjach, zobacz [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) Video, Kuba Montemagno.

## <a name="project-build-configurations"></a>Konfiguracje kompilacji projektu

Projekty mają wiele konfiguracji. Konfiguracja i platforma elementy docelowe projektu są używane razem do określenia właściwości, które mają być używane podczas kompilowania. Przełączanie między konfiguracjami pozwala na różne dane wyjściowe w czasie kompilacji. Na przykład konfiguracja debugowania będzie wyprowadzać symbole debugowania, umożliwiając debugerowi rozpoznawanie nazw funkcji, parametrów lub zmiennych ze śladu stosu aplikacji, które uległy awarii. Chociaż te dodatkowe informacje są przydatne podczas opracowywania, prowadzi do niewypełnionego rozmiaru pliku i nie jest idealnym rozwiązaniem do dystrybucji.

Każda platforma ma konkretne konfiguracje dla swojej kompilacji. Dostęp do stron konfiguracji kompilacji dla projektów można uzyskać, przechodząc do sekcji **kompilacja** w oknie dialogowym **Opcje projektu** . Otwórz to okno dialogowe, klikając prawym przyciskiem myszy projekt i wybierając **Opcje** lub klikając dwukrotnie projekt w Eksploratorze rozwiązań.

## <a name="run-configuration"></a>Uruchom konfigurację

Visual Studio dla komputerów Mac pozwala ustawić _konfigurację uruchamiania_. Konfiguracje uruchomieniowe są wyświetlane na liście rozwijanej na pasku narzędzi obok selektora konfiguracji kompilacji, jak pokazano poniżej:

![Lista rozwijana uruchamiania konfiguracji](media/projects-and-solutions-image8.png)

Konfiguracja przebiegu to zestaw opcji wykonywania o nazwie i kilku konfiguracjach, które są zdefiniowane w projekcie do różnych celów. Konfiguracje uruchomieniowe są definiowane na poziomie projektu, a dla każdego projektu wykonywalnego zostanie automatycznie utworzone ustawienie domyślne, chociaż można dodać dowolną liczbę. Niektóre typy projektów automatycznie generują dodatkowe konfiguracje uruchomieniowe. Na przykład projekty systemu watchOS mogą generować  _szybkie i konfiguracje powiadomień._

Konfiguracje mogą być udostępniane innym deweloperom (w tym przypadku konfiguracje będą przechowywane w pliku. csproj) lub przechowywane lokalnie (w takim przypadku będą przechowywane w pliku. user).

### <a name="android-run-configurations"></a>Konfiguracje uruchamiania systemu Android

Uruchamianie konfiguracji dla projektów systemu Android umożliwia określenie określonego działania, usługi lub odbiornika emisji do uruchomienia podczas uruchamiania lub debugowania projektu. Można przekazać dodatkowe dane i ustawić flagi założeń, aby przetestować składniki w różnych warunkach uruchamiania.

Działania inne niż `MainLauncher` należy `Exported=true` dodać do atrybutu Activity dla debugowania na urządzeniu fizycznym lub zdefiniować filtry zamierzeń.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Przykłady danych, które mogą zostać uwzględnione w konfiguracjach uruchomieniowych

Poniższa lista zawiera przykładowe dane, które mogą zostać uwzględnione w konfiguracjach uruchamiania:

* Zwykły projekt .NET
  * Alternatywna aplikacja startowa
  * Argumenty początkowe
  * Katalog roboczy
  * Zmienne środowiskowe
  * Opcje środowiska uruchomieniowego mono (do użycia tylko w przypadku uruchamiania w trybie mono)
* Projekt systemu Android
  * Punkt wejścia (działanie, usługa, odbiorca)
  * Argumenty i dane intencji
* projekt systemu iOS
  * Tryb (normalny, pobieranie w tle)
* projekt rozszerzenia systemu iOS
  * Aplikacja startowa: domyślna lub niestandardowa
* Projekt WatchKit
  * Tryb (w skrócie, powiadomienie)
  * Ładunek powiadomienia

## <a name="see-also"></a>Zobacz też

- [Informacje o konfiguracjach kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/understanding-build-configurations)