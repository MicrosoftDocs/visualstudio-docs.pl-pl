---
title: Kontrola wersji
description: Używanie systemu Git i Subversion w Visual Studio dla komputerów Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: cf8c0fef2b9690595e99ce3802586cdd55fd37c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108097"
---
# <a name="version-control"></a>Kontrola wersji

Kontrola wersji to system służący do zarządzania plikami w wielu różnych wersjach, a w przypadku opracowywania oprogramowania — zwykle jest to spowodowane przez wielu deweloperów. Głównym celem dowolnego systemu kontroli wersji (_VCS_) jest znalezienie rozwiązania, które pozwala wszystkim użytkownikom na jednoczesne współdziałanie z bazą kodu.

Na początku dowolnego systemu kontroli wersji jest _repozytorium_, które działa jako centralny magazyn danych dla wszystkich różnych plików — podobnie jak w przypadku serwera plików. Jednak w przeciwieństwie do serwera plików repozytorium zawiera całą historię projektu i wszystkie dokonane poprawki.

Jeśli repozytorium jest centralnym magazynem danych, jest to wartość logiczna dla każdego użytkownika, który ma lokalny magazyn danych, dzięki czemu mogą oni z nich korzystać. Jest to tzw. _kopia robocza_. W Visual Studio dla komputerów Mac kopia robocza będzie wyświetlana podobnie jak w przypadku dowolnego innego katalogu lokalnego na komputerze, co pozwala na odczytywanie i zapisywanie plików. Ponieważ jednak Visual Studio dla komputerów Mac ma integrację systemu kontroli wersji, można użyć Subversion i git bez opuszczania środowiska IDE.

Subversion to scentralizowany system kontroli wersji, który oznacza, że istnieje pojedynczy serwer, który zawiera wszystkie pliki i poprawki, z których użytkownicy mogą wyewidencjonować dowolną wersję dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium podwersji, użytkownik otrzymuje migawkę repozytorium w tym momencie.

Git to rozproszony system kontroli wersji, który umożliwia zespołom równoczesne działanie tych samych dokumentów. Za pomocą narzędzia Git może istnieć pojedynczy serwer, który zawiera wszystkie pliki, ale całe repozytorium jest sklonowane lokalnie na maszynę za każdym razem, gdy repozytorium jest wyewidencjonowane z tego centralnego źródła.

## <a name="basic-concepts"></a>Koncepcje podstawowe

Visual Studio dla komputerów Mac zapewnia obsługę systemów kontroli wersji Git i Subversion. Poniższe artykuły zawierają informacje dotyczące konfigurowania repozytoriów Git i podwersji za pomocą Visual Studio dla komputerów Mac, a także proste funkcje, takie jak przeglądanie, zatwierdzanie i wypychanie zmian.

* [Konfigurowanie repozytorium Git](set-up-git-repository.md)
* [Praca z usługą Git](working-with-git.md)
* [Konfigurowanie repozytorium podwersji](set-up-subversion-repository.md)
* [Praca z podwersją](working-with-subversion.md)

## <a name="see-also"></a>Zobacz także

* [Kontrola wersji w programie Visual Studio (w systemie Windows)](/visualstudio/version-control/)