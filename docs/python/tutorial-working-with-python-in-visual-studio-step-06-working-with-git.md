---
title: Samouczek Python w programie Visual Studio — krok 6, współpraca z usługą git
titleSuffix: ''
description: Krok 6 podstawowego przewodnika w języku Python w programie Visual Studio, obejmujący funkcje programu Visual Studio związane z usługą git.
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72289718"
---
# <a name="step-6-work-with-git"></a>Krok 6. Współpraca z usługą git

**Poprzedni krok: [Instalowanie pakietów i zarządzanie środowiskiem języka Python](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Program Visual Studio zapewnia bezpośrednią integrację z lokalnymi repozytoriami git i zdalnymi repozytoriami dla usług takich jak GitHub i Azure Repos. Integracja obejmuje klonowanie repozytorium, zatwierdzanie zmian i zarządzanie gałęziami.

Ten artykuł zawiera podstawowe omówienie tworzenia lokalnego repozytorium git dla istniejącego projektu i zaznajomienia się z niektórymi funkcjami związanymi z Git programu Visual Studio.

1. Mając otwarty projekt w programie Visual Studio, taki jak projekt z [poprzedniego kroku](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md), kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj rozwiązanie do kontroli źródła**. Program Visual Studio tworzy lokalne repozytorium git zawierające kod projektu.

1. Gdy program Visual Studio wykryje, że projekt jest zarządzany w repozytorium git, w prawym dolnym rogu okna programu Visual Studio są wyświetlane kontrolki powiązane z Git. Kontrolki pokazują oczekujące zatwierdzenia, zmiany, nazwę repozytorium i gałąź. Umieść kursor nad kontrolkami, aby wyświetlić dodatkowe informacje.

    ![Dodatkowe informacje są wyświetlane po umieszczeniu wskaźnika myszy na kontrolce Git w oknie programu Visual Studio](media/working-with-git-01.png)

1. Po utworzeniu nowego repozytorium lub wybraniu dowolnego z formantów git program Visual Studio otwiera okno **Team Explorer** . (Okno można otworzyć w dowolnym momencie z **widokiem**  >  **Team Explorer** polecenie menu.) Okno ma trzy główne okienka, które można przełączać między przy użyciu listy rozwijanej w nagłówku **Team Explorer** . Okienko **Synchronizacja** , które zapewnia operacje publikowania, jest również wyświetlany po wybraniu kontrolki **push** (ikona strzałki w górę):

    ![Team Explorer w programie Visual Studio po utworzeniu lokalnego repozytorium](media/working-with-git-02.png)

1. Wybierz pozycję **zmiany** (lub kontrolkę git z ikoną ołówka), aby przejrzeć Niezatwierdzone zmiany i zatwierdzić je w razie potrzeby.

    ![Team Explorer w programie Visual Studio pokazujące Niezatwierdzone zmiany](media/working-with-git-03.png)

    Kliknij dwukrotnie plik na liście **zmiany** , aby otworzyć widok diff dla tego pliku:

    ![Widok różnicowy dla zmian w pliku](media/working-with-git-05.png)

1. Wybierz **gałęzie** (lub kontrolkę git z nazwą rozgałęzienia), aby sprawdzać gałęzie i wykonywać operacje scalania i rebase:

    ![Team Explorer w programie Visual Studio pokazujący gałęzie](media/working-with-git-04.png)

1. Wybranie kontrolki git z nazwą repozytorium (**CosineWave** na poprzednim obrazie) powoduje, że **Team Explorer** pokazuje Interfejs **połączenia** , za pomocą którego można całkowicie szybko przełączyć się do innego repozytorium.

1. W przypadku korzystania z repozytorium lokalnego zatwierdzone zmiany są przekazywane bezpośrednio do repozytorium. Jeśli masz połączenie z repozytorium zdalnym, wybierz nagłówek listy rozwijanej w **Team Explorer**, wybierz pozycję **Synchronizuj** , aby przełączyć się do sekcji **Synchronizacja** , i pracuj z wyświetlonymi poleceniami **ściągania** i **pobierania** .

## <a name="go-deeper"></a>Przejdź głębiej

Aby uzyskać krótki przewodnik tworzenia projektu na podstawie zdalnego repozytorium git, zobacz [Szybki Start: klonowanie repozytorium kodu w języku Python w programie Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Aby uzyskać bardziej szczegółowy samouczek, w tym obsługę konfliktów scalania, przeglądanie kodu z żądaniami ściągnięcia, zmiana bazy i selekcjonowanie zmian między gałęziami, zobacz Wprowadzenie [do usługi git i Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Przegląd samouczka

Gratulujemy ukończenia tego samouczka w języku Python w programie Visual Studio. W tym samouczku przedstawiono, jak:

- Twórz projekty i wyświetlaj zawartość projektu.
- Użyj edytora kodu i Uruchom projekt.
- Użyj okna **interaktywnego** , aby opracować nowy kod i łatwo skopiować ten kod do edytora.
- Uruchamianie ukończonego programu w debugerze programu Visual Studio.
- Instalowanie pakietów i zarządzanie środowiskami języka Python.
- Pracuj z kodem w repozytorium git.

W tym miejscu zapoznaj się z pojęciami i przewodnikami instruktażowymi, takimi jak następujące artykuły:

- [Tworzenie rozszerzenia C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilowanie](profiling-python-code-in-visual-studio.md)
- [Testowanie jednostek](unit-testing-python-in-visual-studio.md)
