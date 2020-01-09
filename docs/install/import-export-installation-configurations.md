---
title: Importowanie lub eksportowanie konfiguracji instalacji
titleSuffix: ''
description: Dowiedz się, jak wyeksportować konfigurację instalacji do pliku. vsconfig, aby udostępnić je innym osobom i jak zaimportować ją do klonowania.
ms.date: 05/18/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dddd34c9d57497a011f58bdb643c670ed84f6ded
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596856"
---
# <a name="import-or-export-installation-configurations"></a>Importowanie lub eksportowanie konfiguracji instalacji

Program Visual Studio można skonfigurować w całej organizacji przy użyciu plików konfiguracji instalacji. Aby to zrobić, po prostu wyeksportuj informacje o obciążeniu i składniku do pliku. vsconfig za pomocą Instalatora programu Visual Studio. Następnie można zaimportować konfigurację do nowych lub istniejących instalacji i udostępnić je innym osobom.

Poniżej przedstawiono sposób.

::: moniker range="vs-2017"

> [!NOTE]
> Ta funkcja jest dostępna tylko w programie Visual Studio 2017 w wersji 15,9 lub nowszej.

::: moniker-end

## <a name="export-a-configuration"></a>Eksportowanie konfiguracji

Możesz wyeksportować plik konfiguracji instalacji z wcześniej zainstalowanego wystąpienia programu Visual Studio lub już instalowanego.

1. Otwórz Instalator programu Visual Studio.

1. Na karcie produkt wybierz przycisk **więcej** , a następnie wybierz pozycję **Eksportuj konfigurację**.

   ![Eksportowanie konfiguracji z karty produkt w Instalatorze programu Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Przeglądaj w poszukiwaniu lub wpisz lokalizację, w której chcesz zapisać plik. vsconfig, a następnie wybierz pozycję **Przejrzyj szczegóły**.

   ![Eksportuj konfigurację z Instalatora programu Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Upewnij się, że masz wybrane obciążenia i składniki, a następnie wybierz pozycję **Eksportuj**.

## <a name="import-a-configuration"></a>Importowanie konfiguracji

Gdy wszystko jest gotowe do zaimportowania pliku konfiguracji instalacji, wykonaj następujące kroki.

1. Otwórz Instalator programu Visual Studio.

1. Na karcie produkt wybierz przycisk **więcej** , a następnie wybierz pozycję **Importuj konfigurację**.

1. Zlokalizuj plik vsconfig, który chcesz zaimportować, a następnie wybierz pozycję **Przejrzyj szczegóły**.

1. Upewnij się, że masz wybrane obciążenia i składniki, a następnie wybierz pozycję **Zamknij**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automatycznie Instaluj brakujące składniki

**Nowość w programie Visual Studio 2019**: gdy zapisujesz plik. vsconfig w katalogu głównym rozwiązania, a następnie otworzysz rozwiązanie, program Visual Studio automatycznie wykryje składniki, których brakuje, i wyświetli monit o ich zainstalowanie.

![Eksplorator rozwiązań sugeruje dodatkowe składniki](../install/media/vs-2019/solution-explorer-config-file.png)

Możesz również wygenerować plik. vsconfig bezpośrednio z Eksplorator rozwiązań.

1. Kliknij prawym przyciskiem myszy plik rozwiązania.

1. Wybierz pozycję Dodaj **plik konfiguracji instalacji**>.

1. Potwierdź lokalizację, w której chcesz zapisać plik. vsconfig, a następnie wybierz pozycję **Przejrzyj szczegóły**.

1. Upewnij się, że masz wybrane obciążenia i składniki, a następnie wybierz pozycję **Eksportuj**.

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz wpis w blogu [Konfigurowanie programu Visual Studio w organizacji za pomocą. vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji opartej na sieci, programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach](set-defaults-for-enterprise-deployments.md)
