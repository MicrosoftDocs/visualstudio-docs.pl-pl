---
title: Konfigurowanie narzędzi kontenerów programu Visual Studio
description: Skonfiguruj narzędzia dostępne w programie Visual Studio do pracy z kontenerami platformy Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188773"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Jak skonfigurować narzędzia kontenerów programu Visual Studio

Za pomocą ustawień programu Visual Studio można kontrolować niektóre aspekty pracy programu Visual Studio z kontenerami platformy Docker, w tym ustawienia, które wpływają na wydajność i użycie zasobów podczas pracy z kontenerami platformy Docker.

## <a name="container-tools-settings"></a>Ustawienia narzędzi kontenerowych

Z menu głównego wybierz polecenie **Narzędzia > opcje**i rozwiń pozycję Narzędzia **kontenerów > ustawienia**. Zostaną wyświetlone ustawienia narzędzi kontenera.

::: moniker range="vs-2017"

![Opcje narzędzi kontenerowych programu Visual Studio, z wyświetlonymi: Automatyczne ściąganie wymaganych obrazów platformy Docker przy obciążeniu projektu, Automatyczne uruchamianie kontenerów w tle, Automatyczne zabijanie kontenerów przy zamykaniu rozwiązania i Nie monituj o ufanie certyfikatowi SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Narzędzia kontenerów **Ustawienia ogólne:**

![Opcje narzędzi kontenerowych programu Visual Studio z wyświetlaniem: Instalowanie pulpitu platformy Docker w razie potrzeby oraz certyfikat zaufania ASP.NET core SSL.](./media/configure-container-tools/tools-options-1.png)

Ustawienia **pojedynczego projektu i** **kompozycji docker** narzędzi kontenerowych:

![Opcje narzędzi kontenerów programu Visual Studio, z pokazem: Zabij kontenery przy zamknięciu projektu, Ściągaj wymagane obrazy platformy Docker przy otwartym projekcie i Uruchom kontenery przy otwartym projekcie.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Poniższa tabela może pomóc w podjęciu decyzji, jak ustawić te opcje.

::: moniker range="vs-2017"
| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatyczne ściąganie wymaganych obrazów platformy Docker przy obciążeniu projektu | Włączone | Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów, Visual Studio rozpocznie operację ściągania platformy Docker w tle, dzięki czemu po przygotowaniu do uruchomienia kodu obraz jest już pobrany lub w trakcie pobierania. Jeśli tylko ładujesz projekty i przeglądasz kod, możesz to wyłączyć, aby uniknąć pobierania obrazów kontenerów, których nie potrzebujesz. |
| Automatyczne uruchamianie kontenerów w tle | Włączone | Docker Compose | Ponownie w celu zwiększenia wydajności visual studio tworzy kontener z instalacji woluminu gotowy do podczas tworzenia i uruchamiania kontenera. Jeśli chcesz kontrolować, kiedy kontener jest tworzony, wyłącz to. |
| Automatyczne zabijanie pojemników po zamknięciu roztworu | Włączone | Docker Compose | Wyłącz tę funkcję, jeśli chcesz, aby kontenery dla rozwiązania były nadal uruchamiane po zamknięciu rozwiązania lub zamknięciu programu Visual Studio. |
| Nie monituj o ufanie certyfikatowi SSL hosta lokalnego | Wyłączone | ASP.NET projekty Core 2.1 | Jeśli certyfikat SSL hosta lokalnego nie jest zaufany, program Visual Studio wyświetli monit przy każdym uruchomieniu projektu, chyba że to pole wyboru jest zaznaczone. |
::: moniker-end

::: moniker range=">=vs-2019"

W poniższej tabeli opisano ustawienia **ogólne:**

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| W razie potrzeby zainstaluj pulpit platformy Docker | Monituj mnie | Pojedynczy projekt, docker compose | Wybierz, czy ma zostać wyświetlony monit, jeśli program Docker Desktop nie jest zainstalowany. |
| Zaufaj ASP.NET certyfikatU SSL Core | Monituj mnie | ASP.NET projekty Core 2.x | Po **ustawieniu monituj o certyfikat**SSL hosta lokalnego, program Visual Studio wyświetli monit przy każdym uruchomieniu projektu. |

W poniższej tabeli opisano ustawienia **pojedynczego projektu** i **kompozycji docker:**

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Ściąganie wymaganych obrazów platformy Docker przy otwieraniu projektu | True | Pojedynczy projekt, docker compose | Aby zwiększyć wydajność podczas ładowania projektów, Visual Studio rozpocznie operację ściągania platformy Docker w tle, dzięki czemu po przygotowaniu do uruchomienia kodu obraz jest już pobrany lub w trakcie pobierania. Jeśli tylko ładujesz projekty i kod przeglądania, możesz ustawić **wartość Fałsz,** aby uniknąć pobierania obrazów kontenerów, których nie potrzebujesz. |
| Uruchamianie kontenerów przy otwartym projekcie | True | Pojedynczy projekt, docker compose | Ponownie w celu zwiększenia wydajności visual studio tworzy kontener z wyprzedzeniem, dzięki czemu jest gotowy do podczas tworzenia i uruchamiania kontenera. Jeśli chcesz kontrolować, kiedy kontener jest tworzony, ustaw wartość **Fałsz**. |
| Zatrzymaj kontenery na zamknięciu projektu | True | Pojedynczy projekt i kompozycja docker | Ustaw **false,** jeśli chcesz kontenerów dla rozwiązania, aby kontynuować uruchamianie po zamknięciu rozwiązania lub zamknięciu programu Visual Studio. |

::: moniker-end
> [!WARNING]
> Jeśli certyfikat SSL hosta lokalnego nie jest zaufany i zaznacz pole wyboru, aby pominąć monitowanie, żądania sieci web HTTPS mogą zakończyć się niepowodzeniem w czasie wykonywania w aplikacji lub usłudze. W takim przypadku wyewidencjonuj pole wyboru **Nie monituj,** uruchom projekt i wskaż zaufanie w wierszu polecenia.

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat pracy z kontenerami w programie Visual Studio można przeczytać w tym [eks.](overview.md)