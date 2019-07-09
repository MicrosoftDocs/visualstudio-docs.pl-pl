---
title: Praca z podwersją
description: Za pomocą rozwiązania Subversion w programie Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: d687215bc91dc01a284c49c141a6e52a16ce9e7a
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692136"
---
# <a name="working-with-subversion"></a>Praca z podwersją

Subversion to scentralizowany system kontroli wersji umożliwiający zapoznaj się z wzorca pojedynczej kopii danych, które scentralizowane. W przeciwieństwie do usługi Git wyewidencjonowywanie repozytorium Subversion nie sklonować całego repozytorium, jedynie tworzy migawkę w danym momencie.

Subversion używa modelu kopiowanie i modyfikowanie scalania, aby użytkownicy mogą jednocześnie pracować na tym samym repozytorium. Oznacza to, że każdy użytkownik tworzy kopię scentralizowane dane, które działają na niezależne lokalnych lub działa. Zmiany użytkowników kopie robocze są scalane w sposób chronologicznym.

Na przykład Wyobraź sobie, że użytkownik A i B użytkownika zapoznaj się z kopiowania z repozytorium zdalnym i poszczególnych plików Modyfikuj. Użytkownik A zakończy się zmian i zatwierdzeń je zdalnie. Zanim użytkownik B zatwierdzeń swoją pracę, należy zaktualizować ich kopia robocza, ze zmianami z lokalizacji zdalnej, scalanie zmian przez użytkownika A.

Poniższe sekcje Poznaj, jak Subversion może służyć do kontroli wersji w programie Visual Studio dla komputerów Mac.

Na poniższym obrazie przedstawiono opcje dostarczane przez program Visual Studio dla komputerów Mac przez element menu kontroli wersji:

![Elementy menu kontroli wersji](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Wyewidencjonowanie...

Przed rozpoczęciem pracy zdalne repozytorium systemu Subversion, zapoznaj się z repozytorium tak, aby utworzyć funkcjonalną kopię tego katalogu na komputerze lokalnym.

Aby dowiedzieć się o używaniu **wyewidencjonowania** funkcji w programie Visual Studio dla komputerów Mac, należy wykonać czynności opisane w [Konfigurowanie repozytorium podwersji](set-up-subversion-repository.md) sekcji.

## <a name="update-solution"></a>Aktualizowanie rozwiązania

Korzystając z repozytorium zdalnego, to należy pamiętać, że inni użytkownicy modyfikuje plików, tworzenie kopii roboczej przestarzałe. W oczekiwaniu konflikty zawsze zaleca się ściągnąć wszystkie zmiany z repozytorium w rozwiązaniu, przed rozpoczęciem pracy i przed zatwierdzeniem. Aby ściągnąć zmiany, wybierz pozycję **kontroli wersji > rozwiązania Update** elementu menu.

## <a name="review-solution-and-commit"></a>Przejrzyj rozwiązanie i zatwierdź

O przegląd zmian dokonanych w plikach, użyj zmiany, polecenia Blame, dziennika i scalić karty na poszczególnych dokumentów, jak pokazano na poniższej ilustracji:

![Wersja kontrolki karty](media/version-control-vcTabs.png)

Przejrzyj wszystkie zmiany w projekcie, przechodząc **kontroli wersji > Przejrzyj rozwiązanie i zatwierdź** element menu:

![Przejrzyj rozwiązanie](media/version-control-vcStatus.png)

To umożliwia wyświetlanie wszystkich zmian w każdym pliku projektu z możliwością przywrócenia, utworzyć poprawki, lub czy zatwierdzić.

Aby przekazać plik do repozytorium zdalnego, naciśnij zatwierdzenia..., wprowadź wiadomość dotyczącą zatwierdzenia i upewnij się, za pomocą przycisku zatwierdzenia:

![Zatwierdzanie pliku](media/version-control-svnCommit.png)

Spowoduje to wysłanie zmiany do repozytorium, gdzie tworzą nowa poprawka wprowadzonych zmian.

## <a name="see-also"></a>Zobacz także

- [Konfigurowanie repozytorium podwersji](set-up-subversion-repository.md)
