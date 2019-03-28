---
title: EditorConfig
description: Przy użyciu pliku editorconfig umożliwia spójne projektu kodowania stylów w programie Visual Studio dla komputerów Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: d42103d17b64ee9b3fb2a0660017824490655808
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58572998"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Tworzenie i edytowanie niestandardowego pliku EditorConfig

W programie Visual Studio dla komputerów Mac, można dodać [EditorConfig](http://editorconfig.org/) plik do projektu lub rozwiązania, aby wymusić spójnej kodowania style dla wszystkich użytkowników, który działa w bazie kodu. Ustawienia zadeklarowany w pliku EditorConfig pierwszeństwo globalnego programu Visual Studio dla ustawienia edytora tekstu Mac. Za pomocą polecenia EditorConfig w obrębie projektu lub plik codebase pozwala ustawić swój kodowania styl, preferencji i ostrzeżenia dla Twojego projektu. Ponieważ plik jest częścią bazy kodu, ułatwia dla wszystkich użytkowników, aby stosować się do praktyk kodowania projektu, niezależnie od tego, środowiska IDE albo edytora kodu, które używają.

[Polecenie EditorConfig](http://editorconfig.org/) pliki są obsługiwane na wiele edytorów IDE i kodu, łącznie z programu Visual Studio 2017.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor programu Visual Studio dla komputerów Mac obsługuje podstawowy zestaw [właściwości EditorConfig](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

Obsługuje również EditorConfig [konwencje kodowania](/visualstudio/ide/editorconfig-code-style-settings-reference) w języku C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Dodanie nowego pliku EditorConfig

1. Otwórz projekt w programie Visual Studio dla komputerów Mac. Wybierz węzeł rozwiązania lub projektu, który chcesz dodać plik wtyczki EditorConfig. Dodawanie pliku do katalogu rozwiązania stosuje ustawienia pliku .editorconfig dla wszystkich projektów w rozwiązaniu.

2. Kliknij prawym przyciskiem myszy węzeł i wybierz pozycję **Dodaj > Nowy plik** otworzyć **nowy plik** okno dialogowe:

    ![Elementy menu zawartości](media/editorconfig-image0.png)

3. Wybierz **różne > pusty plik tekstowy** i nadaj mu **nazwa** `.editorconfig`. Naciśnij klawisz **New** utworzyć plik i otworzyć go w edytorze:

    ![Okno dialogowe Nowy plik](media/editorconfig-image1.png)

    Dodawanie elementu na poziomie rozwiązania automatycznie tworzy i zagnieżdżony w **elementy rozwiązania** folderu:

    ![Element rozwiązania wyświetlane w konsoli rozwiązania](media/editorconfig-image1a.png)

4. Edytuj plik. Na przykład:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Ustawienia z `.editorconfig` pliku będzie dotyczyć nowy kod, który można zapisać, ale istniejący kod może być konieczne można ponownie sformatowane, aby były zgodne z nowymi ustawieniami. Aby zastosować ustawienia z `.editorconfig` pliku do istniejącego pliku źródłowego, otwórz plik i wybierz **Edytuj > Format > Formatuj dokument** na pasku menu::

    ![Formatuj element menu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Dodawanie istniejącego pliku EditorConfig

Jeśli pracujesz z projekt lub rozwiązanie już zawiera `.editorconfig` plików, nie widać niczego, co należy zrobić, aby zastosować ustawienia. Wszelkie nowe wiersze kodu są sformatowane zgodnie z ustawieniami EditorConfig.

Może zajść potrzeba ponownego użycia istniejącej `.editorconfig` plik w projekcie. Aby dodać istniejący plik, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy w folderze, o których chcesz dodać, a następnie wybierz pozycję **Dodaj > Dodaj pliki**.

2. Przejdź do katalogu wymaganego pliku.

3. Pliki zaczyna się od `.` (takie jak `.editorconfig`) są ukryte pliki w systemie macOS, więc naciśnij **Command + Shift +.** zapewnienie `.editorconfig` plików widoczne.

4. Wybierz `.editorconfig` plik i kliknij przycisk **Otwórz**:

    ![dodanie nowego okna pliku](media/editorconfig-image3b.png)

5. Gdy zostanie wyświetlone następujące okno dialogowe, wybierz pozycję **skopiuj plik do katalogu** opcji, a następnie wybierz pozycję **OK**:

    ![Dodaj plik do folderu okno dialogowe Opcje](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Odzwierciedlanie ustawień w pliku .editorconfig

Po dodaniu pliku EditorConfig bazie kodu nowy kod dodany automatycznie jest formatowana zgodnie z określonymi ustawieniami. Istniejący kod nie odzwierciedla ustawienia automatycznie, chyba że formatowania kodu.

Aby uwzględnić ustawienia z `.editorconfig` plików, wybierz węzeł rozwiązania i wybierz **Edytuj > Format > Formatuj dokument** na pasku menu:

![Formatuj dokument z paska menu](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Edytowanie pliku EditorConfig

Plików EditorConfig Użyj układ prosty plik, aby określić ustawienia, co zostało wyjaśnione poniżej z użyciem poprzedniego przykładu:

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Ustawienie `root` do `true` flagi ten plik jako plik najważniejsze bazy kodu i wyżej `.editorconfig` pliki projektu są ignorowane, jak wyjaśniono w [Zastąp ustawienia EditorConfig](#override-editorconfig-settings) sekcji.

Każda sekcja jest wskazywane przez kwadratowe (**[**) nawiasów i określa informacje na temat typów plików, następujące właściwości powinny odnoszą się do.

W powyższym przykładzie niektóre ustawienia są stosowane do wszystkich plików w projekcie, a inne są dodawane tylko do plików języka C#. Poniższe zrzuty ekranu Pokaż przed i po nim `.editorconfig` ustawienia zostały zastosowane:

**Przed**:

![Przed editorconfig ustawienia zostały zastosowane](media/editorconfig-image4.png)

**Po**:

![Po zastosowaniu ustawień wtyczki editorconfig](media/editorconfig-image5.png)

Aby uzyskać więcej informacji na temat dostępnych ustawień EditorConfig, zobacz [.NET coding convention ustawienia dla wtyczki EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) artykułu i [obsługiwanych właściwości](http://editorconfig.org/#supported-properties) sekcji w oficjalnej dokumentacji.

## <a name="override-editorconfig-settings"></a>Override EditorConfig Settings

Można mieć więcej niż jeden `.editorconfig` pliku w poszczególnych rozwiązaniach. Program Visual Studio for Mac odczyty `.editorconfig` plików od góry do dołu w rozwiązaniu, dodawania i zastępowanie ustawień, ponieważ przechodzi. Oznacza to, że ustawienia w `.editorconfig` _najbliższego_ pliku edycji będzie miało pierwszeństwo. Ustawienia są pobierane z `.editorconfig` pliku w tym samym folderze (jeśli istnieje), a następnie `.editorconfig` w folderze nadrzędnym (jeśli istnieje,) itd. do momentu znalezienia `root=true`.

Jeśli chcesz upewnić się, że _nie_ ustawienia z każdym wyższego poziomu `.editorconfig` pliki są stosowane do tej części bazy kodu, Dodaj `root=true` właściwości na początku niższego poziomu `.editorconfig` pliku:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowego edytora ustawień za pomocą wtyczki EditorConfig (Visual Studio Windows)](/visualstudio/ide/create-portable-custom-editor-options)