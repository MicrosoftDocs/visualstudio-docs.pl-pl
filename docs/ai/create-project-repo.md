---
title: Klonowanie repozytorium
description: Dowiedz się, jak używać Visual Studio Tools for AI do klonowania repozytorium kodu w języku Python i tworzenia projektu z niego.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 303c410bf519561844d95cc13fa036534ddb2aa7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726621"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Klonowanie repozytorium kodu w języku Python w programie Visual Studio

Po [zainstalowaniu Visual Studio Tools for AI](installation.md)można łatwo sklonować repozytorium kodu w języku Python i utworzyć projekt z niego.

1. Aby nawiązać połączenie z repozytoriami usługi GitHub, uruchom Instalatora programu Visual Studio, wybierz pozycję **Modyfikuj** i wybierz kartę **poszczególne składniki** . Przewiń w dół do sekcji **Narzędzia kodu** , wybierz pozycję **rozszerzenie GitHub dla programu Visual Studio**, a następnie wybierz pozycję **Modyfikuj**.

    ![Wybieranie rozszerzenia GitHub w Instalatorze programu Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Uruchom program Visual Studio.

3. Wybierz pozycję **wyświetl > Team Explorer** , aby otworzyć okno **Team Explorer** , w którym można nawiązać połączenie z usługą GitHub lub Azure DevOps lub sklonować repozytorium.

    ![Okno programu Team Explorer pokazujące platformę Azure DevOps, GitHub i klonowanie repozytorium](media/create-project-repo/team-explorer-devops.png)

4. W polu adres URL w obszarze **lokalne repozytoria Git** wprowadź `https://github.com/Microsoft/samples-for-ai` , wprowadź folder dla sklonowanych plików, a następnie wybierz pozycję **Klonuj**.

    > [!Tip]
    > Folder określony w Team Explorer jest folderem, w którym mają zostać odebrane sklonowane pliki. W przeciwieństwie do `git clone` polecenia, utworzenie klonu w Team Explorer nie tworzy automatycznie podfolderu o nazwie repozytorium.

5. Po zakończeniu klonowania kliknij dwukrotnie folder repozytorium w dolnej części Team Explorer, aby przejść do pulpitu nawigacyjnego repozytorium. W obszarze **rozwiązania** wybierz pozycję **Nowy**.

    ![Okno Team Explorer, tworzenie nowego projektu na podstawie klonu](media/create-project-repo/team-explorer-new-project.png)

6. W wyświetlonym oknie dialogowym **Nowy projekt** wybierz pozycję "**z istniejącego kodu w języku Python**", określ nazwę projektu, ustaw **lokalizację** na ten sam folder, w którym znajduje się repozytorium, a następnie wybierz **przycisk OK**. W wyświetlonym kreatorze wybierz pozycję **Zakończ**.

7. Wybierz pozycję **wyświetl > Eksplorator rozwiązań** z menu.

8. W Eksplorator rozwiązań rozwiń `TensorFlow Examples> MNIST` węzeł, kliknij prawym przyciskiem myszy `convolutional.py` , a następnie wybierz polecenie **Ustaw jako plik startowy**. Ten krok informuje program Visual Studio, który plik powinien być używany podczas uruchamiania projektu.

9. Naciśnij klawisz **Ctrl** + **F5** lub wybierz opcję **Debuguj > Uruchom bez debugowania** , aby uruchomić program. Jeśli zobaczysz błąd, ponownie sprawdź ustawienia katalogu roboczego w poprzednim kroku.

10. Po pomyślnym uruchomieniu programu zobaczysz, że rozpocznie się pobieranie zestawu danych szkoleniowych i testowych, a następnie nauczenie modelu i wyjście z szybkością błędów. Współczynnik błędów, który ma zostać zmniejszony w czasie

    ![Pierwsze wyjście z programu python MNIST ręcznie](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Jeśli używasz programu Anaconda i wystąpi błąd dotyczący brakujących numpy, może zajść potrzeba [zmiany środowiska języka Python w celu użycia Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. Postęp można wizualizować za pomocą TensorBoard. Kliknij prawym przyciskiem myszy projekt, a następnie kliknij polecenie **Uruchom TensorBoard** , a następnie wybierz katalog wyjściowych dzienników TensorBoard.

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań programu Visual Studio z wybranym projektem MNIST ręcznie i opcją Run TensorBoard wybraną w menu kontekstowym.](media/create-project-repo/run-tensorboard.png)

12. Zwróć uwagę na błąd zmniejszający pracę w nadgodzinach, co oznacza, że jakość jest ulepszana.

   ![Zrzut ekranu przedstawiający główne okno TensorBoard z czterema wykresami, które wizualizują dane z dzienników TensorBoard.](media/create-project-repo/tensorboard.png)
