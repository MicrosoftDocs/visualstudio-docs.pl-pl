---
title: Python w programie Visual Studio krok 6, praca z Git
titleSuffix: ''
description: Krok 6 podstawowego przewodnika pythona w programie Visual Studio, obejmujący funkcje związane z git programu Visual Studio.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "72289718"
---
# <a name="step-6-work-with-git"></a>Krok 6: Praca z Git

**Poprzedni krok: [Instalowanie pakietów i zarządzanie środowiskiem Pythona](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio zapewnia bezpośrednią integrację z lokalnymi repozytoriami Git i zdalnymi repozytoriami w usługach, takich jak GitHub i Repozytorium platformy Azure. Integracja obejmuje klonowanie repozytorium, zatwierdzanie zmian i zarządzanie gałęziami.

Ten artykuł zawiera podstawowe omówienie tworzenia lokalnego repozytorium Git dla istniejącego projektu i zapoznania się z niektórymi funkcjami związanymi z git programu Visual Studio.

1. Po otwarciu projektu w programie Visual Studio, takim jak projekt z [poprzedniego kroku,](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj rozwiązanie do kontroli źródła.** Visual Studio tworzy lokalne repozytorium Git, który zawiera kod projektu.

1. Gdy visual studio wykryje, że projekt jest zarządzany w repozytorium Git związane formanty pojawiają się w prawym dolnym rogu okna programu Visual Studio. Formanty pokazują oczekujące zatwierdzenia, zmiany, nazwę repozytorium i gałąź. Umieść wskaźnik myszy na formanty, aby wyświetlić dodatkowe informacje.

    ![Dodatkowe informacje są wyświetlane po najechaniu kursorem na kontrolkę Git w oknie programu Visual Studio](media/working-with-git-01.png)

1. Po utworzeniu nowego repozytorium lub wybraniu dowolnego z formantów Git program Visual Studio otwiera okno **Eksploratora zespołu.** (Okno można otworzyć w dowolnym momencie za pomocą polecenia menu **Wyświetl** > **Eksploratora** zespołu). Okno ma trzy główne okienka, które przełączają się między użyciem listy rozwijanej w nagłówku **Eksploratora zespołu.** Okienko **Synchronizacja,** które zapewnia operacje publikowania, pojawia się również po wybraniu kontrolki **Push** (ikona strzałki w górę):

    ![Eksplorator zespołu w programie Visual Studio po utworzeniu lokalnego repozytorium](media/working-with-git-02.png)

1. Wybierz **opcję Zmiany** (lub kontrolkę Git z ikoną ołówka), aby przejrzeć niezatwierdzone zmiany i zatwierdzić je w razie potrzeby.

    ![Eksplorator zespołu w programie Visual Studio z niezatwierdzonych zmianami](media/working-with-git-03.png)

    Kliknij dwukrotnie plik na liście **Zmiany,** aby otworzyć widok różnicowy dla tego pliku:

    ![Widok różnicy dla zmian w pliku](media/working-with-git-05.png)

1. Wybierz **opcję Gałęzie** (lub kontrolka Git z nazwą gałęzi), aby zbadać gałęzie i wykonać operacje scalania i ponownego bazowania:

    ![Eksplorator zespołu w programie Visual Studio z oddziałami](media/working-with-git-04.png)

1. Wybierając kontrolkę Git z nazwą repozytorium **(CosineWave** w poprzednim obrazie), **Team Explorer** pokazuje interfejs **Connect,** za pomocą którego można szybko przełączyć się do innego repozytorium całkowicie.

1. Podczas korzystania z lokalnego repozytorium zatwierdzone zmiany przejść bezpośrednio do repozytorium. Jeśli masz połączenie z repozytorium zdalnym, wybierz nagłówek rozwijany w **Eksploratorze zespołu**, wybierz **pozycję Synchronizuj,** aby przełączyć się do sekcji **Synchronizacja,** i pracuj z **wyświetlonymi** tam poleceniami **Ściągnij** i Pobierz.

## <a name="go-deeper"></a>Głębiej

Aby uzyskać krótki instruktaż tworzenia projektu z zdalnego repozytorium Git, zobacz [Szybki start: Klonowanie repozytorium kodu języka Python w programie Visual Studio](quickstart-03-python-in-visual-studio-project-from-repository.md).

Aby uzyskać znacznie bardziej kompleksowy samouczek, w tym obsługę konfliktów scalania, przeglądanie kodu za pomocą żądań ściągnięcia, zmiany dotyczące przekładania i wybierania wiśni między gałęziami, zobacz [Wprowadzenie do git i usługi Azure Repos](/azure/devops/repos/git/gitquickstart).

## <a name="tutorial-review"></a>Recenzja samouczka

Gratulujemy ukończenia tego samouczka na temat języka Python w programie Visual Studio. W tym samouczku dowiesz się, jak:

- Tworzenie projektów i wyświetlanie zawartości projektu.
- Użyj edytora kodu i uruchom projekt.
- Użyj **interaktywnego** okna, aby opracować nowy kod i łatwo skopiować ten kod do edytora.
- Uruchom ukończony program w debugerze programu Visual Studio.
- Instalowanie pakietów i zarządzanie środowiskami Języka Python.
- Praca z kodem w repozytorium Git.

W tym miejscu zapoznaj się z przewodnikami pojęć i poradnikami, w tym następującymi artykułami:

- [Tworzenie rozszerzenia języka C++ dla języka Python](working-with-c-cpp-python-in-visual-studio.md)
- [Publikowanie w usłudze Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Profilowania](profiling-python-code-in-visual-studio.md)
- [Testy jednostkowe](unit-testing-python-in-visual-studio.md)
