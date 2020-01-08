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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce87385314ec84c7c0ed9d30c806a6287bb91d9e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591336"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybierasz podczas pierwszego otwierania programu Visual Studio&mdash;na przykład ogólne programowanie lub Wizualizacja C#. (Aby uzyskać informacje o zmienianiu lub resetowaniu ustawień, zobacz [Ustawienia środowiska](environment-settings.md)).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót **F2** wywołuje polecenie `Edit.EditCell`, jeśli używasz **projektanta ustawień** i wywołuje polecenie `File.Rename`, jeśli używasz **Team Explorer**.

Niezależnie od ustawień, dostosowania i kontekstu, zawsze możesz znaleźć i zmienić skrót klawiaturowy w **opcje** okno dialogowe. Możesz również wyszukać domyślne skróty klawiaturowe kilku dziesiątek poleceń w [popularnych skrótach klawiaturowych](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie ogólnych ustawień **deweloperskich** ), zobacz [wszystkie skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia w kontekście *globalnym* i nie ma innych kontekstów, ten skrót zawsze wywoła to polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ta strona jest oparta na profilu **ogólnych ustawień deweloperskich** .

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

2. Rozwiń **środowiska**, a następnie wybierz **klawiatury**.

3. Opcjonalnie: Filtrować listę poleceń, wprowadzając całość lub część nazwy polecenia, bez spacji w **Pokaż polecenia zawierające** pole.

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

   W **Użyj nowego skrótu** listy, wybierz obszar funkcji, w której chcesz użyć skrótu.

   Na przykład, można wybrać **Global** Jeśli chcesz, aby skrót działał we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

   > [!NOTE]
   > Nie można przypisać następujących kluczy jako części skrótu klawiaturowego w języku **globalnym**:
   >
   > - ENTER, TAB, Caps Lock
   > - Print Scrn/sys RQ, Scroll Lock, Pause/Break
   > - Wstaw, Strona główna, końcowa, Strona w górę, Strona w dół
   > - Klucz logo systemu Windows, klucz aplikacji, dowolny z klawiszy strzałek
   > - Num Lock, DELETE lub Clear na klawiaturze numerycznej
   > - Kombinacja klawiszy Ctrl + Alt + Delete

6. W **naciśnij klawisze skrótu** wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Można utworzyć skrót, który łączy literę z **Alt** klucza **Ctrl** lub oboma. Można również utworzyć skrót, który łączy **Shift** klucz i literę z **Alt** klucza **Ctrl** lub oboma.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się w **skrót aktualnie używany przez** pole. W takim przypadku wybierz **Backspace** klawisz, aby usunąć skrót, przed podjęciem próby innej.

    ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png)

7. Wybierz **przypisać** przycisku.

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, kliknij przycisk **Przypisz**, a następnie kliknij przycisk **Anuluj** , aby zamknąć okno dialogowe, przypisany skrót nie zostanie przywrócony.

## <a name="share-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia** > **Import i eksport ustawień**.

2. Wybierz opcję **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz przycisk **dalej**.

3. W obszarze **jakie ustawienia chcesz eksportować?** , wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

4. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **dalej**.

   ![Wyeksportować tylko skróty klawiaturowe niestandardowe](../ide/media/exportshortcuts.png)

5. W polu **jak chcesz nazwać plik ustawień** i **Zapisz plik My Settings w tym katalogu** pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz pozycję **Zakończ**.

::: moniker range="vs-2017"

Domyślnie skróty są zapisywane w pliku w *%USERPROFILE%\Documents\Visual Studio 2017\Settings* folderu. Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie nie *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Domyślnie skróty są zapisywane w pliku w folderze *%USERPROFILE%\Documents\Visual Studio 2019 \ Settings (ustawienia* ). Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie nie *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz **narzędzia** > **Import i eksport ustawień**.

2. Wybierz przycisk opcji **Importuj wybrane ustawienia środowiska** , a następnie wybierz **dalej**.

3. Wybierz przycisk opcji **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** , a następnie wybierz **dalej**.

4. W obszarze **Moje ustawienia**, wybierz plik zawierający skróty, które chcesz zaimportować, lub wybierz **Przeglądaj** przycisk, aby zlokalizować odpowiedni plik.

5. Wybierz **dalej**.

6. W obszarze **ustawienia, które chcesz zaimportować?** , wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

7. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **Zakończ**.

   ![Zaimportować tylko skróty klawiaturowe niestandardowe](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Zobacz także

- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
