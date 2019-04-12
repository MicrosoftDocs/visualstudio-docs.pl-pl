---
title: Konfigurowanie narzędzia kontenerów programu Visual Studio
description: Konfigurowanie narzędzi dostępnych w programie Visual Studio do pracy z kontenerami aparatu Docker.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 6fe51e0067ac15eb8e775786047009411c1e3181
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537968"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Jak skonfigurować narzędzia kontenerów programu Visual Studio

Ustawienia programu Visual Studio można kontrolować niektóre aspekty jak program Visual Studio współpracuje z kontenerami aparatu Docker, w tym ustawienia, które mają wpływ na wydajność i użycie zasobów podczas pracy z kontenerami aparatu Docker.

## <a name="container-tools-settings"></a>Ustawienia narzędzia kontenera

W menu głównym wybierz **Narzędzia > Opcje**i rozwiń **narzędzia kontenerów > Ustawienia**. Ustawienia narzędzia kontenerów są wyświetlane.

::: moniker range="vs-2017"

![Visual Studio, narzędzia kontenerów opcje przedstawiający: Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu, automatycznie uruchom kontenery w tle, automatycznie kill kontenerów na Zamknij rozwiązanie i nie Monituj o ufanie certyfikatu SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Narzędzia kontenerów **ogólne** ustawienia:

![Visual Studio, narzędzia kontenerów opcje przedstawiający: Zainstaluj pulpit platformy Docker, w razie potrzeby i certyfikatu zaufania SSL programu ASP.NET Core.](./media/configure-container-tools/tools-options-1.png)

Narzędzia kontenerów **pojedynczego projektu** i **narzędzia Docker Compose** ustawienia:

![Visual Studio, narzędzia kontenerów opcje przedstawiający: Kill kontenerów na Zamknij projekt, Ściągnij wymagane obrazy platformy Docker w projekcie otwarty i uruchom kontenery w projekcie open.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Poniższa tabela może pomóc zdecydować, jak ustawić te opcje.

::: moniker range="vs-2017"
| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | On | Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów programu Visual Studio rozpocznie operacji ściągania aparatu Docker w tle, tak, aby gdy wszystko będzie gotowe uruchomić kod, obraz, który został już pobrany, lub w trakcie pobierania. Jeśli właśnie trwa ładowanie projektów i przeglądania kodu, możesz Wyłącz tę opcję, aby uniknąć pobierania obrazów kontenerów, które nie są potrzebne. |
| Automatycznie uruchom kontenery w tle | On | Docker Compose | Ponownie do zwiększenia wydajności programu Visual Studio tworzy kontener z instaluje wolumin gotowy do podczas kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować, po utworzeniu kontenera, wyłącz tę opcję. |
| Automatycznie zabij kontenery rozwiązanie, zamknij | On | Docker Compose | Wyłącz tę opcję, jeśli chcesz kontenerów do rozwiązania w celu będą nadal działać po zamknięcie rozwiązania lub zamknięcia programu Visual Studio. |
| Nie monituj o zaufanie certyfikatowi protokołu SSL | Off | Projekty ASP.NET Core 2.1 | Jeśli certyfikatowi protokołu SSL nie jest zaufany, Visual Studio wyświetli monit o za każdym razem, gdy uruchamiasz projekt, chyba że to pole wyboru jest zaznaczone. |
::: moniker-end

::: moniker range=">=vs-2019"

W poniższej tabeli opisano **ogólne** ustawienia:

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Instalowanie programu Desktop platformy Docker w razie potrzeby | Monituj | Pojedynczego projektu, Docker Compose | Wybierz, czy ma zostać wyświetlony monit, jeśli nie zainstalowano platformy Docker pulpitu. |
| Ufać certyfikatowi protokołu SSL programu ASP.NET Core | Monituj | Projekty programu ASP.NET Core 2.x | Po ustawieniu **wiersza mnie**, jeśli certyfikatowi protokołu SSL nie jest zaufany, Visual Studio wyświetli monit o każdym razem, aby uruchomić projekt. |

W poniższej tabeli opisano **pojedynczego projektu** i **narzędzia Docker Compose** ustawienia:

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Ściągnij wymagane obrazy platformy Docker w projekcie open | Prawda | Pojedynczego projektu, Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów programu Visual Studio rozpocznie operacji ściągania aparatu Docker w tle, tak, aby gdy wszystko będzie gotowe uruchomić kod, obraz, który został już pobrany, lub w trakcie pobierania. Jeśli właśnie trwa ładowanie projektów i przeglądania kodu, można ustawić **False** Aby uniknąć pobierania obrazów kontenerów, które nie jest potrzebny. |
| Uruchamiaj kontenery na projekt open | Prawda | Pojedynczego projektu, Docker Compose | Ponownie do zwiększenia wydajności programu Visual Studio tworzy kontener z instaluje wolumin gotowy do podczas kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować, po utworzeniu kontenera, równa **False**. |
| Zamknij zabij kontenery projektu | Prawda | Pojedynczy projekt i narzędzie Docker Compose | Ustaw **False** czy chcesz kontenerów do rozwiązania w celu będą nadal działać po zamknięcie rozwiązania lub zamknięcia programu Visual Studio. |

::: moniker-end
> [!WARNING]
> Jeśli certyfikatowi protokołu SSL nie jest zaufany, a następnie zaznacz odpowiednie pole, aby pominąć monit, żądań sieci web protokołu HTTPS może przestać działać w czasie wykonywania aplikacji lub usługi. W takim przypadku usuń zaznaczenie pola wyboru **nie Monituj** zaznacz pole wyboru Uruchom projekt i wskazać zaufania w wierszu.

## <a name="next-steps"></a>Następne kroki

Dowiedz się więcej o pracy z kontenerami w programie Visual Studio, w tym [Przegląd](visual-studio-tools-for-docker.md).