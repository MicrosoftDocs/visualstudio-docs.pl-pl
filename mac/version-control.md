---
title: Kontrola wersji
description: Korzystanie z git i subversion w programie Visual Studio dla komputerów Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "70108097"
---
# <a name="version-control"></a>Kontrola wersji

Kontrola wersji to system zarządzania plikami w wielu różnych wersjach i - w tworzeniu oprogramowania - jest zazwyczaj przyczynia się do wielu programistów. Głównym celem dowolnego systemu kontroli wersji _(VCS)_ jest znalezienie rozwiązania, które umożliwia wszystkim użytkownikom pracę na bazie kodu w tym samym czasie.

Sednem każdego systemu kontroli wersji jest _repozytorium,_ które działa jako centralny magazyn danych dla wszystkich różnych plików - podobne do serwera plików. Jednak w przeciwieństwie do serwera plików repozytorium zawiera całą historię projektu i wszystkie poprawki, które zostały wprowadzone.

Jeśli repozytorium jest centralnym magazynem danych, logiczne jest, aby każdy użytkownik miał lokalny magazyn danych, umożliwiając im pracę nad nim. Jest to tak zwana _kopia robocza_. W programie Visual Studio for Mac kopia robocza będzie wyświetlana tak samo, jak każdy inny katalog lokalny na komputerze, co umożliwia odczytywanie i zapisywanie do dowolnego z plików. Jednak ponieważ Visual Studio dla komputerów Mac ma integrację systemu kontroli wersji, można użyć Subversion i Git bez opuszczania IDE.

Subversion to scentralizowany system kontroli wersji, co oznacza, że istnieje jeden serwer, który zawiera wszystkie pliki i poprawki, z których użytkownicy mogą wyewidencjonować dowolną wersję dowolnego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium Subversion, użytkownik pobiera migawkę repozytorium w tym momencie.

Git to rozproszony system kontroli wersji, który umożliwia zespołom jednoczesną pracę nad tymi samymi dokumentami. Z Git może istnieć jeden serwer, który zawiera wszystkie pliki, ale całe repozytorium jest klonowane lokalnie do komputera, gdy repozytorium jest wyewidencjonowany z tego centralnego źródła.

## <a name="basic-concepts"></a>Koncepcje podstawowe

Visual Studio dla komputerów Mac zapewnia obsługę systemów kontroli wersji Git i Subversion. W poniższych artykułach eksplorujemy konfigurowanie repozytoriów Git i Subversion za pośrednictwem programu Visual Studio dla komputerów Mac, a także proste funkcje, takie jak przeglądanie, zatwierdzanie i wypychanie zmian.

* [Konfigurowanie repozytorium Git](set-up-git-repository.md)
* [Praca z usługą Git](working-with-git.md)
* [Konfigurowanie repozytorium podwersji](set-up-subversion-repository.md)
* [Praca z podwersją](working-with-subversion.md)

## <a name="see-also"></a>Zobacz też

* [Kontrola wersji w programie Visual Studio (w systemie Windows)](/visualstudio/version-control/)