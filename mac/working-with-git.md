---
title: Praca z usługą Git
description: Korzystanie z narzędzia Git w Visual Studio dla komputerów Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 767c08505877391d71ca085097a0464d516f4f24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "70108024"
---
# <a name="working-with-git"></a>Praca z usługą Git

Git to rozproszony system kontroli wersji, który umożliwia zespołom równoczesne działanie tych samych dokumentów. Oznacza to, że istnieje centralny serwer, który zawiera wszystkie pliki, ale jeśli repozytorium jest wyewidencjonowane z tego centralnego źródła, całe repozytorium jest sklonowane na komputerze lokalnym.

Poniższe sekcje zapoznają się z sposobem korzystania z usługi Git na potrzeby kontroli wersji w Visual Studio dla komputerów Mac.

## <a name="git-version-control-menu"></a>Menu kontroli wersji Git

Na poniższym obrazie przedstawiono opcje dostępne Visual Studio dla komputerów Mac przez element menu kontroli wersji:

![Element menu kontroli wersji](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Wypychanie i ściąganie

Wypychanie i ściąganie to dwie z najczęściej używanych działań w ramach usługi git. Aby synchronizować zmiany wprowadzone przez inne osoby w repozytorium zdalnym, należy **ściągnąć** z tego miejsca. Odbywa się to w Visual Studio dla komputerów Mac, wybierając pozycję **Kontrola wersji > Aktualizuj rozwiązanie**.

Po zaktualizowaniu plików przejrzyj je i zatwierdzić, a następnie **wypchnij** je do repozytorium zdalnego, aby umożliwić innym osobom dostęp do Twoich zmian. Odbywa się to w Visual Studio dla komputerów Mac przez wybranie pozycji **Kontrola wersji > wypychania zmian**. Spowoduje to wyświetlenie okna dialogowego wypychania, umożliwiające wyświetlenie zatwierdzonych zmian i wybranie gałęzi, do której ma zostać wykonane wypychanie:

![Okno dialogowe pokazujące gałąź do zatwierdzenia](media/version-control-gitPush.png)

Możesz również zatwierdzić i wypchnąć zmiany w tym samym czasie, za pomocą okna dialogowego zatwierdzania:

![Opcja pokazująca, jak zatwierdzić i wypchnąć w tym samym czasie.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Polecenia Blame, Rejestruj i Scalaj

W dolnej części okna wyświetlane są pięć kart, jak pokazano poniżej:

![Karty kontroli wersji](media/version-control-gitTabs.png)

Umożliwiają one wykonywanie następujących czynności:

* **Źródło** — wyświetla plik kodu źródłowego.
* **Zmiany** — wyświetla zmiany w kodzie między plikiem lokalnym a plikiem podstawowym. Możesz również porównać różne wersje pliku z różnych skrótów:

    ![Karta zmiany](media/version-control-gitChange.png)

* **Polecenia Blame** — wyświetla nazwę użytkownika skojarzoną z każdą sekcją kodu.
* **Log** — wyświetla wszystkie zatwierdzenia, godziny, daty, komunikaty i użytkowników odpowiedzialne za plik:

    ![Karta Dziennik](media/version-control-gitLog.png)

* **Scalanie** — ten element może być używany w przypadku konfliktu scalania podczas zatwierdzania pracy. Pokazuje wizualną reprezentację zmian dokonanych przez Ciebie i innego programisty, co pozwala na przejrzyste łączenie obu sekcji kodu.

## <a name="switching-branches"></a>Przełączanie gałęzi

Domyślnie pierwsza gałąź utworzona w repozytorium jest określana jako gałąź **główna** . Między gałęzią główną a innymi nie istnieje technicznie wszystko, ale gałąź główna jest taka, która najczęściej jest przemyślana w zespołach programistycznych jako gałąź "na żywo" lub "produkcja".

Niezależny wiersz rozwoju może być tworzony przez rozgałęzienie (lub inne gałęzie). Zapewnia to nową wersję gałęzi głównej w danym momencie, umożliwiając programowanie niezależnie od tego, co to jest "Live". Używanie gałęzi w ten sposób często jest używane do tworzenia oprogramowania

Użytkownicy mogą utworzyć dowolną liczbę gałęzi dla każdego repozytorium, ale zaleca się, aby po zakończeniu korzystania z gałęzi była ona usuwana, aby zachować zorganizowanie repozytorium.

Gałęzie są wyświetlane w Visual Studio dla komputerów Mac przez przechodzenie do **kontroli wersji > zarządzanie gałęziami i zdalnymi...**:

![Widok gałęzi](media/version-control-gitBranch2.png)

Przejdź do innej gałęzi, wybierając ją na liście i naciskając przycisk **Przełącz do gałęzi** .

Aby utworzyć nową gałąź, wybierz przycisk **Nowy** w oknie dialogowym Konfiguracja repozytorium git. Wprowadź nową nazwę gałęzi:

![Utwórz nową gałąź](media/version-control-gitBranch.png)

Można również ustawić gałąź zdalną dla gałęzi _śledzenia_ . Przeczytaj więcej na temat śledzenia gałęzi w [dokumentacji usługi git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zapoznaj się z bieżącą gałęzią w okienko rozwiązania obok nazwy projektu:

 ![Bieżąca gałąź wyświetlana w konsoli rozwiązania](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Przeglądanie i zatwierdzanie

Aby przejrzeć zmiany w plikach, Skorzystaj z kart zmiany, polecenia Blame, log i Merge w każdym dokumencie przedstawionym wcześniej w tym temacie.

Przejrzyj wszystkie zmiany w projekcie, przechodząc do okna **Kontrola wersji > Przejrzyj rozwiązanie i element menu zatwierdzania** :

![Przejrzyj widok kodu](media/version-control-gitReviewCommit.png)

Umożliwia to wyświetlanie wszystkich zmian w każdym pliku projektu z opcją przywracania, tworzenia poprawki lub zatwierdzania.

Aby zatwierdzić plik do repozytorium zdalnego, naciśnij przycisk **Zatwierdź**, Wprowadź wiadomość dotyczącą zatwierdzenia i Potwierdź przy użyciu przycisku zatwierdzania:

![Zatwierdzanie pliku](media/version-control-gitCommit.png)

Po zatwierdzeniu zmian wypchnij je do zdalnego repozytorium, aby umożliwić innym użytkownikom ich wyświetlanie.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Zobacz też

* [Udostępnianie kodu w programie Visual Studio 2017 i Azure Repos git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)
