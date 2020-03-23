---
title: Ogólne informacje o konfiguracjach kompilacji
description: W tym artykule opisano różne konfiguracje kompilacji w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983597"
---
# <a name="understanding-build-configurations"></a>Opis konfiguracji kompilacji

## <a name="project-build-configurations"></a>Konfiguracje kompilacji projektu

Projekty mają tendencję do wielu konfiguracji i przełączania między nimi pozwala na różne wyjścia w czasie kompilacji. Na przykład konfiguracja debugowania będzie wyprowadzać symbole debugowania, umożliwiając debugerowi rozpoznawanie nazw funkcji, parametrów lub zmiennych z śledzenia stosu aplikacji rozbitej. Chociaż te dodatkowe informacje są przydatne podczas tworzenia, prowadzi do zawyżonego rozmiaru pliku i nie jest idealny do dystrybucji.

Każda platforma ma określone konfiguracje dla jego kompilacji.

## <a name="solution-configurations"></a>Konfiguracje rozwiązań

Podobne do konfiguracji projektu, konfiguracje rozwiązania są używane do tworzenia niestandardowych konfiguracji dla całego projektu. Korzystając z karty **Mapowania konfiguracji** w elemencie **Konstruuj konfiguracje >,** można przypisać konfigurację docelową dla każdego elementu rozwiązania, jak pokazano na poniższej ilustracji:

![Opcje mapowania konfiguracji](media/projects-and-solutions-image3.png)

Aby uzyskać więcej informacji na temat konfiguracji, zobacz klip wideo [dotyczący programu Menedżer konfiguracji autorstwa](https://www.youtube.com/watch?v=tjSdkqYh5Vg) Jamesa Montemagno.

## <a name="run-configuration"></a>Uruchom konfigurację

W poprzednich wersjach programu Xamarin Studio można było wybrać opcję ustawienia projektu jako **projektu startowego**, czyli projektu uruchamianego/debugowanego podczas korzystania z globalnego polecenia run/debug. Zostało to wskazane przez pogrubiony krój czcionki dla nazwy projektu w panelu projektu.

W programie Visual Studio dla komputerów Mac zamiast ustawiania projektu startowego można ustawić _konfigurację uruchamiania_. Konfiguracje uruchamiania są prezentowane na liście rozwijanej na pasku narzędzi, obok selektora konfiguracji kompilacji, jak pokazano poniżej:

![Uruchom z listy rozwijanej Konfiguracja](media/projects-and-solutions-image8.png)

Konfiguracja uruchamiania to zestaw opcji wykonywania o nazwie i kilku konfiguracjach, które są zdefiniowane w projekcie do różnych celów. Uruchom konfiguracje są definiowane na poziomie projektu, a domyślnie zostanie utworzony automatycznie dla każdego projektu wykonywalnego, chociaż jest możliwe, aby dodać jak najwięcej, zgodnie z potrzebami. Niektóre typy projektów automatycznie generują dodatkowe konfiguracje uruchamiania. Na przykład projekty watchOS może generować _konfiguracje glance i notification._

Konfiguracje mogą być współużytkowane innym deweloperom (w takim przypadku konfiguracje będą przechowywane w pliku csproj) lub przechowywane lokalnie (w takim przypadku będą przechowywane w pliku .user).

### <a name="android-run-configurations"></a>Konfiguracje uruchamiania systemu Android

Uruchom konfiguracje dla projektów systemu Android pozwalają określić, które działanie, usługa lub odbiornik emisji do uruchomienia podczas uruchamiania lub debugowania projektu. Można przekazać intencji dodatkowych danych i ustawić intencji flagi, aby móc przetestować składniki w różnych warunkach uruchamiania.

Działania inne niż `MainLauncher` będą musiały `Exported=true` dodać do atrybutu Działanie do debugowania na urządzeniu fizycznym lub mają zdefiniowane filtry intencji.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Przykłady danych, które mogą być uwzględnione w konfiguracjach uruchamiania

Poniższa lista zawiera kilka przykładów danych, które mogą być zawarte w konfiguracjach uruchamiania:

* Zwykły projekt .NET
  * Alternatywna aplikacja startowa
  * Argumenty startowe
  * Katalog roboczy
  * Zmienne środowiskowe
  * Opcje mono-runtime (do użycia tylko podczas pracy na mono)
* Projekt Android
  * Punkt wejścia (aktywność, serwis, odbiorca)
  * Argumenty i dane intencji
* Projekt systemu iOS
  * Tryb (normalny, pobieranie tła)
* Projekt rozszerzenia systemu iOS
  * Aplikacja startowa: domyślna lub niestandardowa
* Projekt WatchKit
  * Tryb (rzut oka, powiadomienie)
  * Ładowność powiadomień

## <a name="see-also"></a>Zobacz też

- [Opis konfiguracji kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/understanding-build-configurations)
