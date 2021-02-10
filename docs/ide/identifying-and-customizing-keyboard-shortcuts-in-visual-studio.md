---
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 84d78a86c64cd85ea8738ec9038c5e64642ca950
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935953"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybierasz podczas pierwszego otwierania programu Visual Studio &mdash; , na przykład ogólne programowanie lub Visual C#. (Aby uzyskać informacje o zmienianiu lub resetowaniu ustawień, zobacz [Ustawienia środowiska](environment-settings.md)).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót **F2** wywołuje `Edit.EditCell` polecenie, jeśli używasz **projektanta ustawień** i wywołuje `File.Rename` polecenie, jeśli używasz **Team Explorer**.

Niezależnie od ustawień, dostosowania i kontekstu, można zawsze znaleźć i zmienić skrót klawiaturowy w oknie dialogowym **Opcje** . Możesz również wyszukać domyślne skróty klawiaturowe kilku dziesiątek poleceń w [popularnych skrótach klawiaturowych](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie ogólnych ustawień **deweloperskich** ), zobacz [wszystkie skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia w kontekście *globalnym* i nie ma innych kontekstów, ten skrót zawsze wywoła to polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ta strona jest oparta na profilu **ogólnych ustawień deweloperskich** .

## <a name="identify-a-keyboard-shortcut"></a>Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz pozycję **Klawiatura**.

   ![Wyświetl skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png)

3. W polu **Pokaż polecenia zawierające** wpisz wszystko lub część nazwy polecenia bez spacji.

   Można na przykład znaleźć polecenia dla `solutionexplorer` .

4. Na liście, wybierz odpowiednie polecenie.

    Można na przykład wybrać opcję `View.SolutionExplorer` .

5. Jeśli polecenie ma skrót klawiaturowy, pojawia się w **skrótach dla wybranej listy poleceń** .

   ![Wyświetl skrót do określonego polecenia](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz pozycję **Klawiatura**.

3. Opcjonalne: Przefiltruj listę poleceń, wprowadzając wszystkie lub część nazwy polecenia, bez spacji, w polu **Pokaż polecenia zawierające** .

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

   Na liście **Użyj nowego skrótu w** wybierz obszar funkcji, w którym chcesz użyć skrótu.

   Na przykład, możesz wybrać **globalne** , jeśli chcesz, aby skrót działał we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

   > [!NOTE]
   > Nie można przypisać następujących kluczy jako części skrótu klawiaturowego w języku **globalnym**:
   >
   > - ENTER, TAB, Caps Lock
   > - Print Scrn/sys RQ, Scroll Lock, Pause/Break
   > - Wstaw, Strona główna, końcowa, Strona w górę, Strona w dół
   > - Klucz logo systemu Windows, klucz aplikacji, dowolny z klawiszy strzałek
   > - Num Lock, DELETE lub Clear na klawiaturze numerycznej
   > - Kombinacja klawiszy Ctrl + Alt + Delete

6. W polu **naciśnij klawisz skrótu** Wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Można utworzyć skrót, który łączy literę z klawiszem **Alt** , klawiszem **Ctrl** lub obu. Możesz również utworzyć skrót, który łączy klawisz **SHIFT** i literę z klawiszem **Alt** , klawiszem **Ctrl** lub obu.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się w polu **skrót aktualnie używany przez** . W takim przypadku wybierz klawisz **Backspace** , aby usunąć ten skrót przed podjęciem próby innej.

    ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png)

7. Wybierz przycisk **Przypisz** .

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, kliknij przycisk **Przypisz**, a następnie kliknij przycisk **Anuluj** , aby zamknąć okno dialogowe, przypisany skrót nie zostanie przywrócony.

## <a name="share-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Importuj i Eksportuj ustawienia**.

2. Wybierz opcję **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz przycisk **dalej**.

3. W obszarze **jakie ustawienia chcesz eksportować?** wyczyść pole wyboru **wszystkie ustawienia** , rozwiń **Opcje**, a następnie rozwiń **środowisko**.

4. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **dalej**.

   ![Eksportuj tylko dostosowane skróty klawiaturowe](../ide/media/exportshortcuts.png)

5. W polu **jak chcesz nazwać plik ustawień** i **Zapisz plik My Settings w tym katalogu** pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz pozycję **Zakończ**.

::: moniker range="vs-2017"

Domyślnie skróty są zapisywane w pliku w folderze *%USERPROFILE%\Documents\Visual Studio 2017 \ Settings (ustawienia* ). Nazwa pliku odzwierciedla datę wyeksportowania ustawień, a rozszerzenie to *. vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Domyślnie skróty są zapisywane w pliku w folderze *%USERPROFILE%\Documents\Visual Studio 2019 \ Settings (ustawienia* ). Nazwa pliku odzwierciedla datę wyeksportowania ustawień, a rozszerzenie to *. vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **Importuj i Eksportuj ustawienia**.

2. Wybierz przycisk opcji **Importuj wybrane ustawienia środowiska** , a następnie wybierz **dalej**.

3. Wybierz przycisk opcji **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** , a następnie wybierz **dalej**.

4. W obszarze **Moje ustawienia** wybierz plik zawierający skróty, które chcesz zaimportować, lub kliknij przycisk **Przeglądaj** , aby zlokalizować właściwy plik.

5. Wybierz pozycję **Next** (Dalej).

6. W obszarze **jakie ustawienia chcesz zaimportować?** wyczyść pole wyboru **wszystkie ustawienia** , rozwiń **Opcje**, a następnie rozwiń **środowisko**.

7. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **Zakończ**.

   ![Importuj tylko dostosowane skróty klawiaturowe](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Zobacz też

- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
