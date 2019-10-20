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
ms.openlocfilehash: 6157646526a2d634ff5034d98eb497c00585c067
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659101"
---
# <a name="how-to-use-the-expression-editor"></a>Instrukcje: korzystanie z edytora wyrażeń
Edytor wyrażeń jest formantem [!INCLUDE[wfd1](../includes/wfd1-md.md)], który jest używany w wielu działaniach przepływu pracy jako sposób wprowadzania i oceniania tych wyrażeń. Edytor wyrażeń zawiera dopracowane środowisko edycji środowiska IDE, w tym funkcje IntelliSense, kolorowanie, ParamInfo, zygzaki błędów, między innymi. Kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu. Jeśli wyrażenie jest nieprawidłowe, zostanie wyświetlona ikona błędu. Edytor można także otworzyć jako okno dialogowe **Edytor wyrażeń** .

 Wyrażenia są wartościami literałów lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodzie związanym z argumentami lub właściwościami. Zawierają one elementy wartości (np. zmienne, stałe, literały, właściwości), które są łączone z operacjami w celu uzyskania nowej wartości. Wyrażenia są zapisywane przy użyciu składni VB.NET, nawet jeśli aplikacja znajduje się w programie C#przy użyciu. Oznacza to, że nie ma znaczenia, porównanie jest wykonywane przy użyciu pojedynczego znaku równości ("="), a nie ("= ="), operatory logiczne to słowa "i" i "lub" zamiast symboli "& &" i "&#124;&#124;", a **niczego nie** są używane zamiast **wartości null**. Aby uzyskać więcej informacji na temat wyrażeń i operatorów w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i dla niektórych przykładów, zobacz [Operatory i wyrażenia w Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 **Edytor wyrażeń** zachowuje się w następujący sposób:

- Jeśli fokus nie znajduje się w edytorze wyrażeń, wygląda jak zwykła kontrolka TextBlock.

- Gdy fokus znajduje się w edytorze wyrażeń, wygląda i zachowuje się jak kontrolka Edytor wyrażeń. Po utracie fokusu będzie on wyglądał jak zwykły element TextBlock.

- W przypadku fokusu w edytorze wyrażeń w Projektancie przepływu pracy przeprowadzonej ponownie zachowuje się to jak pole tekstowe. Gdy fokus zostanie utracony w Projektancie przepływów pracy, Edytor wyrażeń będzie wyglądał jak zwykły element TextBlock.

> [!NOTE]
> Funkcja IntelliSense dla edytora wyrażeń jest dostępna tylko wewnątrz [!INCLUDE[vs2010](../includes/vs2010-md.md)]. W przypadku [!INCLUDE[vs2010](../includes/vs2010-md.md)] i scenariuszy rehostowania kompilator sprawdza poprawność wyrażenia po jego wprowadzeniu, a w edytorze wyrażeń jest wyświetlana ikona błędu, jeśli wyrażenie jest nieprawidłowe.

### <a name="using-the-expression-editor"></a>Korzystanie z edytora wyrażeń

1. W [!INCLUDE[vs2010](../includes/vs2010-md.md)] Otwórz nowy lub istniejący projekt przepływu pracy.

2. Dodaj na przykład działanie <xref:System.Activities.Statements.Assign> do przepływu pracy.

    > [!NOTE]
    > Wiele działań przepływu pracy ma edytory wyrażeń. Bloki tekstu wyrażenia są również wyświetlane w projektancie zmiennych, projektancie argumentów i projektancie argumentów dynamicznych. Działanie <xref:System.Activities.Statements.Assign> jest używane jako przykład.

3. Kliknij Edytor wyrażeń lewy w projektancie działań dla działania <xref:System.Activities.Statements.Assign>.

     Ciągi szarego znaku wodnego **\<To >** i **\<Enter wyrażeniem VB >** są domyślnymi ciągami tekstowymi dla edytorów wyrażeń w działaniu <xref:System.Activities.Statements.Assign>.

4. Wprowadź wyrażenie. Jeśli wprowadzisz ciąg, upewnij się, że zostały umieszczone cudzysłowy wokół ciągu. Jeśli wybierzesz powiązanie argumentu wyrażenia z zmienną, pozostaw cudzysłowy.

     Gdy wszystko będzie gotowe, wybierz region lub obszar poza edytorem wyrażeń, aby przenieść fokus do innej części projektanta. Spowoduje to, że kompilator sprawdzi poprawność wyrażenia zgodnie z wcześniejszym opisem.

     Alternatywny sposób wprowadzania/edytowania wyrażenia polega na kliknięciu wielokropka obok nazwy właściwości w siatce właściwości. Spowoduje to otwarcie **edytora wyrażeń** jako okna dialogowego.

## <a name="see-also"></a>Zobacz też
 <xref:System.Activities.Presentation.View.ExpressionTextBox>