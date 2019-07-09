---
title: Kontrola wersji
description: Przy użyciu narzędzia Git i Subversion w programie Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 33d4fa8b641f71094930d5eac39164916b41f4b4
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692224"
---
# <a name="version-control"></a>Kontrola wersji

Kontroli wersji jest systemem zarządzania plikami na wiele różnych wersji i — w oprogramowaniu opracowywanie zawartości — jest zazwyczaj przyczyniły się do przez wielu deweloperów. Głównym celem dowolnego systemu kontroli wersji (_VC_) ma na celu znalezienie rozwiązań, która umożliwia wszystkim użytkownikom na pracować nad bazy kodu w tym samym czasie.

W samym sercu żadnych kontroli wersji jest system _repozytorium_, który działa jako centralny dane magazynu dla wszystkich różnych plików — podobnie jak na serwerze plików. W przeciwieństwie do serwera plików, repozytorium zawiera całą historię projektu i wszystkie poprawki, które zostały wprowadzone.

Jeśli repozytorium jest magazyn danych w centralnym, jest dla każdego użytkownika lokalnego magazynu danych, umożliwiając im pracować nad nim. Jest to nazywane _kopia robocza_. W programie Visual Studio dla komputerów Mac Twoja kopia robocza pojawi się podobnie jak inne katalogu lokalnym na komputerze co umożliwia odczytywanie i zapisywanie do plików. Jednak program Visual Studio for Mac jest integracja systemu kontroli wersji, dlatego służy Subversion i Git bez opuszczania środowiska IDE.

Subversion to scentralizowany system kontroli wersji, co oznacza, że jest pojedynczego serwera, który zawiera wszystkie pliki i wersje, z których użytkownicy mogą zapoznaj się z dowolną wersję każdego pliku. Gdy pliki są wyewidencjonowane ze zdalnego repozytorium systemu Subversion, użytkownik pobiera migawkę repozytorium w danym momencie.

Git to Rozproszony system kontroli wersji umożliwiający zespoły mogą pracować na tym samym dokumentach jednocześnie. Za pomocą narzędzia Git może być jednym serwerze, który zawiera wszystkie pliki, ale całego repozytorium został sklonowany lokalnie na komputerze w każdym przypadku, gdy repozytorium jest wyewidencjonowany z tego źródła centralnej.

## <a name="basic-concepts"></a>Koncepcje podstawowe

Program Visual Studio for Mac zapewnia obsługę systemów kontroli wersji Git i Subversion. Konfigurowanie repozytoriów Git i Subversion, za pomocą programu Visual Studio dla komputerów Mac, a także proste funkcje, takie jak przeglądanie, zatwierdzanie i wypychaniu zmian można znaleźć, zapoznaj się następujące artykuły.

* [Konfigurowanie repozytorium Git](set-up-git-repository.md)
* [Praca z usługą Git](working-with-git.md)
* [Konfigurowanie repozytorium podwersji](set-up-subversion-repository.md)
* [Praca z podwersją](working-with-subversion.md)

## <a name="see-also"></a>Zobacz także

* [Kontrola wersji w programie Visual Studio (na Windows)](/visualstudio/version-control/)