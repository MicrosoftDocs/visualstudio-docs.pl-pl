---
title: 'Projektant przepływu pracy — jak: korzystanie z edytora wyrażeń'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04c0fdaab87c88028b8c14ca59e93fa93e74be74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817440"
---
# <a name="how-to-use-the-expression-editor"></a>Instrukcje: Używanie edytora wyrażeń

Edytor wyrażeń jest formantem Projektant przepływu pracy, który jest używany w wielu działaniach przepływu pracy do wprowadzania i obliczania wyrażeń. Edytor wyrażeń zawiera dopracowane środowisko edycji środowiska IDE, w tym funkcje IntelliSense, kolorowanie, ParamInfo, zygzaki błędów, między innymi. Kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu. Jeśli wyrażenie jest nieprawidłowe, zostanie wyświetlona ikona błędu. Edytor można także otworzyć jako okno dialogowe **Edytor wyrażeń** .

Wyrażenia są wartościami literałów lub Visual Basic kodzie związanym z argumentami lub właściwościami. Zawierają one elementy wartości (na przykład zmienne, stałe, literały, właściwości), które są łączone z operacjami w celu uzyskania nowej wartości. Wyrażenia są zapisywane przy użyciu składni VB.NET, nawet jeśli aplikacja znajduje się w programie przy użyciu języka C#. Oznacza to, że nie ma znaczenia, porównanie jest wykonywane przy użyciu pojedynczego znaku równości ("=" zamiast "= ="), operatory logiczne są słowami "i" i "lub" zamiast symboli "&&" i "| |" i **nic** nie jest używane zamiast **wartości null**. Aby uzyskać więcej informacji na temat wyrażeń i operatorów w Visual Basic i dla niektórych przykładów, zobacz [Operatory i wyrażenia w Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Edytor wyrażeń** zachowuje się w następujący sposób:

- Jeśli fokus nie znajduje się w edytorze wyrażeń, wygląda jak zwykła kontrolka TextBlock.

- Gdy fokus znajduje się w edytorze wyrażeń, wygląda i zachowuje się jak kontrolka Edytor wyrażeń. Po utracie fokusu Edytor wyrażeń będzie wyglądał jak zwykły element TextBlock.

- W przypadku fokusu w edytorze wyrażeń w Projektancie przepływu pracy przeprowadzonej ponownie zachowuje się to jak pole tekstowe. Gdy fokus zostanie utracony w Projektancie przepływów pracy, Edytor wyrażeń będzie wyglądał jak zwykły element TextBlock.

> [!NOTE]
> Funkcja IntelliSense dla edytora wyrażeń jest dostępna tylko w programie Visual Studio. Zarówno w programie Visual Studio, jak i w scenariuszach rehostowania, kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu, a w edytorze wyrażeń jest wyświetlana ikona błędu, jeśli wyrażenie jest nieprawidłowe.

## <a name="use-the-expression-editor"></a>Używanie edytora wyrażeń

1. W programie Visual Studio Otwórz nowy lub istniejący projekt przepływu pracy.

2. Dodaj na przykład <xref:System.Activities.Statements.Assign> działanie do przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy ma edytory wyrażeń. Bloki tekstu wyrażenia są również wyświetlane w projektancie zmiennych, projektancie argumentów i projektancie argumentów dynamicznych. To <xref:System.Activities.Statements.Assign> działanie jest używane jako przykład.

3. Kliknij Edytor wyrażeń lewy w projektancie działań dla <xref:System.Activities.Statements.Assign> działania.

     Ciągi szarego znaku wodnego **\<To>** i **\<Enter a VB Expression>** są domyślnymi ciągami tekstowymi dla edytorów wyrażeń w <xref:System.Activities.Statements.Assign> działaniu.

4. Wprowadź wyrażenie. Jeśli wprowadzisz ciąg, upewnij się, że zostały umieszczone cudzysłowy wokół ciągu. Jeśli wybierzesz powiązanie argumentu wyrażenia z zmienną, pozostaw cudzysłowy.

     Gdy skończysz, wybierz region lub obszar poza edytorem wyrażeń, aby przenieść fokus do innej części projektanta. Przesunięcie fokusu powoduje, że kompilator sprawdza poprawność wyrażenia zgodnie z wcześniejszym opisem.

     Alternatywny sposób wprowadzania lub edytowania wyrażenia polega na kliknięciu wielokropka obok nazwy właściwości w siatce właściwości. Wybranie wielokropka powoduje otwarcie **edytora wyrażeń** jako okna dialogowego.

## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
