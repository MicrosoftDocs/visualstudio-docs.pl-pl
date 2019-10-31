---
title: Konfigurowanie narzędzi kontenera programu Visual Studio
description: Skonfiguruj narzędzia dostępne w programie Visual Studio do pracy z kontenerami platformy Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188773"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Jak skonfigurować narzędzia kontenera programu Visual Studio

Za pomocą ustawień programu Visual Studio można kontrolować niektóre aspekty działania programu Visual Studio z kontenerami platformy Docker, w tym ustawienia, które wpływają na wydajność i użycie zasobów podczas pracy z kontenerami platformy Docker.

## <a name="container-tools-settings"></a>Ustawienia narzędzi kontenera

Z menu głównego wybierz polecenie **narzędzia > opcje**i rozwiń węzeł **Narzędzia kontenera > Ustawienia**. Zostaną wyświetlone ustawienia narzędzi kontenerów.

::: moniker range="vs-2017"

![Opcje narzędzi kontenera programu Visual Studio, pokazujące: Automatyczne ściąganie wymaganych obrazów platformy Docker podczas ładowania projektu, automatyczne uruchamianie kontenerów w tle, automatyczne zabicia kontenerów w ramach rozwiązania i Niemonitowanie o zaufanie certyfikatu SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Ustawienia **Ogólne** narzędzi kontenera:

![Opcje narzędzi kontenera programu Visual Studio, pokazujące: Zainstaluj program Docker Desktop w razie konieczności i ufaj ASP.NET Core certyfikatem SSL.](./media/configure-container-tools/tools-options-1.png)

Opcje **pojedynczego projektu** i **Docker Compose** narzędzi kontenera:

![Opcje narzędzi kontenera programu Visual Studio, pokazujące: zabicia kontenerów w zamknięciu projektu, ściąganie wymaganych obrazów platformy Docker w projekcie otwartym i uruchamianie kontenerów przy otwartym projekcie.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Poniższa tabela może pomóc określić, jak ustawić te opcje.

::: moniker range="vs-2017"
| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | On | Docker Compose | W celu zwiększenia wydajności podczas ładowania projektów program Visual Studio rozpocznie operację ściągania platformy Docker w tle, dzięki czemu gdy wszystko będzie gotowe do uruchomienia kodu, obraz jest już pobrany lub proces pobierania. Jeśli właśnie ładujesz projekty i przeglądasz kod, możesz je wyłączyć, aby uniknąć pobierania niepotrzebnych obrazów kontenerów. |
| Automatycznie uruchamiaj kontenery w tle | On | Docker Compose | W celu zwiększenia wydajności program Visual Studio tworzy kontener z instalacjami woluminów gotowymi do kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować czas tworzenia kontenera, wyłącz tę opcję. |
| Automatycznie Kasuj kontenery przy bliskim rozwiązaniu | On | Docker Compose | Wyłącz tę opcję, jeśli chcesz, aby kontenery dla rozwiązania nadal działały po zamknięciu rozwiązania lub zamknięciu programu Visual Studio. |
| Nie Monituj o ufanie certyfikatowi SSL hosta lokalnego | Off | Projekty ASP.NET Core 2,1 | Jeśli certyfikat SSL hosta lokalnego nie jest zaufany, program Visual Studio wyświetli monit przy każdym uruchomieniu projektu, chyba że to pole wyboru jest zaznaczone. |
::: moniker-end

::: moniker range=">=vs-2019"

W poniższej tabeli opisano ustawienia **Ogólne** :

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Zainstaluj program Docker Desktop w razie konieczności | Monituj | Pojedynczy projekt, Docker Compose | Zdecyduj, czy chcesz otrzymywać monity, jeśli program Docker Desktop nie jest zainstalowany. |
| Certyfikat SSL ASP.NET Core zaufania | Monituj | ASP.NET Core 2. x projekty | Gdy ustawisz opcję **Monituj**, jeśli certyfikat protokołu SSL hosta lokalnego nie jest zaufany, program Visual Studio wyświetli monit za każdym razem, gdy uruchomisz projekt. |

W poniższej tabeli opisano ustawienia **pojedynczego projektu** i **Docker Compose** :

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Ściągnij wymagane obrazy platformy Docker w otwartym projekcie | Oznacza | Pojedynczy projekt, Docker Compose | W celu zwiększenia wydajności podczas ładowania projektów program Visual Studio rozpocznie operację ściągania platformy Docker w tle, dzięki czemu gdy wszystko będzie gotowe do uruchomienia kodu, obraz jest już pobrany lub proces pobierania. Jeśli właśnie ładujesz projekty i przeglądasz kod, możesz ustawić **wartość false** , aby uniknąć pobierania niepotrzebnych obrazów kontenerów. |
| Uruchom kontenery przy otwartym projekcie | Oznacza | Pojedynczy projekt, Docker Compose | W celu zwiększenia wydajności program Visual Studio tworzy kontener przed chwilą, tak aby był gotowy do tworzenia i uruchamiania kontenera. Jeśli chcesz kontrolować czas tworzenia kontenera, ustaw **wartość false**. |
| Zatrzymaj kontenery po zamknięciu projektu | Oznacza | Pojedynczy projekt i Docker Compose | Ustaw **wartość false** , jeśli chcesz, aby kontenery dla rozwiązania nadal działały po zamknięciu rozwiązania lub zamknięciu programu Visual Studio. |

::: moniker-end
> [!WARNING]
> Jeśli certyfikat protokołu SSL hosta lokalnego nie jest zaufany i zaznaczasz pole, aby pominąć monitowanie, żądania sieci Web HTTPS mogą kończyć się niepowodzeniem w czasie wykonywania w aplikacji lub usłudze. W takim przypadku Usuń zaznaczenie pola wyboru nie **Monituj** , Uruchom projekt i wskaż polecenie Ufaj w wierszu polecenia.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat pracy z kontenerami w programie Visual Studio można znaleźć w tym [omówieniu](overview.md).