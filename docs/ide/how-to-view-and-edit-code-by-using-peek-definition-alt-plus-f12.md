---
title: Korzystanie z definicji wglądu
ms.date: 01/10/2018
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 753d26e2c48f6263ccbc9c403f255948b5077924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86092313"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Instrukcje: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)

Aby wyświetlić i edytować kod bez przełączania się z kodu, który piszesz, można użyć polecenia Sprawdź **definicję** . Zobacz **definicję** i **Przejdź do definicji** Pokaż te same informacje, ale w oknie podręcznym wybierz pozycję **Definicja wglądu** , a następnie **Przejdź do** definicji — pokazuje kod w oddzielnym oknie kodu. Polecenie **Przejdź do definicji** powoduje, że kontekst (czyli aktywne okno kodu, bieżący wiersz i pozycja kursora) do przełączenia do okna kodu definicji. Przy użyciu **definicji wglądu**można wyświetlać i edytować definicję i poruszać się wewnątrz pliku definicji, zachowując swoje miejsce w oryginalnym pliku kodu.

Możesz użyć **definicji wglądu** z kodem C#, Visual Basic i C++. W Visual Basic funkcja **wglądu do definicji** pokazuje łącze do **Przeglądarka obiektów** dla symboli, które nie mają metadanych definicji (na przykład typów wbudowanych w programie .NET).

## <a name="use-peek-definition"></a>Użyj definicji wglądu

### <a name="open-a-peek-definition-window"></a>Otwórz okno definicji wglądu

1. Możesz uzyskać wgląd w definicję, wybierając pozycję Sprawdź **definicję** z menu dostępnego po kliknięciu prawym przyciskiem myszy dla typu lub elementu członkowskiego, który chcesz zbadać. Jeśli ta opcja jest włączona, można także skorzystać z klawiatury, naciskając klawisz **Ctrl** (lub inny modyfikator) i klikając nazwę elementu członkowskiego. Lub na klawiaturze naciśnij klawisz **Alt** + **F12**.

     Na tej ilustracji przedstawiono okno **definicji wglądu** dla metody o nazwie `Print()` :

     ![Okno wglądu](../ide/media/peekwindow.png)

     Okno definicji jest wyświetlane poniżej `printer.Print("Hello World!")` wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Poniższe wiersze `printer.Print("Hello World!")` pojawiają się w oknie definicji.

1. Kursor można przenieść do różnych lokalizacji w oknie Definicja wglądu. Nadal można poruszać się w oknie oryginalnego kodu.

1. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.

1. Możesz zamknąć okno definicji, wybierając klawisz **ESC** lub przycisk **Zamknij** na karcie okna definicji.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otwórz okno definicji wglądu z poziomu okna definicji wglądu

Jeśli masz już otwarte okno **definicji wglądu** , możesz ponownie wywołać **definicję wglądu** do kodu w tym oknie. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.

   ![Wgląd w okno w oknie wglądu](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>Wgląd do definicji z wieloma wynikami

Jeśli używasz funkcji **wglądu definicję** w kodzie, który ma więcej niż jedną definicję (na przykład klasy częściowej), lista wyników pojawi się z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.

   ![Wgląd do okna z wielu wyników](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>Edytuj wewnątrz okna definicji wglądu

Gdy zaczniesz edytować wewnątrz okna **definicji wglądu** , modyfikowany plik zostanie automatycznie otwarty jako osobna karta w edytorze kodu i będzie odzwierciedlać wprowadzone zmiany. Można nadal wprowadzać, cofać i zapisywać zmiany w oknie **Definicja wglądu** , a karta będzie nadal odzwierciedlać te zmiany. Nawet jeśli zamkniesz okno **definicji wglądu** bez zapisywania zmian, możesz wprowadzać, cofać i zapisywać więcej zmian na karcie, wybierając dokładnie miejsce w oknie **Definicja wglądu** .

   ![Edytowanie w oknie wglądu](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>Aby zmienić opcje definicji wglądu

1. Przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **Ogólne**.

1. Wybierz opcję **Otwórz definicję w widoku wglądu**.

1. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Opcje** .

   ![Ustawianie opcji wyboru podglądu kliknięcia przycisku myszy](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>Skróty klawiaturowe dla definicji wglądu

Możesz użyć następujących skrótów klawiaturowych z oknem **definicji wglądu** :

|Funkcja|Skrót klawiaturowy|
|-------------------|:-----------------------:|
|Otwórz okno definicji|**Alt** + **F12**|
|Zamknij okno definicji|**Esc**|
|Promuj okno definicji do karty zwykłego dokumentu|**Ctrl** + **Alt** + **Strona główna**|
|Przechodzenie między oknami definicji|**Ctrl** + **Alt** + Alt **-** i **Ctrl** + **Alt**+**=**|
|Przechodzenie między wieloma wynikami|**F8** i **SHIFT** + **F8**|
|Przełączanie się między oknem edytora kodu i oknem definicji|**SHIFT** + **ESC**|

> [!NOTE]
> Możesz również użyć tych samych skrótów klawiaturowych do edycji kodu w oknie **definicji wglądu** w innym miejscu w programie Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Nawiguj po kodzie](../ide/navigating-code.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Funkcje produktywności w programie Visual Studio](../ide/productivity-features.md)
