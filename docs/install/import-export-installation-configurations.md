---
title: Importowanie lub eksportowanie konfiguracji instalacji
titleSuffix: ''
description: Dowiedz się, jak wyeksportować konfigurację instalacji do pliku vsconfig, aby udostępnić go innym osobom, oraz jak zaimportować go do sklonowania.
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 1fc4b181436b5e214300b334163b9257af0d0d35
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307469"
---
# <a name="import-or-export-installation-configurations"></a>Importowanie lub eksportowanie konfiguracji instalacji

Możesz skonfigurować Visual Studio w całej organizacji przy użyciu plików konfiguracji instalacji. Aby to zrobić, po prostu wyeksportuj informacje o obciążeniu i składniku do pliku vsconfig przy użyciu Visual Studio instalatora. Następnie możesz zaimportować konfigurację do nowych lub istniejących instalacji i udostępnić ją innym.

Oto jak to zrobić.

::: moniker range="vs-2017"

> [!NOTE]
> Ta funkcja jest dostępna tylko w Visual Studio 2017 w wersji 15.9 i nowszych.

::: moniker-end

## <a name="export-a-configuration"></a>Eksportowanie konfiguracji

Możesz wyeksportować plik konfiguracji instalacji z wcześniej zainstalowanego wystąpienia programu Visual Studio lub z aktualnie instalowanego wystąpienia.

1. Otwórz Instalator programu Visual Studio.

1. Na karcie produktu wybierz przycisk **Więcej,** a następnie wybierz pozycję **Eksportuj konfigurację**.

   ![Eksportowanie konfiguracji z karty produktu w instalatorze Visual Studio konfiguracji](../install/media/vs-2019/vs-installer-export-config.png)

1. Przejdź do lokalizacji, w której chcesz zapisać plik vsconfig, lub wpisz lokalizację, w której chcesz zapisać plik vsconfig, a następnie wybierz **pozycję Przejrzyj szczegóły.**

   ![Eksportowanie konfiguracji z Visual Studio instalatora](../install/media/vs-2019/export-configuration-confirmation.png)

1. Upewnij się, że masz obciążenia i składniki, których potrzebujesz, a następnie wybierz pozycję **Eksportuj.**

## <a name="import-a-configuration"></a>Importowanie konfiguracji

Gdy wszystko będzie gotowe do zaimportowania pliku konfiguracji instalacji, wykonaj następujące kroki.

1. Otwórz Instalator programu Visual Studio.

1. Na karcie produktu wybierz przycisk **Więcej,** a następnie wybierz pozycję **Importuj konfigurację**.

1. Znajdź plik vsconfig, który chcesz zaimportować, a następnie wybierz pozycję **Przejrzyj szczegóły.**

1. Upewnij się, że masz obciążenia i składniki, których potrzebujesz, a następnie wybierz pozycję **Zamknij.**

::: moniker range=">=vs-2019"

## <a name="automatically-install-missing-components"></a>Automatycznie instaluj brakujące składniki

**Nowość w programie Visual Studio 2019:** po zapisaniu pliku vsconfig w katalogu głównym rozwiązania, a następnie otwarciu rozwiązania program Visual Studio automatycznie wykryje brakujące składniki i wyświetli monit o ich zainstalowanie.

![Eksplorator rozwiązań sugeruje dodatkowe składniki](../install/media/vs-2019/solution-explorer-config-file.png)

Plik vsconfig można również wygenerować bezpośrednio z Eksplorator rozwiązań.

1. Kliknij prawym przyciskiem myszy plik rozwiązania.

1. Wybierz **pozycję Dodaj** plik konfiguracji > **instalacji.**

1. Potwierdź lokalizację, w której chcesz zapisać plik vsconfig, a następnie wybierz **pozycję Przejrzyj szczegóły.**

1. Upewnij się, że masz obciążenia i składniki, których potrzebujesz, a następnie wybierz pozycję **Eksportuj.**

::: moniker-end

> [!NOTE]
> Aby uzyskać więcej informacji, zobacz wpis [w blogu Configure Visual Studio across your organization with .vsconfig (Konfigurowanie](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) aplikacji w całej organizacji za pomocą pliku VSCONFIG).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Tworzenie instalacji sieciowej Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizowanie sieciowej instalacji Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Sterowanie aktualizacjami na potrzeby wdrożeń programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Ustawianie wartości domyślnych dla wdrożeń przedsiębiorstwa](set-defaults-for-enterprise-deployments.md)
