---
title: Ustawianie wielu projektów startowych
description: W tym artykule opisano sposób ustawiania uruchamiania lub debugowania wielu projektów.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 1b015d9009dc813c50ef891a4a523ba497c254c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950550"
---
# <a name="set-multiple-startup-projects"></a>Ustawianie wielu projektów startowych

Visual Studio dla komputerów Mac pozwala określić, że więcej niż jeden projekt ma być uruchamiany podczas debugowania lub uruchamiania rozwiązania.

## <a name="to-set-multiple-startup-projects"></a>Aby ustawić wiele projektów startowych

1. W okienko rozwiązania wybierz rozwiązanie (górny węzeł).

2. Kliknij prawym przyciskiem myszy węzeł rozwiązanie, a następnie wybierz pozycję **Ustaw projekty startowe**:

   ![Wybierz pozycję Ustaw projekty startowe](media/startup-proj-ctx-menu.png)

3. Zostanie otwarte okno dialogowe **Tworzenie konfiguracji przebiegu rozwiązania** . To okno dialogowe pozwala utworzyć nową nazwę uruchomieniową rozwiązania dla danego rozwiązania. Możesz użyć dowolnej nazwy. Nazwa domyślna to `Multiple Projects` .

   ![Okno dialogowe Tworzenie konfiguracji przebiegu rozwiązania](media/create-sln-run-config.png)

4. Wybierz pozycję **Utwórz konfigurację przebiegu**. Zostanie otwarte okno dialogowe **Opcje rozwiązania** z wybraną nową konfiguracją przebiegu rozwiązania:

   ![Opcje rozwiązania — okno dialogowe](media/sln-options-run-config-multi-projects.png)

5. Wybierz projekty, które chcesz uruchomić podczas debugowania lub uruchamiania aplikacji z Visual Studio dla komputerów Mac:

   ![Okno dialogowe Opcje rozwiązania z wybranymi projektami](media/sln-options-run-config-multi-projects-configured.png)

6. Wybierz pozycję **OK**. Nowa konfiguracja przebiegu rozwiązania jest ustawiona jako aktywna Konfiguracja przebiegu:

   ![Rozwiązanie z wieloma projektami skonfigurowanymi do uruchamiania podczas debugowania lub uruchamiania](media/startup-project-configured.png)

   Można zobaczyć, że dwa projekty są skonfigurowane do uruchamiania, ponieważ oba projekty są **pogrubione** w okienko rozwiązania. Na pasku narzędzi Nowa konfiguracja przebiegu jest ustawiana jako Bieżąca konfiguracja przebiegu rozwiązania.

## <a name="next-steps"></a>Następne kroki

- [Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac](compiling-and-building.md)
- [Ogólne informacje o konfiguracjach kompilacji](configurations.md)
