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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592077"
---
# <a name="view-type-and-member-definitions"></a>Wyświetlanie definicji typów i elementów członkowskich

Deweloperzy często trzeba wyświetlić definicje kodu źródłowego dla typów lub członków klasy, których używają w kodzie. W programie Visual Studio **funkcje Przejdź do definicji** i **definicji wglądu** umożliwiają łatwe wyświetlanie definicji typu lub elementu członkowskiego. Jeśli kod źródłowy nie jest dostępny, zamiast tego są wyświetlane metadane.

## <a name="go-to-definition"></a>Przejdź do definicji

Funkcja **Przejdź do definicji** przechodzi do źródła typu lub elementu członkowskiego i otwiera wynik na nowej karcie. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu gdzieś wewnątrz nazwy symbolu i naciśnij **klawisz F12**. Jeśli jesteś użytkownikiem myszy, wybierz polecenie **Przejdź do definicji** z menu po kliknięciu prawym przyciskiem myszy lub użyj funkcji **kliknięcia klawiszem Ctrl** opisaną w poniższej sekcji.

### <a name="ctrl-click-go-to-definition"></a>Ctrl-kliknij przycisk Przejdź do definicji

**Kliknięcie klawisza Ctrl**+**to** skrót dla użytkowników myszy, aby szybko uzyskać dostęp **do opcji Przejdź do definicji**. Symbole stają się klikalne po naciśnięciu **klawisza Ctrl** i umieszczeniu wskaźnika myszy na typie lub człowieczeńsku. Aby szybko przejść do definicji symbolu, naciśnij klawisz **Ctrl,** a następnie kliknij go. To takie proste!

![Kliknięcie myszą przejdź do animacji definicji](../ide/media/click_gotodef.gif)

Klucz modyfikatora myszy można kliknąć myszą **Kliknij pozycję Przejdź do definicji,** przechodząc do **Tools** > **edytora** > tekstu Narzędzia**Opcje** > tekstu**i**wybierając **alt** lub **klawisz Ctrl**+**Alt** z listy rozwijanej **Użyj klawisza modyfikatora.** Można również wyłączyć kliknięcie myszą, klikając przycisk **Przejdź do definicji,** odznaczając pole wyboru **Włącz kliknięcie myszą, aby wykonać polecenie Przejdź do definicji.**

![Włączanie klikania myszy przejdź do definicji](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Podejrzyj definicję

Funkcja **Definicji wglądu** umożliwia podgląd definicji typu bez pozostawiania bieżącej lokalizacji w edytorze. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu w miejscu wewnątrz nazwy typu lub członka i naciśnij **klawisze Alt + F12**. Jeśli jesteś użytkownikiem myszy, możesz wybrać opcję **Zaglądanie do definicji** z menu po kliknięciu prawym przyciskiem myszy.

Aby włączyć funkcję**kliknięcia** **klawisza Ctrl,**+przejdź do **edytora** > **tekstu Narzędzia** > **Opcje** > tekstu **.** Wybierz opcję **Otwórz definicję w widoku wglądu** i kliknij przycisk **OK,** aby zamknąć okno dialogowe **Opcje.**

![Ustawianie opcji definicji wglądu do kliknięcia myszą](../ide/media/editor_options_peek_view.png)

Następnie naciśnij klawisz **Ctrl** (lub dowolny klawisz modyfikatora w **opcji)** i kliknij typ lub element członkowski.

![Animacja definicji wglądu](../ide/media/peek_definition.gif)

Jeśli zerkniesz na inną definicję z okna podręcznego, rozpoczniesz ścieżkę nawigacji, którą można poruszać się za pomocą okręgów i strzałek wyświetlanych nad wyskakującym okienkiem.

Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie i edytowanie kodu przy użyciu funkcji Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Wyświetlanie metadanych jako kodu źródłowego (C#)

Podczas wyświetlania definicji typów Języka C# lub członków, których kod źródłowy nie jest dostępny, ich metadane są wyświetlane zamiast tego. Można zobaczyć deklaracje typów i członków, ale nie ich implementacje.

Po uruchomieniu polecenia **Przejdź do definicji** lub **definicji wglądu** dla elementu, którego kod źródłowy jest niedostępny, w edytorze kodu pojawia się dokument z kartami zawierający widok metadanych tego elementu, wyświetlany jako kod źródłowy. Nazwa typu, po której następuje **[z metadanych]**, pojawia się na karcie dokumentu.

Na przykład po uruchomieniu polecenia **Przejdź do definicji** dla <xref:System.Console>metadane dla <xref:System.Console> pojawia się w edytorze kodu jako kod źródłowy języka C#. Kod przypomina jego deklaracji, ale nie pokazuje implementacji.

![Metadane jako źródło](../ide/media/metadatasource.png)

> [!NOTE]
> Podczas próby uruchomienia **polecenia Przejdź do definicji** lub **definicji wglądu** dla typów lub elementów członkowskich, które są oznaczone jako wewnętrzne, Visual Studio nie wyświetla ich metadanych jako kod źródłowy, niezależnie od tego, czy zestaw odwołujący się jest przyjacielem, czy nie.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Wyświetlanie dekompilowanych definicji źródeł zamiast metadanych (C#)

Można ustawić opcję, aby wyświetlić dekompilowany kod źródłowy podczas wyświetlania definicji typu C# lub elementu członkowskiego, którego kod źródłowy jest niedostępny. Aby włączyć tę funkcję, wybierz pozycję**Opcje** **narzędzi** > z paska menu. Następnie rozwiń węzeł **Edytor** > tekstu**C#** > **Zaawansowane**i wybierz pozycję **Włącz nawigację do dekompilowanych źródeł**.

![Wyświetlanie dekompilowanych definicji](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje treści metody przy użyciu dekompilacji ILSpy. Przy pierwszym dostępie do tej funkcji użytkownik musi wyrazić zgodę na wyłączenie odpowiedzialności prawnej w odniesieniu do prawa do licencjonowania oprogramowania oraz praw autorskich i znaków towarowych.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie](../ide/navigating-code.md)
- [Jak: Wyświetlanie i edytowanie kodu przy użyciu funkcji Peek Definition (Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
