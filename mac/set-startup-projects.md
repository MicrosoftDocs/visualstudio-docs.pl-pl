---
title: Ustawianie wielu projektów startowych w programie Visual Studio dla komputerów Mac
description: W tym artykule opisano ustawianie wielu projektów, można uruchomić na debugowania lub wykonywania.
author: sayedihashimi
ms.author: sayedha
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: a4a4f2f4fd4ce6cd88d11979a21e4e9184adfca8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937163"
---
# <a name="how-to-set-multiple-startup-projects"></a>Instrukcje: Ustawianie wielu projektów startowych

Program Visual Studio for Mac umożliwia określenie sposobu więcej niż jeden projekt jest uruchomiona podczas debugowania i uruchamiania rozwiązania.

## <a name="to-set-multiple-startup-projects"></a>Aby ustawić wiele projektów startowych

1. W **konsoli rozwiązania**, wybierz rozwiązanie (najwyższy węzeł).

2. Wybierz menu kontekstowe (kliknij prawym przyciskiem myszy) węzła rozwiązania, a następnie wybierz **Ustaw projekty startowe...** .

   ![Menu kontekstowe projektów uruchamiania zestawu](media/startup-proj-ctx-menu.png)

3. **Tworzenie konfiguracji uruchomienia rozwiązania** zostanie wyświetlone okno dialogowe. To okno dialogowe utworzy nową nazwanego rozwiązania Uruchom konfigurację dla Twojego rozwiązania. Można nadać dowolną nazwę możesz na przykład, domyślna nazwa to `Multiple Projects`.

   ![Tworzenie okna dialogowego konfiguracji uruchamiania rozwiązania](media/create-sln-run-config.png)

4. Kliknij przycisk **Tworzenie konfiguracji przebiegu**. **Opcje rozwiązania** zostanie otwarte okno dialogowe z nowego rozwiązania uruchomienia wybranej konfiguracji.

   ![Okno dialogowe Opcje rozwiązania](media/sln-options-run-config-multi-projects.png)

5. Wybierz projekty, które ma być uruchamiany podczas debugowania i uruchamiania aplikacji w programie Visual Studio dla komputerów Mac.

   ![Okno dialogowe Opcje rozwiązania przy użyciu skonfigurowanego konfiguracji uruchamiania](media/sln-options-run-config-multi-projects-configured.png)

6. Kliknij przycisk **OK**. Okno dialogowe zostanie odrzucony, a nowa konfiguracja rozwiązania uruchamiania jest ustawiony jako aktywnej konfiguracji przebiegu.

   ![Rozwiązanie z wieloma projektami skonfigurowany do debugowania uruchamiane lub](media/startup-project-configured.png) widać, że dwa projekty są skonfigurowane do uruchamiania, ponieważ oba projekty znajdują się w **bold** w **konsoli rozwiązania**. Na pasku narzędzi nowej konfiguracji uruchomieniowej jest skonfigurowany jako bieżącą konfigurację uruchamiania rozwiązania.

## <a name="next-steps"></a>Następne kroki

- [Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac](compiling-and-building.md)
- [Ogólne informacje o konfiguracjach kompilacji](configurations.md)