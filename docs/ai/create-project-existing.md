---
title: Tworzenie projektu AI na podstawie istniejącego kodu
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 416a3358f6fab1fa106f54a360fc156abc16c6dc
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638627"
---
# <a name="create-an-ai-project-from-existing-code"></a>Tworzenie projektu AI na podstawie istniejącego kodu

Po [zainstalowaniu programu Visual Studio Tools for AI](installation.md)można łatwo wprowadzić istniejący kod języka Python do projektu programu Visual Studio.

> [!Important]
> Proces opisany w tym miejscu nie przenosi ani nie kopiuje oryginalnych plików źródłowych. Jeśli chcesz pracować z kopią, najpierw zduplikuj folder.

1. Uruchom program Visual Studio i wybierz **pozycję Plik > nowy projekt >**.

2. W oknie dialogowym **Nowy projekt** wyszukaj szablon "**Narzędzia AI**", wybierz szablon "**Z istniejącego kodu Pythona**", nadaj projektowi nazwę i lokalizację, a następnie wybierz **przycisk OK**.

   ![Nowy projekt z istniejącego kodu, krok 1](media/create-project-existing/new-ai-project.png)

3. W wyświetlonym kreatorze ustaw ścieżkę do istniejącego kodu, ustaw filtr dla typów plików i określ wszystkie ścieżki wyszukiwania, których wymaga projekt, a następnie wybierz przycisk **OK**. Jeśli nie wiesz, jakie są ścieżki wyszukiwania, pozostaw to pole puste.

   ![Nowy projekt z istniejącego kodu, krok 2](media/create-project-existing/azurebatch-newproject.png)

   Jeśli istniejący kod jest częścią projektu usługi Azure Machine Learning, sprawdź **folder Jest usługa Azure Machine Learning,** aby zapewnić pomyślną konwersję ważnych szczegółów konfiguracji usługi Azure Machine Learning, takich jak konto eksperymentowanie, obszar roboczy, który oblicza konteksty do użycia i inne.

4. Aby ustawić plik startowy, znajdź plik w **Eksploratorze rozwiązań**, kliknij prawym przyciskiem myszy i wybierz polecenie **Ustaw jako plik startowy**.

5. Uruchom program, naciskając **klawisz Ctrl**+**F5** lub wybierając **debugowanie > start bez debugowania**.

> [!div class="nextstepaction"]
> [Samouczek: Praca z Pythonem w programie Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Zobacz też

- [Ręczne identyfikowanie istniejącego środowiska języka Python](../python/managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
