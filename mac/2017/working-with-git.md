---
title: Praca z usługą Git
description: Korzystanie z git w programie Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 33148c5202251525504864f26177da4497b5fabe
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983568"
---
# <a name="working-with-git"></a>Praca z usługą Git

Git to rozproszony system kontroli wersji, który umożliwia zespołom jednoczesną pracę nad tymi samymi dokumentami. Oznacza to, że istnieje serwer centralny, który zawiera wszystkie pliki, ale gdy repozytorium jest wyewidencjonowany z tego centralnego źródła, całe repozytorium jest klonowane do komputera lokalnego.

W poniższych sekcjach opisano, jak git może być używany do kontroli wersji w programie Visual Studio dla komputerów Mac.

## <a name="git-version-control-menu"></a>Menu sterowania wersją gita

Na poniższej ilustracji przedstawiono opcje dostępne w programie Visual Studio dla komputerów Mac za pomocą elementu menu Kontrola wersji:

![Element menu Kontrola wersji](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Naciskaj i ciągnij

Pchanie i ciągnięcie to dwie najczęściej używane akcje w Git. Aby zsynchronizować zmiany wprowadzone przez inne osoby w repozytorium zdalnym, należy **stamtąd wyciągnąć.** Odbywa się to w programie Visual Studio dla komputerów Mac, wybierając **formę kontroli wersji > rozwiązanie do aktualizacji**.

Po zaktualizowaniu plików, przejrzeniu i zauwoleniu należy je **wypchnąć** do zdalnego repozytorium, aby umożliwić innym osobom dostęp do zmian. Odbywa się to w programie Visual Studio dla komputerów Mac, wybierając pozycję **Kontrola wersji > zmiany wypychania**. Spowoduje to wyświetlenie okna dialogowego Wypychanie, umożliwiające wyświetlanie zatwierdzonych zmian, i wybranie gałęzi do wypychania:

![Okno dialogowe przedstawiające gałąź, do którego chcesz się zobowiązać](media/version-control-gitPush.png)

Można również zatwierdzać i wypychać zmiany w tym samym czasie, za pośrednictwem okna dialogowego Zatwierdzanie:

![Opcja pokazująca, jak zatwierdzać i wypychać w tym samym czasie.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Wina, Dziennik i Scalanie

W dolnej części okna wyświetlanych jest pięć kart, jak pokazano poniżej:

![Karty kontroli wersji](media/version-control-gitTabs.png)

Umożliwiają one następujące działania:

* **Źródło** — wyświetla plik kodu źródłowego.
* **Zmiany** — wyświetla zmianę kodu między plikiem lokalnym a plikiem podstawowym. Można również porównać różne wersje pliku z różnych skrótów:

    ![Karta Zmiany](media/version-control-gitChange.png)

* **Blame** - Wyświetla nazwę użytkownika skojarzonego z każdą sekcją kodu.
* **Dziennik** — wyświetla wszystkie zatwierdzenia, godziny, daty, wiadomości i użytkowników odpowiedzialnych za plik:

    ![Karta Dziennik](media/version-control-gitLog.png)

* **Scalanie** — może to być używane, jeśli masz konflikt scalania podczas zatwierdzania pracy. Pokazuje wizualną reprezentację zmian wprowadzonych przez Ciebie i innego dewelopera, co pozwala na połączenie obu sekcji kodu czysto.

## <a name="switching-branches"></a>Przełączanie gałęzi

Domyślnie pierwsza gałąź utworzona w repozytorium jest znana jako **gałąź główna.** Nie ma technicznie nic innego między gałęzią główną a żadną inną, ale gałąź główna jest tą, która jest najczęściej uważana w zespołach programistycznych za gałąź "na żywo" lub "produkcyjną".

Niezależna linia rozwoju może być utworzona przez rozgałęzienie master (lub innej gałęzi, o to chodzi). Zapewnia to nową wersję gałęzi głównej w momencie w czasie, co pozwala na rozwój niezależnie od tego, co jest "na żywo". Korzystanie z gałęzi w ten sposób jest często używane do funkcji w tworzeniu oprogramowania

Użytkownicy mogą tworzyć dowolną liczbę gałęzi dla każdego repozytorium, ale zaleca się, aby po zakończeniu korzystania z gałęzi została usunięta w celu zorganizowania repozytorium.

Gałęzie są wyświetlane w programie Visual Studio dla komputerów Mac, przeglądając **system Kontroli wersji > zarządzaj gałęziami i pilotami...**:

![Widok Gałęzie](media/version-control-gitBranch2.png)

Przełącz się do innej gałęzi, zaznaczając ją na liście i naciskając przycisk **Przełącz na gałąź.**

Aby utworzyć nową gałąź, wybierz przycisk **Nowy** w oknie dialogowym konfiguracji repozytorium Git. Wprowadź nową nazwę gałęzi:

![Tworzenie nowej gałęzi](media/version-control-gitBranch.png)

Można również ustawić odgałęzienie zdalne do gałęzi _śledzenia._ Przeczytaj więcej o śledzeniu gałęzi w [dokumentacji Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zobacz bieżącą gałąź w panelu rozwiązania, obok nazwy projektu:

 ![Bieżąca gałąź wyświetlana w konsoli rozrachywniczej](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Przeglądanie i zatwierdzanie

Aby przejrzeć zmiany w plikach, użyj kart Zmiany, Wina, Dziennik i Scal w każdym dokumencie, zilustrowanych wcześniej w tym temacie.

Przejrzyj wszystkie zmiany w projekcie, przeglądając pozycję menu **Kontrola wersji > i Zatwierdzanie:**

![Przejrzyj widok kodu](media/version-control-gitReviewCommit.png)

Umożliwia to wyświetlanie wszystkich zmian w każdym pliku projektu z opcją Powrót, Tworzenie poprawki lub Zatwierdzanie.

Aby zatwierdzić plik do repozytorium zdalnego, naciśnij przycisk **Commit**, wprowadź komunikat zatwierdzenia i potwierdź za pomocą przycisku Zatwierdzanie:

![Zatwierdzanie pliku](media/version-control-gitCommit.png)

Po zaślepeniu zmian wypchnij je do zdalnego repozytorium, aby umożliwić innym użytkownikom ich wyświetlanie.

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Zobacz też

* [Udostępnianie kodu za pomocą programu Visual Studio 2017 i platformy Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)