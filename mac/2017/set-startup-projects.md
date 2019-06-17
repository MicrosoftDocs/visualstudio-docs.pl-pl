---
title: Ustawianie wielu projektów startowych w programie Visual Studio dla komputerów Mac
description: W tym artykule opisano ustawianie wielu projektów, można uruchomić na debugowania lub wykonywania.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: c692cf8907fcd232b7ba442cea351664bc8dd407
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043598"
---
# <a name="set-multiple-startup-projects"></a>Ustawianie wielu projektów startowych

Program Visual Studio for Mac pozwala określić, że więcej niż jednego projektu powinna być uruchamiana podczas debugowania i uruchamiania rozwiązania.

## <a name="to-set-multiple-startup-projects"></a>Aby ustawić wiele projektów startowych

1. W konsoli rozwiązania należy wybrać rozwiązanie (najwyższy węzeł).

2. Kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie wybierz pozycję **Ustaw projekty startowe**:

   ![Wybrany zestaw projektów startowych](media/startup-proj-ctx-menu.png)

3. **Tworzenie konfiguracji uruchomienia rozwiązania** zostanie otwarte okno dialogowe. To okno dialogowe umożliwia tworzenie nowych nazwane Uruchom Konfiguracja rozwiązania dla Twojego rozwiązania. Można użyć dowolnej nazwy, którą chcesz. Nazwa domyślna to `Multiple Projects`.

   ![Tworzenie konfiguracji uruchomienia rozwiązania, okno dialogowe](media/create-sln-run-config.png)

4. Wybierz **Tworzenie konfiguracji przebiegu**. **Opcje rozwiązania** zostanie otwarte okno dialogowe z nowego rozwiązania uruchomienia wybranej konfiguracji:

   ![Okno dialogowe Opcje rozwiązania](media/sln-options-run-config-multi-projects.png)

5. Wybierz projekty, które ma być uruchamiany podczas debugowania i uruchamiania aplikacji w programie Visual Studio dla komputerów Mac:

   ![Okno dialogowe Opcje rozwiązania z wybranych projektów](media/sln-options-run-config-multi-projects-configured.png)

6. Kliknij przycisk **OK**. Nowa konfiguracja rozwiązania uruchamiania jest ustawiony jako aktywnej konfiguracji przebiegu:

   ![Rozwiązanie z wieloma projektami skonfigurowany tak, aby uruchomić debugowania lub nie działa](media/startup-project-configured.png)

   Widać, że dwa projekty są skonfigurowane do uruchamiania, ponieważ oba projekty są **bold** w konsoli rozwiązania. Na pasku narzędzi nowej konfiguracji uruchomieniowej jest ustawiona jako bieżąca konfiguracja Uruchom rozwiązanie.

## <a name="next-steps"></a>Następne kroki

- [Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac](compiling-and-building.md)
- [Ogólne informacje o konfiguracjach kompilacji](configurations.md)
