---
title: Ustawianie wielu projektów startowych
description: W tym artykule opisano sposób ustawiania wielu projektów do uruchomienia lub debugowania.
author: sayedihashimi
ms.author: sayedha
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: visual-studio-mac
ms.assetid: fd354fff-ce6b-4505-a815-84a2311e39ba
ms.openlocfilehash: 46e6447e07d2ee8439fcd86f5d1519beaa1e4609
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75406696"
---
# <a name="set-multiple-startup-projects"></a>Ustawianie wielu projektów startowych

Visual Studio dla komputerów Mac umożliwia określenie, że więcej niż jeden projekt powinien zostać uruchomiony podczas debugowania lub uruchamiania rozwiązania.

## <a name="to-set-multiple-startup-projects"></a>Aby ustawić wiele projektów startowych

1. W panelu rozwiązania wybierz rozwiązanie (węzeł górny).

2. Kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie wybierz polecenie **Ustaw projekty uruchamiania:**

   ![Wybierz pozycję Ustaw projekty uruchamiania](media/startup-proj-ctx-menu.png)

3. Zostanie otwarte okno dialogowe **Tworzenie konfiguracji uruchamiania rozwiązania.** To okno dialogowe umożliwia utworzenie nowej konfiguracji uruchamiania rozwiązania o nazwie Dla rozwiązania. Możesz użyć dowolnej nazwy, którą chcesz. Domyślna nazwa `Multiple Projects`to .

   ![Okno dialogowe Tworzenie konfiguracji uruchamiania rozwiązania](media/create-sln-run-config.png)

4. Wybierz **pozycję Utwórz konfigurację uruchamiania**. Zostanie otwarte okno dialogowe **Opcje rozwiązania** z wybraną nową konfiguracją uruchamiania rozwiązania:

   ![Okno dialogowe Opcje rozwiązania](media/sln-options-run-config-multi-projects.png)

5. Wybierz projekty, które chcesz uruchomić podczas debugowania lub uruchamiania aplikacji z programu Visual Studio dla komputerów Mac:

   ![Okno dialogowe Opcje rozwiązania z wybranymi projektami](media/sln-options-run-config-multi-projects-configured.png)

6. Kliknij przycisk **OK**. Nowa konfiguracja uruchamiania rozwiązania jest ustawiona jako konfiguracja aktywnego uruchamiania:

   ![Rozwiązanie z wieloma projektami skonfigurowanymi do uruchamiania w debugowaniu lub uruchamianiu](media/startup-project-configured.png)

   Widać, że dwa projekty są skonfigurowane do uruchamiania, ponieważ oba projekty są **pogrubione** w panelu rozwiązania. Na pasku narzędzi nowa konfiguracja uruchamiania jest ustawiana jako bieżąca konfiguracja uruchamiania rozwiązania.

## <a name="next-steps"></a>Następne kroki

- [Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac](compiling-and-building.md)
- [Opis konfiguracji kompilacji](configurations.md)
