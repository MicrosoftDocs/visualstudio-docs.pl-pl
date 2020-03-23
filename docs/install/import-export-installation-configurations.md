---
title: Importowanie lub eksportowanie konfiguracji instalacji
titleSuffix: ''
description: Dowiedz się, jak wyeksportować konfigurację instalacji do pliku vsconfig, aby udostępnić go innym osobom, oraz jak zaimportować go do klonowania.
ms.date: 05/18/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 12d22334094b848350d44d245685532fed196389
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114842"
---
# <a name="import-or-export-installation-configurations"></a>Importowanie lub eksportowanie konfiguracji instalacji

Program Visual Studio można skonfigurować w całej organizacji za pomocą plików konfiguracji instalacji. Aby to zrobić, po prostu wyeksportuj informacje o obciążeniu i składniku do pliku vsconfig przy użyciu instalatora programu Visual Studio. Następnie można zaimportować konfigurację do nowych lub istniejących instalacji i udostępnić je również innym osobom.

Oto jak to zrobić.

::: moniker range="vs-2017"

> [!NOTE]
> Ta funkcja jest dostępna tylko w programie Visual Studio 2017 w wersji 15.9 i nowszej.

::: moniker-end

## <a name="export-a-configuration"></a>Eksportowanie konfiguracji

Można wyeksportować plik konfiguracji instalacji z wcześniej zainstalowanego wystąpienia programu Visual Studio lub z aktualnie instalowanych.

1. Otwórz Instalatora programu Visual Studio.

1. Na karcie produktu wybierz przycisk **Więcej,** a następnie wybierz pozycję **Eksportuj konfigurację**.

   ![Eksportowanie konfiguracji z karty produktu w instalatorze programu Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Przejdź do lokalizacji, w której chcesz zapisać plik vsconfig, wybierz pozycję **Przejrzyj szczegóły**.

   ![Eksportowanie konfiguracji z instalatora programu Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Upewnij się, że masz żądane obciążenia i składniki, a następnie wybierz pozycję **Eksportuj**.

## <a name="import-a-configuration"></a>Importowanie konfiguracji

Gdy wszystko będzie gotowe do zaimportowania pliku konfiguracji instalacji, wykonaj następujące kroki.

1. Otwórz Instalatora programu Visual Studio.

1. Na karcie produktu wybierz przycisk **Więcej,** a następnie wybierz pozycję **Importuj konfigurację**.

1. Znajdź plik vsconfig, który chcesz zaimportować, a następnie wybierz pozycję **Przejrzyj szczegóły**.

1. Upewnij się, że masz żądane obciążenia i składniki, a następnie wybierz pozycję **Zamknij**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automatyczne instalowanie brakujących składników

**Nowość w programie Visual Studio 2019**: Po zapisaniu pliku vsconfig w katalogu głównym rozwiązania, a następnie otwarciu rozwiązania program Visual Studio automatycznie wykrywa brak składników i monituje o ich zainstalowanie.

![Eksplorator rozwiązań sugeruje dodatkowe składniki](../install/media/vs-2019/solution-explorer-config-file.png)

Można również wygenerować plik vsconfig bezpośrednio z Eksploratora rozwiązań.

1. Kliknij prawym przyciskiem myszy plik rozwiązania.

1. Wybierz **pozycję Dodaj** > **plik konfiguracji instalacji**.

1. Potwierdź lokalizację, w której chcesz zapisać plik vsconfig, a następnie wybierz pozycję **Przejrzyj szczegóły**.

1. Upewnij się, że masz żądane obciążenia i składniki, a następnie wybierz pozycję **Eksportuj**.

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz Konfigurowanie programu Visual Studio w całej organizacji z wpisem w blogu [.vsconfig.](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej programu Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie instalacji programu Visual Studio opartej na sieci](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ustawianie ustawień domyślnych dla wdrożeń przedsiębiorstw](set-defaults-for-enterprise-deployments.md)
