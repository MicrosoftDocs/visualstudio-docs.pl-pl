---
title: 'Projektant przepływu pracy — jak: Używanie edytora wyrażeń'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee9738cfce003ef19d311856304d87f6a4b2f15
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918913"
---
# <a name="how-to-use-the-expression-editor"></a>Instrukcje: Używanie edytora wyrażeń

Edytor wyrażeń jest formant projektanta przepływów pracy, który jest używany w wielu działań przepływu pracy do wprowadzania i obliczać wyrażeń. Edytor wyrażeń zapewnia pełni funkcjonalnego środowiska IDE, edytowanie kolorowanie środowiska, takie jak IntelliSense, ParamInfo, między innymi funkcjami zygzaki sygnalizujące błędy. Kompilator sprawdza się wyrażenie po jej wprowadzeniu. Jeśli wyrażenie jest nieprawidłowe, jest wyświetlana ikona błędu. Można również otworzyć Edytor jako **edytora wyrażeń** okno dialogowe.

Wyrażenia są wartości literałów lub kod języka Visual Basic, powiązany z argumentami lub właściwości. Zawierają one elementy wartości (na przykład, zmienne, stałe, literały, właściwości), które są połączone z operacjami umożliwiające uzyskanie nową wartość. Wyrażenia są zapisywane przy użyciu składni VB.NET, nawet jeśli aplikacja znajduje się w programie przy użyciu języka C#. Oznacza to, wielkość liter nie ma znaczenia, porównanie odbywa się przy użyciu pojedynczego równe Zaloguj ("=" zamiast "=="), operatory logiczne są wyrazy "i" i "or" zamiast symbole "& &" i "||", i **nic nie** jest używany zamiast **null**. Aby uzyskać więcej informacji na temat wyrażenia i operatory w języku Visual Basic i przykłady, zobacz [operatory i wyrażenia w języku Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Edytora wyrażeń** zachowuje się w następujący sposób:

- Jeśli fokus nie jest w edytorze wyrażeń, wygląda regularne formant TextBlock.

- Gdy fokus jest ustawiony w edytorze wyrażeń, wygląda i zachowuje się jak kontrolka edytora wyrażeń. Po utracie fokusu, Edytor wyrażeń wygląda regularne TextBlock ponownie.

- Jeśli możesz skoncentrować się na edytorze wyrażeń w rehostowanym projektancie przepływu pracy, następnie go zachowuje się jak pole tekstowe. Gdy fokus jest utracone w rehostowanym projektancie przepływu pracy, edytora wyrażeń będzie wyglądać regularne TextBlock ponownie.

> [!NOTE]
> Funkcja IntelliSense edytora wyrażeń jest dostępna tylko w programie Visual Studio. W Visual Studio i scenariuszy rehostowanym kompilator sprawdza poprawność wyrażenia po wprowadzeniu go i Edytor wyrażeń Wyświetla ikonę błędu, jeśli wyrażenie jest nieprawidłowe.

## <a name="use-the-expression-editor"></a>Używanie edytora wyrażeń

1.  W programie Visual Studio Otwórz projekt nowego lub istniejącego przepływu pracy.

2.  Dodaj na przykład <xref:System.Activities.Statements.Assign> działania przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy ma edytory wyrażenia. Obiekty wyrażeń TextBlock również zostać wyświetlony w Projektancie zmiennej, projektanta argumentów i projektanta argumentów dynamicznych. <xref:System.Activities.Statements.Assign> To działanie służy jako przykład.

3.  Kliknij przycisk edytora wyrażeń po lewej stronie, w Projektancie działań dla <xref:System.Activities.Statements.Assign> działania.

     Parametry szare znaku wodnego  **\<do >** i  **\<wprowadź wyrażenie VB >** są domyślne, ciągi tekstowe edytory wyrażenia w <xref:System.Activities.Statements.Assign> działania.

4.  Wprowadź wyrażenie. Jeśli wprowadzisz ciąg, upewnij się umieścić ciąg w cudzysłowie. Jeśli chcesz powiązać argumentu wyrażenia do zmiennej, należy pozostawić znaki cudzysłowu.

     Gdy wszystko będzie gotowe, wybierz region lub obszar, aby przenieść fokus do innej części projektanta poza edytora wyrażeń. Przesunięcie fokus powoduje, że kompilator, aby sprawdzić poprawność wyrażenia, zgodnie z wcześniejszym opisem.

     Alternatywny sposób, aby wprowadzić lub edytować wyrażenie jest kliknij wielokropek obok nazwy właściwości w siatce właściwości. Wybranie wielokropka otwiera **edytora wyrażeń** jako okno dialogowe.

## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.Presentation.View.ExpressionTextBox>