---
title: Wyświetlanie definicji typów
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d78614966a33421aac707f370f2b18e62e4b3d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603542"
---
# <a name="view-type-and-member-definitions"></a>Wyświetlanie definicji typów i elementów członkowskich

Deweloperzy często muszą wyświetlić definicje kodu źródłowego dla typów lub członków klasy, których używają w kodzie. W programie Visual Studio funkcje **Przejdź do definicji** i **wglądu w definicję** umożliwiają łatwe wyświetlanie definicji typu lub elementu członkowskiego. Jeśli kod źródłowy jest niedostępny, zamiast tego są wyświetlane metadane.

## <a name="go-to-definition"></a>Przejdź do definicji

Funkcja **Przejdź do definicji** nawiguje do źródła typu lub elementu członkowskiego, a następnie otwiera wynik na nowej karcie. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu w miejscu wewnątrz nazwy symbolu i naciśnij klawisz **F12**. Jeśli jesteś użytkownikiem myszy, wybierz opcję **Przejdź do definicji** z menu po kliknięciu prawym przyciskiem myszy lub użyj funkcji **Ctrl-kliknięcie** opisanej w poniższej sekcji.

### <a name="ctrl-click-go-to-definition"></a>Ctrl-kliknij Przejdź do definicji

**Ctrl** +**kliknięciu** jest skrótem dla użytkowników myszy, aby szybko uzyskać dostęp **do usługi przejdź do definicji**. Symbole można klikać po naciśnięciu klawisza **Ctrl** i umieszczeniu wskaźnika myszy nad typem lub członkiem. Aby szybko przejść do definicji symbolu, naciśnij klawisz **Ctrl** , a następnie kliknij go. To bardzo proste!

![Kliknięcie przycisku Przejdź do animacji definicji](../ide/media/click_gotodef.gif)

Możesz zmienić klawisz modyfikujący dla kliknięcia przycisku myszy **Przejdź do definicji** , przechodząc do pozycji **narzędzia**  > **Opcje**  > **Edytor tekstów**  > **Ogólne**, a następnie wybierając **Alt** lub **Ctrl** 0**ALT** z listy rozwijanej **Użyj klawisza modyfikującego** . Możesz również wyłączyć myszą, klikając przycisk **Przejdź do definicji** , usuwając zaznaczenie pola wyboru **Włącz myszą, aby wykonać przechodzenie do definicji** .

![Włączanie myszy kliknij pozycję Przejdź do definicji](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Definicja wglądu

Funkcja **definicji wglądu** umożliwia wyświetlenie podglądu definicji typu bez opuszczania bieżącej lokalizacji w edytorze. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu w miejscu wewnątrz typu lub elementu członkowskiego, a następnie naciśnij klawisze **Alt + F12**. Jeśli jesteś użytkownikiem myszy, możesz wybrać opcję Wybierz **definicję** z menu rozwijanego po kliknięciu prawym przyciskiem myszy.

Aby włączyć **klawisz Ctrl** +**kliknij pozycję** funkcje, przejdź do pozycji **Narzędzia**  > **Opcje**  > **Edytor tekstu**  > **Ogólne**. Wybierz opcję **Otwórz definicję w widoku wglądu** i kliknij przycisk **OK** , aby zamknąć okno dialogowe **Opcje** .

![Ustawianie opcji wyboru podglądu kliknięcia przycisku myszy](../ide/media/editor_options_peek_view.png)

Następnie naciśnij klawisz **Ctrl** (lub dowolny klawisz modyfikujący w **opcjach**), a następnie kliknij typ lub element członkowski.

![Podgląd animacji definicji](../ide/media/peek_definition.gif)

Jeśli połączysz inną definicję z okna podręcznego, utworzysz ścieżkę do stron nadrzędnych, którą można nawigować przy użyciu okręgów i strzałek, które są wyświetlane nad menu podręczne.

Aby uzyskać więcej informacji, zobacz [How to: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Wyświetl metadane jako kod źródłowy (C#)

Podczas przeglądania definicji C# typów lub elementów członkowskich, których kod źródłowy jest niedostępny, zamiast tego są wyświetlane ich metadane. Można wyświetlić deklaracje typów i członków, ale nie ich implementacji.

Po uruchomieniu polecenia **Przejdź do definicji** lub **wglądu definicji** dla elementu, którego kod źródłowy jest niedostępny, dokument z kartami zawierający widok metadanych tego elementu, wyświetlany jako kod źródłowy, pojawia się w edytorze kodu. Nazwa typu, a następnie **[z metadanych]** pojawia się na karcie dokumentu.

Na przykład, jeśli uruchomisz polecenie **Przejdź do definicji** <xref:System.Console>, metadane dla <xref:System.Console> są wyświetlane w edytorze kodu jako C# kod źródłowy. Kod jest podobny do swojej deklaracji, ale nie pokazuje implementacji.

![Metadane jako źródło](../ide/media/metadatasource.png)

> [!NOTE]
> Podczas próby uruchomienia polecenia **Przejdź do definicji** lub **wglądu definicji** dla typów lub elementów członkowskich, które są oznaczone jako wewnętrzne, program Visual Studio nie wyświetla swoich metadanych jako kodu źródłowego, niezależnie od tego, czy zestaw, którego dotyczy odwołanie, jest znajomy, czy nie.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Wyświetl dekompilowane Definicje źródeł zamiast metadanych (C#)

Można ustawić opcję wyświetlania dekompilowanego kodu źródłowego podczas wyświetlania definicji C# typu lub elementu członkowskiego, którego kod źródłowy jest niedostępny. Aby włączyć tę funkcję, wybierz pozycję **narzędzia**  > **Opcje** na pasku menu. Następnie rozwiń węzeł **Edytor tekstu**  > **C#**  > **Zaawansowane**i wybierz pozycję **Włącz nawigację do dekompilowanych źródeł**.

![Wyświetlanie dekompilowanej definicji](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Program Visual Studio rekonstruuje treści metod przy użyciu dekompilacji ILSpy. Gdy uzyskujesz dostęp do tej funkcji po raz pierwszy, musisz wyrazić zgodę na oświadczenie prawne dotyczące licencjonowania oprogramowania i praw autorskich oraz przepisów dotyczących znaków towarowych.

## <a name="see-also"></a>Zobacz także

- [Nawiguj po kodzie](../ide/navigating-code.md)
- [Instrukcje: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)