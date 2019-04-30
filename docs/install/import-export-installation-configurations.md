---
title: Importowanie lub eksportowanie konfiguracji instalacji
titleSuffix: ''
description: Dowiedz się, jak korzystać z funkcji konfiguracji importu/eksportu w programie Visual Studio
ms.date: 04/19/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cd932b1748d5c400c6ab64a56b16d1b6a1458c71
ms.sourcegitcommit: f01d9cab3f9e457b365d58e2008137ce786003fa
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346761"
---
# <a name="import-or-export-installation-configurations"></a>Importowanie lub eksportowanie konfiguracji instalacji

Visual Studio można skonfigurować całej organizacji przy użyciu pliku konfiguracji instalacji. Aby to zrobić, po prostu wyeksportuj obciążenia i informacji o składnikach z plikiem .vsconfig za pomocą Instalatora programu Visual Studio. Następnie można zaimportować konfigurację do nowych lub istniejących instalacji.

Poniżej przedstawiono sposób.

::: moniker range="vs-2017"

> [!NOTE]
> Ta funkcja jest dostępna tylko w programie Visual Studio 2017 w wersji 15.9 lub nowszej.

::: moniker-end

## <a name="export-a-configuration"></a>Eksportowanie konfiguracji

Możesz wyeksportować plik konfiguracji instalacji z uprzednio zainstalowanego wystąpienia programu Visual Studio lub taki, który jest obecnie instalowany.

1. Otwórz Instalatora programu Visual Studio.

1. Na karcie produktu wybierz **więcej** przycisk, a następnie wybierz **konfiguracji eksportu**.

   ![Eksportowanie konfiguracji z karty produktu w Instalatorze programu Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Wyszukaj lub wpisz lokalizację, w którym chcesz zapisać plik .vsconfig, a następnie wybierz **Przejrzyj szczegóły**.

   ![Eksportowanie konfiguracji z poziomu Instalatora programu Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Upewnij się, masz obciążenia i składniki, które chcesz, a następnie wybierz **wyeksportować**.

## <a name="import-a-configuration"></a>Importowanie konfiguracji

Gdy wszystko będzie gotowe do zaimportowania pliku konfiguracji instalacji, wykonaj następujące kroki.

1. Otwórz Instalatora programu Visual Studio.

1. Na karcie produktu wybierz **więcej** przycisk, a następnie wybierz **Konfiguracja importu**.

1. Znajdź, którą chcesz zaimportować, a następnie wybierz plik .vsconfig **Przejrzyj szczegóły**.

1. Upewnij się, masz obciążenia i składniki, które chcesz, a następnie wybierz **Zamknij**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automatyczne zainstalowanie brakujących składników

**Nowość w programie Visual Studio 2019**: Podczas zapisywania pliku .vsconfig z katalogiem głównym rozwiązania i następnie otworzyć rozwiązanie programu Visual Studio automatycznie wykrywa składniki, które są spełnione i wyświetli monit o ich zainstalowanie.

![Eksplorator rozwiązań sugeruje dodatkowych składników](../install/media/vs-2019/solution-explorer-config-file.png)

Można również wygenerować plik .vsconfig bezpośrednio z Eksploratora rozwiązań.

1. Kliknij prawym przyciskiem myszy na plik rozwiązania.

1. Wybierz **Dodaj** > **pliku konfiguracji instalacji**.

1. Upewnij się, lokalizacji, w którym chcesz zapisać plik .vsconfig, a następnie wybierz **Przejrzyj szczegóły**.

1. Upewnij się, masz obciążenia i składniki, które chcesz, a następnie wybierz **wyeksportować**.

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz [Konfigurowanie programu Visual Studio w organizacji za pomocą .vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) wpis w blogu.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji opartej na sieci, programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach](set-defaults-for-enterprise-deployments.md)
