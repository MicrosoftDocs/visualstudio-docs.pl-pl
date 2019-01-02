---
title: Wyświetlanie definicji typu
ms.date: 01/10/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 349a395312344ab2abcf7c3a5242e7a92cd5e902
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868907"
---
# <a name="view-type-and-member-definitions"></a>Wyświetlanie definicji typów i elementów członkowskich

Często deweloperzy muszą wyświetlać definicje kodu źródłowego dla typów ani elementów członkowskich klasy, których używają w ich kodzie. W programie Visual Studio **przejdź do definicji** i **Peek Definition** funkcje umożliwiają łatwe wyświetlanie definicji typu lub elementu członkowskiego. Jeśli kod źródłowy nie jest dostępna, metadane są wyświetlane w zamian.

## <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** funkcja powoduje przejście do źródłowego typu lub elementu członkowskiego i otwiera wynik w nowej karcie. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekst zawarty wewnątrz nazwy symbolu i naciśnij klawisz **F12**. Jeśli jesteś użytkownikiem myszy, wybrać **przejdź do definicji** z menu kontekstowego lub użyj **naciśniętym klawiszem CTRL** funkcji opisanych w poniższej sekcji.

### <a name="ctrl-click-go-to-definition"></a>Naciśnij klawisz CTRL i kliknij Przejdź do definicji

W programie Visual Studio 2017 wersji 15.4 jest łatwiejszy sposób użytkownikom myszy szybkiego dostępu **przejdź do definicji**. Symbole stają się po naciśnięciu klawisza **Ctrl** i umieść kursor nad typu lub elementu członkowskiego. Szybkie przechodzenie do definicji symbolu, naciśnij klawisz **Ctrl** klucza, a następnie kliknij go. Jest tak proste!

![Przejdź do definicji animacji kliknięcie myszą](../ide/media/click_gotodef.gif)

Możesz zmienić klucz modyfikujący kliknięcie myszą **przejdź do definicji** , przechodząc do **narzędzia** > **opcje** > **Edytor tekstu**   >  **Ogólne**i wybierając opcję **Alt** lub **Ctrl + Alt** z **klawisz modyfikujący użyj**listy rozwijanej. Można również wyłączyć kliknięcie myszą **przejdź do definicji** , usuwając zaznaczenie pola **Włącz kliknięcie myszą, aby wykonać przejdź do definicji** pola wyboru.

![Włączanie kliknięcie myszą, przejdź do definicji](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Zobacz definicję

**Peek Definition** funkcji umożliwia podgląd definicji typu bez opuszczania Twojej bieżącej lokalizacji w edytorze. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekst zawarty wewnątrz nazwy typu lub elementu członkowskiego i naciśnij klawisz **Alt + F12**. Jeśli jesteś użytkownikiem myszy, możesz wybrać **Peek Definition** z menu kontekstowego. W programie Visual Studio 2017 w wersji 15.4 i nowszych istnieje nowy sposób na wyświetlanie podglądu definicji za pomocą myszy. Przejdź najpierw do **narzędzia** > **opcje** > **edytora tekstów** > **ogólne**. Wybierz opcję **Otwórz definicję w widoku podglądu** i kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.

![Ustawianie opcji kliknięcie myszą definicji wglądu](../ide/media/editor_options_peek_view.png)

Naciśnij klawisz **Ctrl** (lub dowolnego klawisz modyfikujący został wybrany w **opcje**) i kliknij pozycję typu lub elementu członkowskiego.

![Peek definition animacji](../ide/media/peek_definition.gif)

Jeśli wgląd w innej definicji w oknie podręcznym zostanie uruchomiona ścieżki linków do stron nadrzędnych, której można nawigować przy użyciu kółka i strzałki, które pojawiają się powyżej okno podręczne.

Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie i edytowanie kodu za pomocą funkcji zobacz definicję (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Wyświetlanie metadanych jako kodu źródłowego (C#)

Podczas wyświetlania definicji C# typy lub elementy członkowskie, których kod źródłowy jest niedostępny, zamiast tego jest wyświetlana ich metadanych. Możesz zobaczyć deklaracje typów i członków, ale nie ich implementacji.

Po uruchomieniu **przejdź do definicji** lub **Peek Definition** polecenia, dla którego kod źródłowy jest niedostępny, elementu z kartami dokument, który zawiera widok metadanych tego elementu wyświetlana jako kod źródłowy zostanie wyświetlony w edytorze kodu. Nazwa typu, a następnie **[z metadanych]**, pojawi się na karcie dokumentu.

Na przykład jeśli uruchomisz **przejdź do definicji** polecenie, aby uzyskać <xref:System.Console>, metadane <xref:System.Console> pojawia się w edytorze kodu jako C# kodu źródłowego. Kod przypomina jego deklaracji, ale nie pokazuje implementację.

![Metadane jako źródło](../ide/media/metadatasource.png)

> [!NOTE]
> Jeśli zostanie podjęta próba uruchomienia **przejdź do definicji** lub **Peek Definition** polecenia dla typów ani elementów członkowskich, które są oznaczone jako wewnętrzne, Visual Studio nie wyświetla ich metadanych jako kodu źródłowego, niezależnie od tego, czy zestaw odwołujący się jest znajomego, czy nie.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Wyświetlanie definicji dekompilowanych źródeł zamiast metadanych (C#)

Nowość w programie Visual Studio 2017 w wersji 15.6, można ustawić opcje, aby wyświetlić kod źródłowy dekompilowanych, podczas wyświetlania definicji C# typu lub elementu członkowskiego, w której kod źródłowy jest niedostępny. Aby włączyć tę funkcję, wybierz opcję **narzędzia** > **opcje** z paska menu. Następnie rozwiń **edytora tekstów** > **C#** > **zaawansowane**i wybierz **Włącz nawigację do dekompilowanych źródeł** .

![Wyświetlanie definicji dekompilowanych](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Program Visual Studio rekonstruuje treści metod przy użyciu dekompilacji użyciu narzędzia do dekompilacji. Korzystać z tej funkcji po raz pierwszy należy Zaakceptuj zrzeczenie odpowiedzialności prawnej dotyczące oprogramowania, licencjonowania i praw autorskich i trademark przepisów.

## <a name="see-also"></a>Zobacz także

- [Przechodzenie do kodu](../ide/navigating-code.md)
- [Instrukcje: Wyświetlanie i edytowanie kodu za pomocą funkcji zobacz definicję (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)