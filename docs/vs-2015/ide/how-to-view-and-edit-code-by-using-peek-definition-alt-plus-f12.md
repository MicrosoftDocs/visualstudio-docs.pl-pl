---
title: 'Instrukcje: Wyświetlanie i edytowanie kodu za pomocą polecenia Zobacz definicję (Alt + F12) | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 76a45297062b42b559f07867b20bdadac79cc082
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63386843"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Instrukcje: Wyświetlanie i edytowanie kodu za pomocą polecenia Zobacz definicję (Alt + F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **Peek Definition** polecenie, aby wyświetlić i edytować kod bez przełączania kodu, który właśnie piszesz. **Zobacz definicję** i **przejdź do definicji** wyświetlane te same informacje, ale **zobacz definicję** pojawia się w oknie podręcznym, a **przejdź do definicji** pokazuje kod w oddzielnym oknie kodu. **Przejdź do definicji** powoduje, że kontekst (to znaczy aktywne okno kodu, bieżący wiersz i pozycja kursora) przełączyć się do okna kodu definicji. Za pomocą **Peek Definition**, można wyświetlać i edytować definicję i poruszać się wewnątrz pliku definicji, zachowując swoje miejsce w oryginalnym pliku kodu.  
  
 Możesz użyć **Peek Definition** przy użyciu kodu C#, Visual Basic i C++. W języku Visual Basic **Peek Definition** Wyświetla łącze do **przeglądarki obiektów** dla symboli, które nie mają metadanych definicji (na przykład typów programu .NET Framework, które są wbudowane).  
  
> [!IMPORTANT]
> Tego polecenia nie można użyć w dowolnej wersji Express programu Visual Studio 2013.  
  
## <a name="working-with-peek-definition"></a>Praca z funkcją Zobacz definicję  
  
#### <a name="to-open-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję  
  
1. Możesz znaleźć **Peek Definition** , otwierając menu skrótów dla metody, którą chcesz zbadać. (Klawiatura: Alt+F12)  
  
     Ta ilustracja przedstawia **Peek Definition** okna dla metody, która nosi nazwę `Print()`:  
  
     ![Wgląd do okna](../ide/media/peekwindow.png "PeekWindow")  
  
     Okno definicji jest wyświetlane poniżej `printer.Print(“Hello World!”)` wiersza w oryginalnym pliku. Okno nie ukrywa żadnego kodu w pliku oryginalnym. Wiersze, które następują `printer.Print(“Hello World!”)` wywołania są wyświetlane w oknie definicji.  
  
2. Możesz przenieść kursor w inne miejsce w oknie definicji kodu. Nadal możesz się przemieszczać w oknie oryginalnego kodu powyżej lub poniżej okna definicji.  
  
3. Można skopiować ciąg z okna definicji i wkleić go w kodzie oryginalnym. Możesz również przeciągać i upuszczać ciąg z okna definicji do oryginalnego kodu bez usuwania go z okna definicji.  
  
4. Możesz zamknąć okno definicji wybierając klawisz Esc lub **Zamknij** przycisku na karcie okna definicji.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Aby otworzyć okno Zobacz definicję z poziomu okna Zobacz definicję  
  
- Jeśli masz już **Peek Definition** otwarte okno, można wywołać **Peek Definition** ponownie dla kodu w tym oknie. Otwiera się inne okno definicji. Zestaw łączy do stron nadrzędnych obok karty w oknie definicji, służący do nawigacji między oknami definicji. Etykietka narzędzia na każdej kropce ukazuje nazwę pliku i ścieżkę pliku definicji, którą ta kropka reprezentuje.  
  
     ![Okno podglądu w oknie podglądu](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Aby użyć funkcji Zobacz definicję z wieloma wynikami  
  
- Jeśli używasz **Peek Definition** wobec kodu, który ma więcej niż jedną definicję (na przykład klas częściowych), lista wyników pojawi się z prawej strony widoku definicji kodu. Możesz wybrać dowolny wynik na liście, aby wyświetlić jego definicję.  
  
     ![Okno podglądu z wieloma wynikami](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Aby edytować wewnątrz okna Zobacz definicję  
  
- Podczas uruchamiania do edycji wewnątrz **Peek Definition** okna, plik, który modyfikujesz automatycznie otwiera się jako oddzielna karta w edytorze kodu i odzwierciedla wprowadzone już zmiany. Możesz wprowadzić, cofnąć i zapisać zmiany w **Peek Definition** okna, a karta nadal będzie odzwierciedlała te zmiany. Nawet po zamknięciu okna bez zapisywania zmian można wprowadzić, cofnąć i zapisać więcej zmian na karcie, rozpoczynając dokładnie tam, gdzie przerwano.  
  
     ![Edytowanie w oknie podglądu](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Aby używać skrótów klawiaturowych dla funkcji Zobacz definicję  
  
- Można użyć następujących skrótów klawiaturowych z **Peek Definition** okna:  
  
    |Funkcja|Skrót klawiaturowy|  
    |-------------------|-----------------------|  
    |Otwórz okno definicji|Alt+F12|  
    |Zamknij okno definicji|Esc|  
    |Promuj okno definicji do karty zwykłego dokumentu|Shift+Alt+Home|  
    |Przechodzenie między oknami definicji|Ctrl+Alt+- i Ctrl+Alt+=|  
    |Przechodzenie między wieloma wynikami|F8 i Shift + F8|  
    |Przełączanie się między oknem edytora kodu i oknem definicji|Shift + Esc|  
  
    > [!NOTE]
    > Można również użyć tych samych skrótów klawiaturowych do edycji kodu w **Peek Definition** oknie używasz w innym miejscu w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki dotyczące produktywności](../ide/productivity-tips-for-visual-studio.md)
