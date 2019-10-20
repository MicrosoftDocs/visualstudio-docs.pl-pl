---
title: 'Instrukcje: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40772919031200466999df2dfbf651fae3ee01e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670570"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Porady: Podgląd i edycja kodu za pomocą definicji wglądu (Alt+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby wyświetlić i edytować kod bez przełączania się z kodu, który piszesz, można użyć polecenia Sprawdź **definicję** . Zobacz **definicję** i **Przejdź do definicji** Pokaż te same informacje, ale w oknie podręcznym wybierz pozycję **Definicja wglądu** , a następnie **Przejdź do** definicji — pokazuje kod w oddzielnym oknie kodu. Polecenie **Przejdź do definicji** powoduje, że kontekst (czyli aktywne okno kodu, bieżący wiersz i pozycja kursora) do przełączenia do okna kodu definicji. Przy użyciu **definicji wglądu**można wyświetlać i edytować definicję i poruszać się wewnątrz pliku definicji, zachowując swoje miejsce w oryginalnym pliku kodu.

 Możesz użyć **definicji wglądu** z C#, Visual Basic i C++ kodu. W Visual Basic, **wgląd do definicji** pokazuje link do **Przeglądarka obiektów** dla symboli, które nie mają metadanych definicji (na przykład typy .NET Framework wbudowane).

> [!IMPORTANT]
> Tego polecenia nie można użyć w dowolnej wersji Express programu Visual Studio 2013.

## <a name="working-with-peek-definition"></a>Praca z funkcją Zobacz definicję

#### <a name="to-open-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję

1. Możesz znaleźć **definicję wglądu** , otwierając menu skrótów dla metody, którą chcesz zbadać. (Klawiatura: Alt+F12)

     Na tej ilustracji przedstawiono okno **definicji wglądu** dla metody o nazwie `Print()`:

     ![Okno wglądu](../ide/media/peekwindow.png "PeekWindow")

     Okno definicji jest wyświetlane poniżej wiersza `printer.Print(“Hello World!”)` w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, które po wywołaniu `printer.Print(“Hello World!”)` są wyświetlane w oknie definicji.

2. Możesz przenieść kursor w inne miejsce w oknie definicji kodu. Nadal możesz się przemieszczać w oknie oryginalnego kodu powyżej lub poniżej okna definicji.

3. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.

4. Możesz zamknąć okno definicji, wybierając klawisz ESC lub przycisk **Zamknij** na karcie okna definicji.

#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję z poziomu okna Zobacz definicję

- Jeśli masz już otwarte okno **definicji wglądu** , możesz ponownie wywołać **definicję wglądu** do kodu w tym oknie. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.

     ![Wgląd w okno w oknie wglądu](../ide/media/peekwithinpeek.png "PeekWithinPeek")

#### <a name="to-use-peek-definition-with-multiple-results"></a>Aby użyć funkcji Zobacz definicję z wieloma wynikami

- Jeśli używasz **definicji wglądu** w kodzie, który ma więcej niż jedną definicję (na przykład klas częściowych), lista wyników pojawi się z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.

     ![Wgląd do okna z wielu wyników](../ide/media/peekmultiple.png "PeekMultiple")

#### <a name="to-edit-inside-the-peek-definition-window"></a>Aby edytować wewnątrz okna Zobacz definicję

- Po rozpoczęciu edycji wewnątrz okna **definicji wglądu** , plik, który jest modyfikowany, jest automatycznie otwierany jako osobna karta w edytorze kodu i odzwierciedla zmiany, które zostały już wykonane. Można nadal wprowadzać, cofać i zapisywać zmiany w oknie **Definicja wglądu** , a karta będzie nadal odzwierciedlać te zmiany. Nawet po zamknięciu okna bez zapisywania zmian można wprowadzić, cofnąć i zapisać więcej zmian na karcie, rozpoczynając dokładnie tam, gdzie przerwano.

     ![Edytowanie w oknie wglądu](../ide/media/peekedit.png "PeekEdit")

#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Aby używać skrótów klawiaturowych dla funkcji Zobacz definicję

- Możesz użyć następujących skrótów klawiaturowych z oknem **definicji wglądu** :

    |Funkcja|Skrót klawiaturowy|
    |-------------------|-----------------------|
    |Otwórz okno definicji|Alt+F12|
    |Zamknij okno definicji|Esc|
    |Promuj okno definicji do karty zwykłego dokumentu|Shift+Alt+Home|
    |Przechodzenie między oknami definicji|Ctrl+Alt+- i Ctrl+Alt+=|
    |Przechodzenie między wieloma wynikami|F8 i Shift + F8|
    |Przełączanie się między oknem edytora kodu i oknem definicji|Shift + Esc|

    > [!NOTE]
    > Możesz również użyć tych samych skrótów klawiaturowych do edycji kodu w oknie **definicji wglądu** w innym miejscu w programie Visual Studio.

## <a name="see-also"></a>Zobacz też
 [Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)
