---
title: Język Python w Visual Studio — samouczek krok 6, pracy z usługą Git
titleSuffix: ''
description: Krok 6 wskazówki podstawowych języka Python w programie Visual Studio, obejmujące funkcje związane z Git programu Visual Studio.
ms.date: 01/28/2019
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 386821867b1f7290fd195322a699eb161536a06b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919862"
---
# <a name="step-6-work-with-git"></a>Krok 6. Praca z usługą Git

**Poprzedniego kroku: [Instalowanie pakietów i zarządzanie nimi w środowisku Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio zapewnia bezpośrednią integrację z usługą lokalne repozytoria Git i repozytoria zdalne w usługach, takich jak GitHub i repozytoriów platformy Azure. Integracja obejmuje klonowanie repozytorium, zatwierdzanie zmian i zarządzania gałęzi.

Ten artykuł zawiera ogólne omówienie tworzenia lokalnego repozytorium Git dla istniejącego projektu i zapoznawanie się z niektórych funkcji związanych z Git programu Visual Studio.

1. Mając otwarty w programie Visual Studio, takie jak projekt z projekt [poprzedniego kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Dodaj rozwiązanie do kontroli źródła**. Program Visual Studio tworzy lokalnego repozytorium Git, który zawiera kod projektu.

1. Gdy Visual Studio wykryje, że projekt jest zarządzana w kontrolkach Git związane z repozytorium Git są wyświetlane na prawym dolnym rogu okna programu Visual Studio. Pokaż formanty oczekujących zatwierdzeń, zmiany nazwy repozytorium i gałąź. Umieść kursor nad formantów, aby wyświetlić dodatkowe informacje.

    ![Dodatkowe informacje są wyświetlane po umieszczeniu wskaźnika myszy nad formantem Git w oknie programu Visual Studio](media/working-with-git-01.png)

1. Podczas tworzenia nowego repozytorium, lub wybierz dowolny z formantów Git, Visual Studio otwiera **Team Explorer** okna. (Okno można otworzyć w dowolnym momencie za pomocą **widoku** > **Team Explorer** polecenia menu.) Okno ma trzy okienka głównych, których możesz przełączać się między za pomocą listy rozwijanej na **Team Explorer** nagłówka. **Synchronizacji** okienko, które udostępnia operacje publikacji, pojawia się również, po wybraniu **wypychania** kontroli (ikonę strzałki w górę):

    ![Team Explorer w programie Visual Studio po utworzeniu repozytorium lokalnego](media/working-with-git-02.png)

1. Wybierz **zmiany** (lub kontroli Git za pomocą ikony ołówka) niezatwierdzone zmiany przejrzeć i zatwierdzić je, jeśli to konieczne.

    ![Team Explorer w programie Visual Studio przedstawiający niezatwierdzone zmiany](media/working-with-git-03.png)

    Kliknij dwukrotnie plik w **zmiany** listy, aby otworzyć widok różnic dla tego pliku:

    ![Widok różnic dla zmian w pliku](media/working-with-git-05.png)

1. Wybierz **gałęzie** (lub kontroli Git o nazwie gałęzi) do badania gałęzi i wykonywania operacji scalania i zmianę bazy:

    ![Team Explorer w programie Visual Studio przedstawiający gałęzi](media/working-with-git-04.png)

1. Wybranie kontrolki Git o nazwie repozytorium (**CosineWave** na poprzedniej ilustracji), **Team Explorer** pokazuje **Connect** interfejs, za pomocą którego możesz szybko przełączyć się do innym repozytorium całkowicie.

1. Korzystając z lokalnego repozytorium, zatwierdzone zmiany przejdź bezpośrednio do repozytorium. Jeśli masz połączenie z repozytorium zdalnym, wybierz nagłówek listy rozwijanej w **Team Explorer**, wybierz **synchronizacji** Aby przełączyć się do **synchronizacji** sekcji oraz pracować z nimi **Ściągnięcia** i **pobrać** poleceń przedstawionych istnieje.

## <a name="go-deeper"></a>Przejdź dalej

Aby uzyskać krótki przewodnik tworzenia projektu ze zdalnego repozytorium Git, zobacz [Szybki Start: Klonowanie repozytorium kodu w języku Python w programie Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Samouczek znacznie bardziej złożone, w tym obsługa konfliktów scalania, przeglądanie kodu za pomocą żądań ściągnięcia, zmienianie bazy i selekcjonowanie zmiany między gałęziami, zobacz [Rozpoczynanie pracy z usługą Git i repozytoriów platformy Azure](/azure/devops/repos/git/gitquickstart?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json&view=vsts&tabs=visual-studio).

## <a name="tutorial-review"></a>Przejrzyj samouczek

Gratulacje z okazji wykonanie kroków tego samouczka w języku Python w programie Visual Studio. W tym samouczku wyjaśniono sposób:

- Tworzenie projektów i wyświetlanie zawartości projektu.
- Za pomocą edytora kodu i uruchomić projekt.
- Użyj **Interactive** okna do tworzenia nowego kodu i łatwo skopiować ten kod do edytora.
- Uruchom program ukończone w debugerze programu Visual Studio.
- Instalowanie pakietów i zarządzanie środowiskami Python.
- Praca z kodem w repozytorium Git.

W tym miejscu zapoznaj się z pojęciami i przewodniki z instrukcjami, łącznie z następującymi artykułami:

- [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilowanie](profiling-python-code-in-visual-studio.md)
- [Testowanie jednostek](unit-testing-python-in-visual-studio.md)
