---
title: Klonowanie repozytorium
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 73f1595e0e6c8f182f0bedcece51011390964ed2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62539661"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonowanie repozytorium kodu języka Python w programie Visual Studio

Po [zainstalowaniu programu Visual Studio Tools for AI](installation.md)można łatwo sklonować repozytorium kodu języka Python i utworzyć z niego projekt.

1. Aby połączyć się z repozytoriami GitHub, uruchom instalator programu Visual Studio, wybierz pozycję **Modyfikuj**i wybierz kartę **Poszczególne składniki.** Przewiń w dół do sekcji **Narzędzia kodu,** wybierz **rozszerzenie GitHub dla programu Visual Studio**i wybierz pozycję **Modyfikuj**.

    ![Wybieranie rozszerzenia GitHub w instalatorze programu Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Uruchom program Visual Studio.

3. Wybierz **opcję Wyświetl > Eksploratorze zespołu,** aby otworzyć okno **Eksploratora zespołu,** w którym można połączyć się z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno Eksploratora zespołu przedstawiające usługi Azure DevOps, GitHub i klonowanie repozytorium](media/create-project-repo/team-explorer-devops.png)

4. W polu URL w **obszarze Lokalne repozytoria Git**wprowadź , `https://github.com/Microsoft/samples-for-ai`wprowadź folder sklonowanych plików i wybierz opcję **Klonuj**.

    > [!Tip]
    > Folder określony w Eksploratorze zespołu jest specyficznym folderem do odbierania sklonowanych plików. W `git clone` przeciwieństwie do polecenia, utworzenie klona w Eksploratorze zespołu nie powoduje automatycznego utworzenia podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij dwukrotnie folder repozytorium u dołu Eksploratora zespołu, aby przejść do pulpitu nawigacyjnego repozytorium. W obszarze **Rozwiązania**wybierz pozycję **Nowy**.

    ![Okno eksploratora zespołu, tworzenie nowego projektu z klonu](media/create-project-repo/team-explorer-new-project.png)

6. W wyświetlonym oknie dialogowym **Nowy projekt** wybierz opcję **"Z istniejącego kodu języka Python**" określ nazwę projektu, ustaw **lokalizację** na ten sam folder co repozytorium i wybierz **przycisk OK**. W wyświetlonym kreatorze wybierz pozycję **Zakończ**.

7. Z menu **wybierz polecenie Wyświetl > Eksploratora rozwiązań.**

8. W Eksploratorze `TensorFlow Examples> MNIST` rozwiązań rozwiń węzeł, kliknij prawym przyciskiem myszy `convolutional.py`i wybierz polecenie Ustaw jako plik **startowy**. Ten krok informuje visual studio, który plik należy użyć podczas uruchamiania projektu.

9. Naciśnij **klawisz Ctrl**+**F5** lub wybierz **opcję Debugowanie > rozpocznij bez debugowania,** aby uruchomić program. Jeśli zostanie wyświetlony błąd, sprawdź ponownie ustawienie katalogu roboczego w poprzednim kroku.

10. Po pomyślnym uruchomieniu programu zostanie wyświetlony komunikat rozpoczęcie pobierania zestawu danych szkoleniowych i testowych, a następnie szkolenie modelu i wysunienie poziomu błędu. Chcesz, aby poziom błędu zmniejszał się wraz z czasem

    ![Pierwsze dane wyjściowe z programu Python MNIST](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Jeśli używasz Anakondy i pojawia się błąd dotyczący braku numpy, może być [konieczna zmiana środowiska Pythona, aby użyć Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Można wizualizować postęp z TensorBoard. Kliknij prawym przyciskiem myszy projekt i kliknij polecenie **Uruchom tensorboard,** a następnie wybierz katalog wyjściowych dzienników TensorBoard.

   ![uruchamianie tablicy tensorboard](media/create-project-repo/run-tensorboard.png)

12. Zwróć uwagę na zmniejszenie błędu w nadgodzinach, co oznacza, że jakość się poprawia.

   ![uruchamianie tablicy tensorboard](media/create-project-repo/tensorboard.png)
