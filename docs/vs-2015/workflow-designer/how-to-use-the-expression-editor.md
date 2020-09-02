---
title: 'Instrukcje: korzystanie z edytora wyrażeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54099bc5c0f249cdb3697715d153a94a596ac344
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849233"
---
# <a name="how-to-use-the-expression-editor"></a>Instrukcje: Używanie edytora wyrażeń
Edytor wyrażeń jest [!INCLUDE[wfd1](../includes/wfd1-md.md)] formantem, który jest używany w wielu działaniach przepływu pracy jako sposób wprowadzania i oceniania tych wyrażeń. Edytor wyrażeń zawiera dopracowane środowisko edycji środowiska IDE, w tym funkcje IntelliSense, kolorowanie, ParamInfo, zygzaki błędów, między innymi. Kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu. Jeśli wyrażenie jest nieprawidłowe, zostanie wyświetlona ikona błędu. Edytor można także otworzyć jako okno dialogowe **Edytor wyrażeń** .

 Wyrażenia są wartościami literału lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodem związanym z argumentami lub właściwościami. Zawierają one elementy wartości (np. zmienne, stałe, literały, właściwości), które są łączone z operacjami w celu uzyskania nowej wartości. Wyrażenia są zapisywane przy użyciu składni VB.NET, nawet jeśli aplikacja znajduje się w programie przy użyciu języka C#. Oznacza to, że nie ma znaczenia, porównanie jest wykonywane przy użyciu pojedynczego znaku równości ("=") zamiast ("= ="), operatory logiczne to słowa "i" i "lub" zamiast symboli "&&" i "&#124;&#124;", a **niczego** nie są używane zamiast **wartości null**. Aby uzyskać więcej informacji na temat wyrażeń i operatorów w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i dla niektórych przykładów, zobacz [Operatory i wyrażenia w Visual Basic](https://msdn.microsoft.com/library/a1w3te48(VS.100).aspx).

 **Edytor wyrażeń** zachowuje się w następujący sposób:

- Jeśli fokus nie znajduje się w edytorze wyrażeń, wygląda jak zwykła kontrolka TextBlock.

- Gdy fokus znajduje się w edytorze wyrażeń, wygląda i zachowuje się jak kontrolka Edytor wyrażeń. Po utracie fokusu będzie on wyglądał jak zwykły element TextBlock.

- W przypadku fokusu w edytorze wyrażeń w Projektancie przepływu pracy przeprowadzonej ponownie zachowuje się to jak pole tekstowe. Gdy fokus zostanie utracony w Projektancie przepływów pracy, Edytor wyrażeń będzie wyglądał jak zwykły element TextBlock.

> [!NOTE]
> Funkcja IntelliSense dla edytora wyrażeń jest dostępna tylko w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Zarówno w [!INCLUDE[vs2010](../includes/vs2010-md.md)] scenariuszach, jak i w scenariuszu rehostowania, kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu, a w edytorze wyrażeń jest wyświetlana ikona błędu, jeśli wyrażenie jest nieprawidłowe.

### <a name="using-the-expression-editor"></a>Korzystanie z edytora wyrażeń

1. W programie [!INCLUDE[vs2010](../includes/vs2010-md.md)] Otwórz nowy lub istniejący projekt przepływu pracy.

2. Dodaj na przykład <xref:System.Activities.Statements.Assign> działanie do przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy ma edytory wyrażeń. Bloki tekstu wyrażenia są również wyświetlane w projektancie zmiennych, projektancie argumentów i projektancie argumentów dynamicznych. To <xref:System.Activities.Statements.Assign> działanie jest używane jako przykład.

3. Kliknij Edytor wyrażeń lewy w projektancie działań dla <xref:System.Activities.Statements.Assign> działania.

     Ciągi szarego znaku wodnego **\<To>** i **\<Enter a VB Expression>** są domyślnymi ciągami tekstowymi dla edytorów wyrażeń w <xref:System.Activities.Statements.Assign> działaniu.

4. Wprowadź wyrażenie. Jeśli wprowadzisz ciąg, upewnij się, że zostały umieszczone cudzysłowy wokół ciągu. Jeśli wybierzesz powiązanie argumentu wyrażenia z zmienną, pozostaw cudzysłowy.

     Gdy wszystko będzie gotowe, wybierz region lub obszar poza edytorem wyrażeń, aby przenieść fokus do innej części projektanta. Spowoduje to, że kompilator sprawdzi poprawność wyrażenia zgodnie z wcześniejszym opisem.

     Alternatywny sposób wprowadzania/edytowania wyrażenia polega na kliknięciu wielokropka obok nazwy właściwości w siatce właściwości. Spowoduje to otwarcie **edytora wyrażeń** jako okna dialogowego.

## <a name="see-also"></a>Zobacz też
 <xref:System.Activities.Presentation.View.ExpressionTextBox>
