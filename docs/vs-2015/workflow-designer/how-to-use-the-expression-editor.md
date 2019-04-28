---
title: 'Instrukcje: Używanie edytora wyrażeń | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cc876426c18184c966c277e8dafb5a373da332b7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408380"
---
# <a name="how-to-use-the-expression-editor"></a>Instrukcje: Używanie edytora wyrażeń
Edytor wyrażeń jest [!INCLUDE[wfd1](../includes/wfd1-md.md)] formant, który jest używany w wielu działań przepływu pracy jako sposób wprowadzania i tych wyrażeń. Edytora wyrażeń zapewnia w pełni funkcjonalnego środowiska IDE, środowisko, w tym funkcji IntelliSense, edytowania kolorowanie, ParamInfo, między innymi funkcjami zygzaki sygnalizujące błędy. Kompilator sprawdza się wyrażenie po jej wprowadzeniu. Jeśli wyrażenie jest nieprawidłowe, jest wyświetlana ikona błędu. Można również otworzyć Edytor jako **edytora wyrażeń** okno dialogowe.  
  
 Wyrażenia są wartości literałów lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kodu powiązany z argumentami lub właściwości. Zawierają one elementy wartości (np. zmienne, stałe, literały, właściwości), które są połączone z operacjami umożliwiające uzyskanie nową wartość. Wyrażenia są zapisywane przy użyciu składni VB.NET, nawet jeśli aplikacja znajduje się w programie przy użyciu języka C#. Oznacza to, wielkość liter nie ma znaczenia, porównanie odbywa się przy użyciu pojedynczy znak równości ("=") zamiast ("=="), operatory logiczne są wyrazy "i" i "or" zamiast symbole "& &" i "&#124;&#124;", i **nic**  jest używana zamiast **null**. Aby uzyskać więcej informacji na temat wyrażenia i operatory w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i uzyskać kilka przykładów, zobacz [operatory i wyrażenia w języku Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 **Edytora wyrażeń** zachowuje się w następujący sposób:  
  
- Jeśli fokus nie jest w edytorze wyrażeń, wygląda regularne formant TextBlock.  
  
- Gdy fokus jest ustawiony w edytorze wyrażeń, wygląda i zachowuje się jak kontrolka edytora wyrażeń. Po utracie fokusu, it wygląda regularne TextBlock ponownie.  
  
- Jeśli możesz skoncentrować się na edytorze wyrażeń w rehostowanym projektancie przepływu pracy, następnie go zachowuje się jak pole tekstowe. Gdy fokus jest utracone w rehostowanym projektancie przepływu pracy, edytora wyrażeń będzie wyglądać regularne TextBlock ponownie.  
  
> [!NOTE]
> Funkcja IntelliSense edytora wyrażeń jest dostępna tylko wewnątrz elementu [!INCLUDE[vs2010](../includes/vs2010-md.md)]. W obu [!INCLUDE[vs2010](../includes/vs2010-md.md)] i rehostowanym przypadkach kompilator sprawdza poprawność wyrażenia po wprowadzeniu go i Edytor wyrażeń Wyświetla ikonę błędu, jeśli wyrażenie jest nieprawidłowe.  
  
### <a name="using-the-expression-editor"></a>Za pomocą edytora wyrażeń  
  
1. W [!INCLUDE[vs2010](../includes/vs2010-md.md)], otwórz projekt nowego lub istniejącego przepływu pracy.  
  
2. Dodaj na przykład <xref:System.Activities.Statements.Assign> działania przepływu pracy.  
  
    > [!NOTE]
    > Wiele działań przepływu pracy ma edytory wyrażenia. Obiekty wyrażeń TextBlock również zostać wyświetlony w Projektancie zmiennej, projektanta argumentów i projektanta argumentów dynamicznych. <xref:System.Activities.Statements.Assign> To działanie służy jako przykład.  
  
3. Kliknij przycisk edytora wyrażeń po lewej stronie, w Projektancie działań dla <xref:System.Activities.Statements.Assign> działania.  
  
     Parametry szare znaku wodnego  **\<do >** i  **\<wprowadź wyrażenie VB >** są domyślne, ciągi tekstowe edytory wyrażenia w <xref:System.Activities.Statements.Assign> działania.  
  
4. Wprowadź wyrażenie. Jeśli wprowadzisz ciąg, upewnij się umieścić ciąg w cudzysłowie. Jeśli chcesz powiązać argumentu wyrażenia do zmiennej, należy pozostawić znaki cudzysłowu.  
  
     Gdy wszystko będzie gotowe, wybierz region lub obszar, aby przenieść fokus do innej części projektanta poza edytora wyrażeń. To spowoduje, że kompilator, aby sprawdzić poprawność wyrażenia, zgodnie z wcześniejszym opisem.  
  
     Alternatywny sposób, aby wprowadzić/Edytuj wyrażenie jest kliknij wielokropek obok nazwy właściwości w siatce właściwości. Spowoduje to otwarcie **edytora wyrażeń** jako okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>