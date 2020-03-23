---
title: EditorConfig
description: Za pomocą pliku editorconfig, aby włączyć spójne style kodowania projektu w programie Visual Studio dla komputerów Mac.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 6f6241c114d636cc8cb01cf5c4bf9ba2b5106701
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "73716891"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Tworzenie i edytowanie niestandardowego pliku EditorConfig

W programie Visual Studio dla komputerów Mac można dodać [plik EditorConfig](https://editorconfig.org/) do projektu lub rozwiązania, aby wymusić spójne style kodowania dla wszystkich, którzy działają w bazie kodu. Ustawienia zadeklarowane w editorconfig pliku mają pierwszeństwo przed globalnym visual studio dla komputerów Mac ustawienia edytora tekstu. Za pomocą EditorConfig pliku w projekcie lub codebase pozwala ustawić styl kodowania, preferencje i ostrzeżenia dla projektu. Ponieważ plik jest częścią bazy kodu, ułatwia wszystkim użytkownikom stosować się do praktyk kodowania projektu, niezależnie od IDE lub edytora kodu, którego używają.

[EditorConfig](https://editorconfig.org/) pliki są obsługiwane na wiele identyfikatorów i edytorów kodu, w tym Visual Studio.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor w programie Visual Studio dla komputerów Mac obsługuje podstawowy zestaw [właściwości EditorConfig:](https://editorconfig.org/#supported-properties)

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig obsługuje również [konwencje kodowania](/visualstudio/ide/editorconfig-code-style-settings-reference) w języku C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Dodawanie nowego pliku EditorConfig

1. Otwórz projekt w programie Visual Studio dla komputerów Mac. Wybierz węzeł rozwiązania lub projektu, do którego chcesz dodać plik EditorConfig. Dodanie pliku do katalogu rozwiązania powoduje zastosowanie ustawień .editorconfig do wszystkich projektów w rozwiązaniu.

2. Kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **Dodaj > nowy plik,** aby otworzyć okno dialogowe **Nowy plik:**

    ![Elementy menu zawartości](media/editorconfig-image0.png)

3. Wybierz **opcję Różne > pusty plik tekstowy** i nadaj mu **nazwę** `.editorconfig`. Naciśnij **przycisk Nowy,** aby utworzyć plik i otworzyć go w edytorze:

    ![Okno dialogowe Nowy plik](media/editorconfig-image1.png)

    Dodanie elementu na poziomie rozwiązania automatycznie tworzy i zagnieżdża go w folderze **Elementy rozwiązania:**

    ![Element rozwiązania wyświetlany w podkładce rozrachycznej](media/editorconfig-image1a.png)

4. Edytuj plik. Przykład:

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

4. Ustawienia z `.editorconfig` pliku będą miały zastosowanie do każdego nowego kodu, który piszesz, ale istniejący kod może wymagać sformatowanego, aby był zgodny z nowymi ustawieniami. Aby zastosować ustawienia `.editorconfig` z pliku do istniejącego pliku źródłowego, otwórz plik i wybierz polecenie **Edytuj > Formatuj > Formatuj dokument** z paska menu::

    ![Element menu Format dokumentu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Dodawanie istniejącego pliku EditorConfig

Jeśli pracujesz z projektem lub rozwiązaniem, `.editorconfig` które już zawiera plik, nie ma nic, co musisz zrobić, aby zastosować ustawienia. Wszystkie nowe wiersze kodu są sformatowane zgodnie z ustawieniami EditorConfig.

Można ponownie użyć istniejącego `.editorconfig` pliku w projekcie. Aby dodać istniejący plik, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy folder, do którego chcesz go dodać, a następnie wybierz pozycję **Dodaj > Dodaj pliki**.

2. Przejdź do katalogu wymaganego pliku.

3. Pliki zaczynające `.` się `.editorconfig`od (np. ) są ukrytymi plikami w systemie macOS, więc naciśnij **command + shift + .** , aby `.editorconfig` plik był widoczny.

4. Zaznacz `.editorconfig` plik i kliknij przycisk **Otwórz**:

    ![dodawanie nowego okna pliku](media/editorconfig-image3b.png)

5. Po wyświetleniu następującego okna dialogowego wybierz opcję **Kopiuj plik do katalogu** i wybierz przycisk **OK:**

    ![Opcje okna dialogowego Dodawanie pliku do folderu](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Odzwierciedlanie ustawień .editorconfig

Po dodaniu pliku EditorConfig do bazy kodu każdy nowy dodany kod jest automatycznie formatowany zgodnie z określonymi ustawieniami. Istniejący kod nie odzwierciedla automatycznie ustawień, chyba że sformatujesz bazę kodu.

Aby odzwierciedlić ustawienia z `.editorconfig` pliku, wybierz węzeł rozwiązania i wybierz z paska menu pozycję Edytuj > **Formatuj > Formatuj dokument:**

![Formatowanie dokumentu na pasku menu](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Edytowanie pliku EditorConfig

EditorConfig pliki używają prostego układu plików, aby określić ustawienia, co jest wyjaśnione poniżej przy użyciu poprzedniego przykładu:

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

Ustawienie `root` `true` oznaczania tego pliku jako najbardziej najlepszego pliku `.editorconfig` bazy kodu i wszelkich wyższych plików w projekcie są ignorowane, jak wyjaśniono w sekcji [Ustawienia zastępowania Edytora.](#override-editorconfig-settings)

Każda sekcja jest oznaczona nawiasami klamrowymi square (**[ ] )** i określa informacje o typach plików, do których powinny odnosić się następujące właściwości.

W powyższym przykładzie niektóre ustawienia są stosowane do wszystkich plików w projekcie, a inne są dodawane tylko do plików języka C#. Poniższe zrzuty ekranu pokazują `.editorconfig` przed i po zastosowaniu ustawień:

**Przed:**

![Przed zastosowaniem ustawień editorconfig](media/editorconfig-image4.png)

**Po**:

![po zastosowaniu ustawień editorconfig](media/editorconfig-image5.png)

Aby uzyskać więcej informacji na temat dostępnych ustawień EditorConfig, zobacz [ustawienia konwencji kodowania .NET dla EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) artykułu i [obsługiwane właściwości](https://editorconfig.org/#supported-properties) sekcji w oficjalnej dokumentacji.

## <a name="override-editorconfig-settings"></a>Zastąd w ustawieniach edytora

W każdym rozwiązaniu można `.editorconfig` mieć więcej niż jeden plik. Visual Studio dla `.editorconfig` komputerów Mac odczytuje pliki od góry do dołu w rozwiązaniu, dodając i zastępując ustawienia, jak to idzie. Oznacza to, że `.editorconfig` pierwszeństwo mają ustawienia _znajdujące_ się najbliżej edytowanych plików. Ustawienia są pobierane z `.editorconfig` pliku tego samego folderu `.editorconfig` (jeśli istnieje), a następnie w folderze nadrzędnym (jeśli istnieje), itp. aż znajdzie `root=true`.

Jeśli chcesz upewnić _no_ się, że żadne `.editorconfig` ustawienia z plików wyższego poziomu nie są `root=true` stosowane do tej części `.editorconfig` bazy kodu, dodaj właściwość do górnej części pliku niższego poziomu:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie niestandardowych ustawień edytora za pomocą funkcji EditorConfig (visual studio w systemie Windows)](/visualstudio/ide/create-portable-custom-editor-options)