---
title: Praca z usługą Git
description: Za pomocą narzędzia Git w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: ba98312617aaf636ee388ec97f47c14ede75507d
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58573106"
---
# <a name="working-with-git"></a>Praca z usługą Git

Git to Rozproszony system kontroli wersji umożliwiający zespoły mogą pracować na tym samym dokumentach jednocześnie. Oznacza to, że jest centralny serwer, który zawiera wszystkie pliki, ale jeśli repozytorium jest wyewidencjonowany z tego źródła centralnej, całe repozytorium został sklonowany do komputera lokalnego.

W poniższych sekcjach przedstawimy, jak Git może służyć do kontroli wersji w programie Visual Studio dla komputerów Mac.

## <a name="git-version-control-menu"></a>Menu Kontrola wersji Git

Na poniższej ilustracji przedstawiono opcje dostarczane przez program Visual Studio dla komputerów Mac przez element menu kontroli wersji:

![Element menu kontroli wersji](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Wypychanie i ściąganie

Wypychanie i ściąganie są dwa najczęściej używane akcje w ramach usługi Git. Aby zsynchronizować zmiany zostały wprowadzone do repozytorium zdalnego dla innych osób, musisz mieć **ściągnięcia** z tego miejsca. Odbywa się w programie Visual Studio dla komputerów Mac, wybierając **kontroli wersji > rozwiązania Update**.

Gdy zaktualizowane pliki, przeglądane i zatwierdzane ich należy następnie **wypychania** ich do repozytorium zdalnego, aby umożliwić innym osobom uzyskanie dostępu do zmiany. Odbywa się w programie Visual Studio dla komputerów Mac, wybierając **kontroli wersji > wypychanie zmian**. Spowoduje to wyświetlić okno dialogowe wypychania, który umożliwia przeglądanie zatwierdzone zmiany i wybierz gałąź, aby wypchnąć do:

![Okno dialogowe z wyświetloną gałęzi, aby zatwierdzić](media/version-control-gitPush.png)

Można także zatwierdzić i wypchnąć zmiany w tym samym czasie, za pomocą okna dialogowego zatwierdzenia:

![Opcja pokazujący sposób Zatwierdź i Wypchnij w tym samym czasie.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Polecenia blame dziennika i scalania

W dolnej części okna istnieje pięć kart wyświetlane, jak przedstawiono poniżej:

![Wersja kontrolki karty](media/version-control-gitTabs.png)

Umożliwiają one następujące akcje:

* **Źródło** -Wyświetla pliku kodu źródłowego.
* **Zmiany** -wyświetla zmiany kodu między plik lokalny i pliku podstawowego. Można również porównać różnych wersji pliku z różnych skrótów:

    ![Karta zmiany](media/version-control-gitChange.png)

* **Polecenia blame** -Wyświetla nazwę użytkownika skojarzonego z każdej sekcji kodu.
* **Dziennik** -Wyświetla wszystkie zatwierdzenia, godziny, daty, wiadomości i użytkowników, którzy są odpowiedzialni za pliku:

    ![Karta dziennika](media/version-control-gitLog.png)

* **Scalanie** — może to służyć w przypadku konfliktu scalania podczas zatwierdzania pracy. Pokazuje wizualną reprezentację zmiany wprowadzone przez Ciebie i innych deweloperów, dzięki czemu możesz połączyć obie sekcje kodu nie pozostawia żadnych śladów.

## <a name="switching-branches"></a>Przełączanie gałęzi

Domyślnie pierwszej gałęzi, które są tworzone w repozytorium jest znany jako **wzorzec** gałęzi. Nie ma pod względem technicznym żadnych różnic między głównej gałęzi i inne, ale gałąź główna jest tą, która jest w większości przypadków traktować w zespołów programistycznych jako gałąź "live" lub "produkcja".

Niezależnie od wiersza rozwoju mogą być tworzone przez Rozgałęzianie poza głównego (lub dowolnej innej gałęzi istotnego dla badania). Dzięki temu można nowej wersji głównej gałęzi w punkcie w czasie, co do tworzenia aplikacji, niezależnie od co to jest "live". Korzystając z odgałęzień w ten sposób jest często używana na potrzeby funkcji podczas tworzenia oprogramowania

Użytkownicy mogą tworzyć jako wiele gałęzi, takich jak ich dla każdego repozytorium, ale zaleca się, że po zakończeniu ich przy użyciu gałęzi, ich usunięcia go, aby zachować repozytorium organizacji.

Gałęzie są wyświetlane w programie Visual Studio dla komputerów Mac, przechodząc do **kontroli wersji > Zarządzanie gałęziami i źródłami zdalnymi...** :

![Wyświetl gałęzi](media/version-control-gitBranch2.png)

Przełącz na inną gałąź, wybierając ją na liście i naciskając klawisz **Przełącz do gałęzi** przycisku.

Aby utworzyć nowy Wybierz gałąź **New** przycisk w oknie dialogowym Konfiguracja repozytorium Git. Wprowadź nową nazwę gałęzi:

![Utwórz nową gałąź](media/version-control-gitBranch.png)

Można również ustawić gałęzi zdalnej, Twoje _śledzenia_ gałęzi. Przeczytaj więcej na temat śledzenia gałęzi, skorzystaj z [dokumentacja usługi Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zobacz bieżącej gałęzi w konsoli rozwiązania, obok nazwy projektu:

 ![Bieżąca gałąź wyświetlane w konsoli rozwiązania](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Przeglądu i zatwierdzania

O przegląd zmian dokonanych w plikach, użyj zmiany, polecenia Blame, dzienników i scalić kartach każdego dokumentu, przedstawione wcześniej w tym temacie.

Przejrzyj wszystkie zmiany w projekcie, przechodząc do **kontroli wersji > Przejrzyj rozwiązanie i zatwierdź** element menu:

![Sprawdź widok kodu](media/version-control-gitReviewCommit.png)

Umożliwia to wyświetlanie wszystkich zmian w każdym pliku projektu z możliwością przywrócenia, Utwórz poprawkę lub czy zatwierdzić.

Aby przekazać plik do repozytorium zdalnego, naciśnij klawisze **zatwierdzenia**, wprowadź wiadomość dotyczącą zatwierdzenia i upewnij się, za pomocą przycisku zatwierdzenia:

![Zatwierdzanie pliku](media/version-control-gitCommit.png)

Raz zostały zatwierdzone zmiany i przekazać je do repozytorium zdalnego, aby umożliwić innym użytkownikom je zobaczyć.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Zobacz także

* [Udostępnij swój kod za pomocą programu Visual Studio 2017 i Azure repozytoriów Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)