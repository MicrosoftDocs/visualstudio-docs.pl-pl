---
title: Ustawianie wielu projektów startowych
description: W tym artykule opisano sposób ustawiania uruchamiania lub debugowania wielu projektów.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.topic: how-to
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: df1e088a5e2d0f65d8b72dad0895f1edb1740f1f
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493572"
---
# <a name="set-multiple-startup-projects"></a>Ustawianie wielu projektów startowych

Visual Studio dla komputerów Mac pozwala określić, że więcej niż jeden projekt ma być uruchamiany podczas debugowania lub uruchamiania rozwiązania.

## <a name="to-set-multiple-startup-projects"></a>Aby ustawić wiele projektów startowych

1. W oknie rozwiązanie wybierz rozwiązanie (górny węzeł).

2. Kliknij prawym przyciskiem myszy węzeł rozwiązanie, a następnie wybierz pozycję **Ustaw projekty startowe** :

   ![Wybierz pozycję Ustaw projekty startowe](media/startup-proj-ctx-menu.png)

3. Zostanie otwarte okno dialogowe **Tworzenie konfiguracji przebiegu rozwiązania** . To okno dialogowe pozwala utworzyć nową nazwę uruchomieniową rozwiązania dla danego rozwiązania. Możesz użyć dowolnej nazwy. Nazwa domyślna to `Multiple Projects` .

   ![Okno dialogowe Tworzenie konfiguracji przebiegu rozwiązania](media/create-sln-run-config.png)

4. Wybierz pozycję **Utwórz konfigurację przebiegu**. Zostanie otwarte okno dialogowe **Opcje rozwiązania** z wybraną nową konfiguracją przebiegu rozwiązania:

   ![Opcje rozwiązania — okno dialogowe](media/sln-options-run-config-multi-projects.png)

5. Wybierz projekty, które chcesz uruchomić podczas debugowania lub uruchamiania aplikacji z Visual Studio dla komputerów Mac:

   ![Okno dialogowe Opcje rozwiązania z wybranymi projektami](media/sln-options-run-config-multi-projects-configured.png)

6. Wybierz przycisk **OK**. Nowa konfiguracja przebiegu rozwiązania jest ustawiona jako aktywna Konfiguracja przebiegu:

   ![Rozwiązanie z wieloma projektami skonfigurowanymi do uruchamiania podczas debugowania lub uruchamiania](media/startup-project-configured.png)

   Teraz dwa projekty są skonfigurowane do uruchamiania, które są reprezentowane przez oba projekty pojawiające się **pogrubione** w oknie rozwiązania. Na pasku narzędzi Nowa konfiguracja przebiegu jest ustawiana jako Bieżąca konfiguracja przebiegu rozwiązania.

## <a name="next-steps"></a>Następne kroki

- [Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac](compiling-and-building.md)
- [Ogólne informacje o konfiguracjach kompilacji](configurations.md)
