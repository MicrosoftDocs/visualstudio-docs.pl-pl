---
title: Praca z podwersją
description: Używanie Subversion w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 909da0bcb1ad3ca080d6bf4ba4e5184c1c2da98f
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402642"
---
# <a name="working-with-subversion"></a>Praca z podwersją

Subversion to scentralizowany system kontroli wersji, który umożliwia wyewidencjonowanie jednej głównej kopii scentralizowanych danych. W przeciwieństwie do usługi git, wyewidencjonowanie repozytorium podwersji nie powoduje klonowania całego repozytorium, w tym momencie wykonuje jedynie migawkę.

Funkcja Subversion korzysta z modelu Copy-Modify-Merge, aby umożliwić użytkownikom jednoczesne działanie tego samego repozytorium. Oznacza to, że każdy użytkownik tworzy lokalną lub działającą kopię scentralizowanych danych, które działają niezależnie od siebie. Zmiany w kopiach roboczych użytkowników są scalane w sposób chronologiczny.

Załóżmy na przykład, że użytkownik A i użytkownik B wyewidencjonuje kopię z repozytorium zdalnego i każdy z nich modyfikuje pliki. Użytkownik A kończy modyfikacje i zatwierdza je zdalnie. Zanim użytkownik B zatwierdzi swoją pracę, musi zaktualizować swoją kopię roboczą o zmiany ze zdalnego, scalając w zmianach użytkownika A.

W poniższych sekcjach opisano, jak Podwersja może być używana do kontroli wersji w Visual Studio dla komputerów Mac.

Na poniższej ilustracji przedstawiono opcje dostępne Visual Studio dla komputerów Mac przez element menu kontroli wersji:

![Elementy menu kontroli wersji](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Wyewidencjonowywanie...

Przed rozpoczęciem korzystania ze zdalnego repozytorium podwersji Sprawdź repozytorium, aby utworzyć działającą kopię tego katalogu na komputerze lokalnym.

Aby dowiedzieć się więcej o korzystaniu z funkcji **wyewidencjonowywania** w Visual Studio dla komputerów Mac, wykonaj kroki opisane w sekcji [Konfigurowanie repozytorium Subversion](set-up-subversion-repository.md) .

## <a name="update-solution"></a>Aktualizuj rozwiązanie

W przypadku korzystania z repozytorium zdalnego należy pamiętać, że inni użytkownicy mogą modyfikować pliki, powodując nieaktualną kopię roboczą. W przewidywaniu konfliktów zawsze zaleca się ściąganie wszelkich zmian z repozytorium do rozwiązania przed rozpoczęciem pracy i przed zatwierdzeniem. Aby wykonać zmiany ściągnięcia, wybierz element menu **> aktualizacji kontroli wersji** .

## <a name="review-solution-and-commit"></a>Przejrzyj rozwiązanie i zatwierdź

Aby przejrzeć zmiany w plikach, użyj kart zmiany, polecenia Blame, log i Merge w każdym dokumencie, jak pokazano na poniższej ilustracji:

![Karty kontroli wersji](media/version-control-vcTabs.png)

Przejrzyj wszystkie zmiany w projekcie, przeglądając elementy menu **Kontrola wersji > Przejrzyj rozwiązanie i zatwierdź** :

![Przejrzyj rozwiązanie](media/version-control-vcStatus.png)

Umożliwia to wyświetlanie wszystkich zmian w każdym pliku projektu z opcją przywracania, tworzenia poprawek lub zatwierdzania.

Aby zatwierdzić plik do repozytorium zdalnego, naciśnij pozycję Zatwierdź..., Wprowadź wiadomość dotyczącą zatwierdzenia i Potwierdź przy użyciu przycisku zatwierdzania:

![Zatwierdzanie pliku](media/version-control-svnCommit.png)

Spowoduje to wysłanie zmian do repozytorium, w którym zostanie utworzona nowa poprawka wszystkich modyfikacji.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie repozytorium Subversion](set-up-subversion-repository.md)
