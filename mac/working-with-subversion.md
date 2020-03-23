---
title: Praca z podwersją
description: Korzystanie z Subversion w programie Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: d687215bc91dc01a284c49c141a6e52a16ce9e7a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692136"
---
# <a name="working-with-subversion"></a>Praca z podwersją

Subversion to scentralizowany system kontroli wersji, który umożliwia wyewidencjonowanie pojedynczej kopii wzorcowej scentralizowanych danych. W przeciwieństwie do Git, wyewidencjonowanie repozytorium Subversion nie klonuje całego repozytorium, zajmuje tylko migawkę w tym momencie.

Subversion używa modelu kopiowania i modyfikowania-scalania, aby umożliwić użytkownikom jednoczesną pracę nad tym samym repozytorium. Oznacza to, że każdy użytkownik tworzy lokalną lub działającą kopię scentralizowanych danych, nad którymi pracuje niezależnie. Zmiany w kopiach roboczych użytkowników są scalane w chronologiczny sposób.

Załóżmy na przykład, że użytkownik A i B zarówno wyewidencjonować kopię z repozytorium zdalnego i każdy zmodyfikować pliki. Użytkownik A kończy modyfikacje i zatwierdza je zdalnie. Zanim użytkownik B zobowiąże się do pracy, musi zaktualizować swoją kopię roboczą ze zmianami ze zdalnego, łącząc zmiany użytkownika A.

W poniższych sekcjach opisano, jak Subversion może służyć do kontroli wersji w programie Visual Studio dla komputerów Mac.

Na poniższej ilustracji przedstawiono opcje dostępne w programie Visual Studio dla komputerów Mac za pomocą elementu menu Kontrola wersji:

![Elementy menu Kontrola wersji](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Checkout...

Przed rozpoczęciem korzystania ze zdalnego repozytorium Subversion, sprawdź repozytorium, aby utworzyć roboczą kopię tego katalogu na komputerze lokalnym.

Aby dowiedzieć się więcej o korzystaniu z funkcji **wyewidencjonowywać** w programie Visual Studio dla komputerów Mac, wykonaj kroki opisane w sekcji [Konfigurowanie repozytorium Subversion.](set-up-subversion-repository.md)

## <a name="update-solution"></a>Rozwiązanie do aktualizacji

Podczas korzystania ze zdalnego repozytorium należy pamiętać, że inni użytkownicy mogą modyfikować pliki, czyniąc kopię roboczą nieaktualną. W oczekiwaniu na konflikty zawsze zaleca się pobranie wszelkich zmian z repozytorium do rozwiązania przed rozpoczęciem pracy i przed zatwierdzeniem. Aby wykonać zmiany ściągania, wybierz pozycję menu **Kontrola wersji > Aktualizuj rozwiązanie.**

## <a name="review-solution-and-commit"></a>Przejrzyj rozwiązanie i zatwierdz się

Aby przejrzeć zmiany w plikach, użyj kart Zmiany, Wina, Dziennik i Scalenie w każdym dokumencie, jak pokazano na poniższej ilustracji:

![Karty kontroli wersji](media/version-control-vcTabs.png)

Przejrzyj wszystkie zmiany w projekcie, przeglądając pozycję menu **Kontrola wersji > i Zatwierdzanie:**

![Sprawdź rozwiązanie](media/version-control-vcStatus.png)

Umożliwia to wyświetlanie wszystkich zmian w każdym pliku projektu z opcją Przywróć, Utwórz poprawkę lub Zatwierdzenie.

Aby zatwierdzić plik do repozytorium zdalnego, naciśnij przycisk Commit..., wprowadź komunikat o zatwierdzeniu i potwierdź za pomocą przycisku Zatwierdzanie:

![Zatwierdzanie pliku](media/version-control-svnCommit.png)

Spowoduje to wysłanie zmian do repozytorium, w którym utworzą nową wersję wszystkich modyfikacji.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie repozytorium Subversion](set-up-subversion-repository.md)
