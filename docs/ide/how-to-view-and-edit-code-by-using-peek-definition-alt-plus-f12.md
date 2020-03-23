---
title: Korzystanie z definicji wglądu
ms.date: 01/10/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eac5c8c47c208f39f74f542fbbff89c8340a93f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591349"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Jak: Wyświetlanie i edytowanie kodu przy użyciu funkcji Peek Definition (Alt+F12)

Za pomocą polecenia **Peek Definition** można wyświetlać i edytować kod bez przełączania się od kodu, który piszesz. **Peek Definition** i **Go To Definition** wyświetlają te same informacje, ale **peek definition** pokazuje go w wyskakującym oknie, a Przejdź do **definicji** pokazuje kod w osobnym oknie kodu. **Przejdź do definicji** powoduje, że kontekst (czyli aktywne okno kodu, bieżący wiersz i położenie kursora), aby przełączyć się do okna kodu definicji. Za pomocą **funkcji Peek Definition**można wyświetlać i edytować definicję oraz poruszać się wewnątrz pliku definicji, zachowując miejsce w oryginalnym pliku kodu.

Można użyć **peek definicji** z c#, Visual Basic i C++ kod. W języku Visual Basic **definicja wglądu** zawiera łącze do **przeglądarki obiektów** dla symboli, które nie mają metadanych definicji (na przykład .NET typów, które są wbudowane).

## <a name="use-peek-definition"></a>Użyj definicji wglądu

### <a name="open-a-peek-definition-window"></a>Otwieranie okna Definicja wglądu

1. Można zajrzeć do definicji, wybierając **opcję Peek Definition** z menu po kliknięciu prawym przyciskiem myszy dla typu lub elementu członkowskiego, który chcesz eksplorować. Jeśli ta opcja jest włączona, można również zapoznać się z definicją za pomocą myszy, naciskając klawisz **Ctrl** (lub inny modyfikator) i klikając nazwę elementu członkowskiego. Lub, z klawiatury, naciśnij **klawisz Alt**+**F12**.

     Na tej ilustracji przedstawiono okno **Definicja wglądu** dla metody o nazwie: `Print()`

     ![Okno wglądu](../ide/media/peekwindow.png)

     Okno definicji pojawi `printer.Print("Hello World!")` się poniżej wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, `printer.Print("Hello World!")` które następują są wyświetlane w oknie definicji.

1. Kursor można przenieść do różnych lokalizacji w oknie definicji wglądu. Nadal można poruszać się w oryginalnym oknie kodu.

1. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.

1. Okno definicji można zamknąć, wybierając klawisz **Esc** lub przycisk **Zamknij** na karcie okna definicji.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otwieranie okna Definicja wglądu z poziomu okna Definicja wglądu

Jeśli masz już otwarte okno **definicji wglądu,** możesz ponownie wywołać **definicję wglądu** w kod w tym oknie. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.

   ![Zaglądaj do okna wglądu w okno wgląd](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Peek Definition z wieloma wynikami

Jeśli używasz **definicji wglądu** w kod, który ma więcej niż jedną definicję (na przykład klasy częściowej), lista wyników pojawia się po prawej stronie widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.

   ![Zaglądanie do okna z wielu wyników](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Edytowanie wewnątrz okna Definicja wglądu

Po rozpoczęciu edycji w oknie **Definicji wglądu** plik, który modyfikujesz, zostanie automatycznie otwarty jako osobna karta w edytorze kodu i odzwierciedla wprowadzone zmiany. Możesz nadal wprowadzać, cofać i zapisywać zmiany w oknie **Definicja wglądu,** a karta będzie nadal odzwierciedlać te zmiany. Nawet jeśli zamkniesz okno **Definicja wglądu** bez zapisywania zmian, możesz wprowadzić, cofnąć i zapisać więcej zmian na karcie, podnosząc dokładnie miejsce, w którym zostało przerwane w oknie **Definicja wglądu.**

   ![Edytowanie w oknie wglądu](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Aby zmienić opcje definicji wglądu

1. Przejdź do**Options** > **edytora tekstu** > Opcje **narzędzi** > **.**

1. Wybierz opcję **Otwórz definicję w widoku wglądu**.

1. Kliknij **przycisk OK,** aby zamknąć okno dialogowe **Opcje.**

   ![Ustawianie opcji definicji wglądu do kliknięcia myszą](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Skróty klawiaturowe w definicji wglądu

Tych skrótów klawiaturowych można używać w oknie **Definicja wglądu:**

|Funkcjonalność|Skrót klawiaturowy|
|-------------------|:-----------------------:|
|Otwórz okno definicji|**Alt**+**F12**|
|Zamknij okno definicji|**Esc**|
|Promuj okno definicji do karty zwykłego dokumentu|**Shift**+**Alt**+**Strona główna**|
|Przechodzenie między oknami definicji|**Ctrl**+**Alt** + **-** i **Ctrl**+**Alt**+**=**|
|Przechodzenie między wieloma wynikami|**F8** i **Shift**+**F8**|
|Przełączanie się między oknem edytora kodu i oknem definicji|**Przesunięcie**+**Esc**|

> [!NOTE]
> Można również użyć tych samych skrótów klawiaturowych do edycji kodu w oknie **definicji wglądu,** jak używasz w innym miejscu w programie Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie](../ide/navigating-code.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Funkcje zwiększające produktywność w programie Visual Studio](../ide/productivity-features.md)
