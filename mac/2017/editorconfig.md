---
title: EditorConfig
description: Korzystanie z pliku editorconfig w celu włączenia spójnych stylów kodowania projektu w Visual Studio dla komputerów Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: be8f508a0055d4cd7cbacf1c728e6d73c8b281f7
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984713"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Tworzenie i edytowanie niestandardowego pliku EditorConfig

W Visual Studio dla komputerów Mac można dodać plik [EditorConfig](https://editorconfig.org/) do projektu lub rozwiązania, aby wymusić spójne style kodowania dla wszystkich, które działają w bazie kodu. Ustawienia zadeklarowane w pliku EditorConfig mają pierwszeństwo przed ustawieniami globalnego edytora tekstu Visual Studio dla komputerów Mac. Przy użyciu pliku EditorConfig w ramach projektu lub bazy kodu, można ustawić styl kodowania, preferencje i ostrzeżenia dla projektu. Ponieważ plik jest częścią bazy kodu, ułatwia wszystkim użytkownikom przestrzeganie praktyk związanych z kodowaniem projektu, niezależnie od środowiska IDE lub edytora kodu, którego używają.

Pliki [EditorConfig](https://editorconfig.org/) są obsługiwane przez wiele środowisk IDE i edytorów kodu, w tym Visual Studio 2017.

## <a name="supported-settings"></a>Obsługiwane ustawienia

Edytor w Visual Studio dla komputerów Mac obsługuje podstawowy zestaw [Właściwości EditorConfig](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig również obsługuje [konwencje kodowania](/visualstudio/ide/editorconfig-code-style-settings-reference) w C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Dodawanie pliku EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Dodawanie nowego pliku EditorConfig

1. Otwórz projekt w Visual Studio dla komputerów Mac. Wybierz węzeł rozwiązania lub projektu, do którego chcesz dodać plik EditorConfig. Dodanie pliku do katalogu rozwiązania powoduje zastosowanie ustawień. editorconfig do wszystkich projektów w rozwiązaniu.

2. Kliknij prawym przyciskiem myszy węzeł i wybierz polecenie **dodaj > nowy plik** , aby otworzyć okno dialogowe **nowy plik** :

    ![Elementy menu zawartość](media/editorconfig-image0.png)

3. Wybierz pozycję **różne > pusty plik tekstowy** i nadaj jej **nazwę** `.editorconfig`. Naciśnij przycisk **New (nowy** ), aby utworzyć plik i otworzyć go w edytorze:

    ![Okno dialogowe Nowy plik](media/editorconfig-image1.png)

    Dodanie elementu na poziomie rozwiązania powoduje automatyczne utworzenie i zagnieżdżenie go w folderze **elementów rozwiązania** :

    ![Element rozwiązania wyświetlany w konsoli rozwiązania](media/editorconfig-image1a.png)

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

4. Ustawienia z pliku `.editorconfig` będą stosowane do każdego nowego kodu, który można napisać, ale istniejący kod może wymagać ponownego sformatowania, aby był zgodny z nowymi ustawieniami. Aby zastosować ustawienia z pliku `.editorconfig` do istniejącego pliku źródłowego, Otwórz plik i wybierz polecenie **Edytuj format > > formatowanie dokumentu** na pasku menu::

    ![Formatowanie elementu menu dokumentu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Dodawanie istniejącego pliku EditorConfig

Jeśli pracujesz z projektem lub rozwiązaniem, które zawiera już plik `.editorconfig`, nie trzeba nic robić, aby zastosować ustawienia. Wszelkie nowe wiersze kodu są formatowane zgodnie z ustawieniami EditorConfig.

Możesz chcieć ponownie użyć istniejącego pliku `.editorconfig` w projekcie. Aby dodać istniejący plik, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy folder, do którego chcesz dodać, a następnie wybierz pozycję **dodaj > Dodaj pliki**.

2. Przejdź do katalogu wymaganego pliku.

3. Pliki zaczynające się od `.` (takie jak `.editorconfig`) są ukrytymi plikami w macOS, więc naciśnij **polecenie + SHIFT +.** Aby wyświetlić `.editorconfig` plik.

4. Wybierz plik `.editorconfig` i kliknij przycisk **Otwórz**:

    ![Dodawanie nowego okna pliku](media/editorconfig-image3b.png)

5. Gdy zostanie wyświetlone następujące okno dialogowe, zaznacz opcję **Kopiuj plik do katalogu** i wybierz **przycisk OK**:

    ![Opcje okna dialogowego Dodawanie pliku do folderu](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Odzwierciedlanie ustawień. editorconfig

Po dodaniu pliku EditorConfig do bazy kodu każdy dodany kod jest automatycznie formatowany zgodnie z określonymi ustawieniami. Istniejący kod nie odzwierciedla ustawień automatycznie, chyba że zostanie sformatowany baza kodu.

Aby odzwierciedlić ustawienia w pliku `.editorconfig`, zaznacz węzeł rozwiązanie i wybierz polecenie **Edytuj format > > formatowanie dokumentu** na pasku menu:

![Formatuj dokument z paska menu](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Edytowanie pliku EditorConfig

Pliki EditorConfig używają prostego układu plików do określania ustawień, co zostało wyjaśnione poniżej przy użyciu poprzedniego przykładu:

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

Ustawienie `root` na `true` flaguje ten plik jako górny plik bazy kodu i wszystkie wyższe `.editorconfig` pliki w projekcie zostaną zignorowane, jak wyjaśniono w sekcji [Przesłoń ustawienia EditorConfig](#override-editorconfig-settings) .

Każda sekcja jest oznaczona przez kwadrat ( **[]** ) nawiasy klamrowe i określa informacje o typach plików, do których powinny odnosić się następujące właściwości.

W powyższym przykładzie niektóre ustawienia są stosowane do wszystkich plików w projekcie, a inne są dodawane tylko do C# plików. Poniższe zrzuty ekranu pokazują przed i po zastosowaniu ustawień `.editorconfig`:

**Przed**:

![Przed zastosowaniem ustawień editorconfig](media/editorconfig-image4.png)

**Po**:

![Po zastosowaniu ustawień editorconfig](media/editorconfig-image5.png)

Aby uzyskać więcej informacji na temat dostępnych ustawień EditorConfig, zobacz artykuł [Ustawienia konwencji kodowania .NET dla EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) i sekcja [obsługiwane właściwości](https://editorconfig.org/#supported-properties) w oficjalnej dokumentacji.

## <a name="override-editorconfig-settings"></a>Zastąp ustawienia EditorConfig

W każdym rozwiązaniu można mieć więcej niż jeden plik `.editorconfig`. Visual Studio dla komputerów Mac odczytuje `.editorconfig` pliki z góry do dołu w rozwiązaniu, dodając i zastępując ustawienia w miarę ich wypełniania. Oznacza to, że ustawienia znajdujące się w `.editorconfig` _najbliżej_ edytowanego pliku będą mieć pierwszeństwo. Ustawienia są pobierane z pliku `.editorconfig` tego samego folderu (jeśli istnieje), a następnie `.editorconfig` w folderze nadrzędnym (jeśli istnieje) itd. do momentu znalezienia `root=true`.

Jeśli chcesz upewnić się, że żadne ustawienia z plików `.editorconfig` wyższego poziomu _nie_ są stosowane do tej części bazy kodu, dodaj Właściwość `root=true` na początku pliku `.editorconfig` niższego poziomu:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych ustawień edytora za pomocą EditorConfig (Visual Studio w systemie Windows)](/visualstudio/ide/create-portable-custom-editor-options)