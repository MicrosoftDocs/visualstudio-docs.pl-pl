---
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a54f18e6e69fd71f1d46205903728a909c668383
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935722"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybrano podczas pierwszego uruchomienia programu Visual Studio (na przykład ogólne ustawienia projektowania lub Visual C#).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład **F2** skrót wywołuje `Edit.EditCell` polecenia, jeśli używasz **Projektant ustawień** i `File.Rename` polecenia, jeśli używasz **Team Explorer**.

Niezależnie od ustawień, dostosowania i kontekstu, zawsze możesz znaleźć i zmienić skrót klawiaturowy w **opcje** okno dialogowe. Możesz również wyszukać domyślne skróty klawiaturowe dla kilkudziesięciu poleceń w [domyślne skróty klawiaturowe dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), możesz znaleźć, aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie **ogólne Ustawienia środowiska deweloperskiego**) w [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia wyłącznie w kontekście globalnym, ten skrót zawsze będzie wywoływał dane polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ten temat opiera się na **ogólnych ustawieniach projektowych**.

## <a name="identify-a-keyboard-shortcut"></a>Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. Rozwiń **środowiska**, a następnie wybierz **klawiatury**.

   ![Wyświetlić skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png)

3. W **Pokaż polecenia zawierające** wpisz całość lub część nazwy polecenia bez spacji.

   Na przykład można znaleźć polecenia dla `solutionexplorer`.

4. Na liście, wybierz odpowiednie polecenie.

    Na przykład, można wybrać `View.SolutionExplorer`.

5. Jeśli polecenie ma skrót klawiaturowy, pojawia się w **skróty dla wybranego polecenia** listy.

   ![Wyświetl skrót dla określonego polecenia](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. Rozwiń **środowiska** folder, a następnie wybierz **klawiatury**.

3. Opcjonalne: Filtruj listę poleceń, wprowadzając całość lub część nazwy polecenia, bez spacji w **Pokaż polecenia zawierające** pole.

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

    W **Użyj nowego skrótu** listy, wybierz obszar funkcji, w której chcesz użyć skrótu.

    Na przykład, można wybrać **Global** Jeśli chcesz, aby skrót działał we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

    > [!NOTE]
    > Nie można przypisać następujących klawiszy jako części skrótów klawiaturowych w **Global**: Drukuj podręcznego/Sys Rq, Scroll Lock, Pause/Break, kartę, włączony klawisz Caps Lock, Insert, Home, End, Page Up, Page Down, klawiszy logo Windows, klucz aplikacji, za pomocą klawiszy strzałek lub Enter; Num Lock, Delete lub Clear na klawiaturze numerycznej; Kombinacja klawiszy Ctrl + Alt + Delete.

6. W **naciśnij klawisze skrótu** wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Można utworzyć skrót, który łączy literę z **Alt** klucza **Ctrl** lub oboma. Można również utworzyć skrót, który łączy **Shift** klucz i literę z **Alt** klucza **Ctrl** lub oboma.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się w **skrót aktualnie używany przez** pole. W takim przypadku wybierz **Backspace** klawisz, aby usunąć skrót, przed podjęciem próby innej.

    ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png)

7. Wybierz **przypisać** przycisku.

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, wybierz **przypisać** przycisk, a następnie wybierz **anulować** przycisku, okno dialogowe zostanie zamknięte, ale zmiany nie zostanie wycofana.

## <a name="share-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia** > **Import i eksport ustawień**.

2. Wybierz **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz **dalej** przycisku.

3. W obszarze **jakie ustawienia chcesz eksportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

4. Wybierz **klawiatury** pole wyboru, a następnie wybierz **dalej** przycisku.

    ![Wyeksportować tylko skróty klawiaturowe niestandardowe](../ide/media/exportshortcuts.png)

5. W **co chcesz nazwać plik swoich ustawień?** i **Store plik moich ustawień w tym katalogu** pola, albo pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz  **Zakończ** przycisku.

    Domyślnie skróty są zapisywane w pliku w *%USERPROFILE%\Documents\Visual Studio 2017\Settings* folderu. Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie nie *.vssettings*.

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia** > **Import i eksport ustawień**.

2. Wybierz **Importuj ustawienia wybranego środowiska** przycisk opcji, a następnie wybierz **dalej** przycisku.

3. Wybierz **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** przycisk opcji, a następnie wybierz **dalej** przycisku.

4. W obszarze **Moje ustawienia**, wybierz plik zawierający skróty, które chcesz zaimportować, lub wybierz **Przeglądaj** przycisk, aby zlokalizować odpowiedni plik.

5. Wybierz **dalej** przycisku.

6.  W obszarze **ustawienia, które chcesz zaimportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

7. Wybierz **klawiatury** pole wyboru, a następnie wybierz **Zakończ** przycisku.

    ![Zaimportować tylko skróty klawiaturowe niestandardowe](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)