---
title: Za pomocą definicji wglądu
ms.date: 01/10/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eac5c8c47c208f39f74f542fbbff89c8340a93f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591349"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Porady: wyświetlanie i edytowanie kodu za pomocą funkcji zobacz definicję (Alt + F12)

Możesz użyć **Peek Definition** polecenie, aby wyświetlić i edytować kod bez przełączania kodu, który właśnie piszesz. **Zobacz definicję** i **przejdź do definicji** wyświetlane te same informacje, ale **zobacz definicję** pojawia się w oknie podręcznym, a **przejdź do definicji** pokazuje kod w oddzielnym oknie kodu. **Przejdź do definicji** powoduje, że kontekst (to znaczy aktywne okno kodu, bieżący wiersz i pozycja kursora) przełączyć się do okna kodu definicji. Za pomocą **Peek Definition**, można wyświetlać i edytować definicję i poruszać się wewnątrz pliku definicji, zachowując swoje miejsce w oryginalnym pliku kodu.

Możesz użyć **Peek Definition** przy użyciu kodu C#, Visual Basic i C++. W Visual Basic funkcja **wglądu do definicji** pokazuje łącze do **Przeglądarka obiektów** dla symboli, które nie mają metadanych definicji (na przykład typów wbudowanych w programie .NET).

## <a name="use-peek-definition"></a>Użyj definicji wglądu

### <a name="open-a-peek-definition-window"></a>Otwórz okno definicji wglądu

1. Możesz uzyskać wgląd w definicję, wybierając pozycję Sprawdź **definicję** z menu dostępnego po kliknięciu prawym przyciskiem myszy dla typu lub elementu członkowskiego, który chcesz zbadać. Jeśli ta opcja jest włączona, można także skorzystać z klawiatury, naciskając klawisz **Ctrl** (lub inny modyfikator) i klikając nazwę elementu członkowskiego. Lub z klawiatury, naciśnij klawisz **Alt**+**F12**.

     Ta ilustracja przedstawia **Peek Definition** okna dla metody, która nosi nazwę `Print()`:

     ![Okno podglądu](../ide/media/peekwindow.png)

     Okno definicji jest wyświetlane poniżej `printer.Print("Hello World!")` wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, które następują `printer.Print("Hello World!")` są wyświetlane w oknie definicji.

1. Kursor można przenieść do innej lokalizacji w okna definicji wglądu. Możesz nadal można poruszać się w oknie oryginalnego kodu.

1. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.

1. Możesz zamknąć okno definicji wybierając **Esc** klucza lub **Zamknij** przycisku na karcie okna definicji.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otwórz okno zobacz definicję z poziomu okna Zobacz definicję

Jeśli masz już **Peek Definition** otwarte okno, można wywołać **Peek Definition** ponownie dla kodu w tym oknie. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.

   ![Okno podglądu w oknie podglądu](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Zobacz definicję z wieloma wynikami

Jeśli używasz **Peek Definition** wobec kodu, który ma więcej niż jedną definicję (na przykład klasa częściowa), lista wyników pojawi się z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.

   ![Wgląd do okna z wieloma wynikami](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Edytować wewnątrz okna Zobacz definicję

Podczas uruchamiania do edycji wewnątrz **Peek Definition** okna, plik, który modyfikujesz automatycznie otwiera się jako oddzielna karta w edytorze kodu i odzwierciedla wprowadzone już zmiany. Możesz wprowadzić, cofnąć i zapisać zmiany w **Peek Definition** okna, a karta nadal będzie odzwierciedlała te zmiany. Nawet po zamknięciu **Peek Definition** okna bez zapisywania zmian, można wprowadzić, cofnąć i zapisać więcej zmian na karcie Pobieranie dokładnie tam, gdzie Przerwano w **Peek Definition** okna.

   ![Edytowanie w obrębie okna podglądu](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Aby zmienić opcje dla funkcji zobacz definicję

1. Przejdź do **narzędzia** > **opcje** > **edytora tekstów** > **ogólne**.

1. Wybierz opcję **Otwórz definicję w widoku podglądu**.

1. Kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.

   ![Ustawianie opcji kliknięcie myszą definicji wglądu](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Skróty klawiaturowe dla funkcji zobacz definicję

Można użyć następujących skrótów klawiaturowych z **Peek Definition** okna:

|Funkcja|Skrót klawiaturowy|
|-------------------|:-----------------------:|
|Otwórz okno definicji|**ALT**+**F12**|
|Zamknij okno definicji|**ESC**|
|Promuj okno definicji do karty zwykłego dokumentu|**SHIFT**+**Alt**+**strona główna**|
|Przechodzenie między oknami definicji|**CTRL**+**Alt** + **-** i **Ctrl**+**Alt**+ **=**|
|Przechodzenie między wieloma wynikami|**F8** i **Shift**+**F8**|
|Przełączanie się między oknem edytora kodu i oknem definicji|**SHIFT**+**Esc**|

> [!NOTE]
> Można również użyć tych samych skrótów klawiaturowych do edycji kodu w **Peek Definition** oknie używasz w innym miejscu w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- [Przechodzenie do kodu](../ide/navigating-code.md)
- [Polecenia Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Funkcje produktywności w programie Visual Studio](../ide/productivity-features.md)
