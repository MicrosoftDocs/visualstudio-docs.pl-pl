---
title: Tworzenie projektu AI z istniejącego kodu
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 8c0909259291bc5d2db2c4a9c8b87b1a0321d362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371719"
---
# <a name="create-an-ai-project-from-existing-code"></a>Tworzenie projektu AI z istniejącego kodu

Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo przenieść istniejący kod języka Python do projektu programu Visual Studio.

> [!Important]
> Opisany tutaj proces nie przenosi ani nie kopiuje oryginalnych plików źródłowych. Jeśli chcesz korzystać z kopii, najpierw należy zduplikować folder.

1. Uruchom program Visual Studio i wybierz pozycję **plik > nowym > projekcie**.

2. W oknie dialogowym **Nowy projekt** Wyszukaj ciąg "**narzędzia AI**", wybierz szablon "**z istniejącego kodu Python**", Nadaj projektowi nazwę i lokalizację, a następnie wybierz przycisk **OK**.

   ![Nowy projekt z istniejącego kodu, krok 1](media/create-project-existing/new-ai-project.png)

3. W wyświetlonym Kreatorze Ustaw ścieżkę do istniejącego kodu, Ustaw filtr dla typów plików i określ wszystkie ścieżki wyszukiwania wymagane przez projekt, a następnie wybierz przycisk **OK**. Jeśli nie wiesz, jakie ścieżki wyszukiwania są, pozostaw to pole puste.

   ![Nowy projekt z istniejącego kodu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Jeśli istniejący kod jest częścią projektu Azure Machine Learning, sprawdź **folder is Azure Machine Learning** , aby upewnić się, że zakończono pomyślnie konwersję ważnych Azure Machine Learning szczegółów konfiguracji, takich jak konto eksperymentowania, obszar roboczy, w którym konteksty obliczeniowe mają być używane i nie tylko.

4. Aby ustawić plik startowy, zlokalizuj plik w **Eksplorator rozwiązań**, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Ustaw jako plik startowy**.

5. Uruchom program, naciskając klawisz **Ctrl** + **F5** lub wybierając pozycję **Debuguj > Rozpocznij bez debugowania**.

> [!div class="nextstepaction"]
> [Samouczek: Praca z językiem Python w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Zobacz też

- [Ręcznie Zidentyfikuj istniejące środowisko języka Python](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
