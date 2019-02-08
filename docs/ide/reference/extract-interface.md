---
title: Wyodrębnianie interfejsu Refaktoryzacja
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bc10a43cc5834453e6c5e11e1c7b787903f24c06
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909183"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnianie interfejsu Refaktoryzacja

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia utworzenie interfejsu przy użyciu istniejących członków z klasy, struktury lub interfejsu.

**Kiedy:** Istnieje kilka klasy, struktury lub interfejsy z metod, które można ustanowić typowe i używane przez inne klasy, struktury lub interfejsów.

**Dlaczego:** Interfejsy są doskonałe konstrukcje projekty zorientowane obiektowo. Wyobraź sobie, mających klasy dla różnych zwierząt (psów i kotów, Bird), które mogą mieć typowych metod, takich jak Eat, napoju, usypiania/budzenia. Przy użyciu interfejsu, takich jak IAnimal pozwoliłoby pies, Cat i Bird mają wspólne "signature" dotyczącej tych metod.

## <a name="how-to"></a>Instrukcje

1. Wyróżnij nazwę klasy, aby wykonać akcji lub po prostu gdzieś umieścić kursor tekstu w nazwie klasy.

   - C#:

       ![Wyróżniony kod-C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/extractinterface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + I**. (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Wyodrębnij interfejs**.
      - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz opcję **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.

3. W **Wyodrębnij interfejs** okno dialogowe, które się pojawi, wprowadź informacje monit:

   ![Wyodrębnij interface](media/extractinterface-dialog-cs.png)


   | Pole | Opis |
   | - | - |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. To domyślnie zostanie I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranego powyżej. |
   | **Nowa nazwa pliku** | Nazwa pliku, który zostanie wygenerowany i który będzie zawierał interfejsu. Zgodnie z nazwą interfejsu, to domyślnie zostanie I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranego powyżej. |
   | **Wybierz publiczne elementy członkowskie do interfejsu formularza** | Elementy, które można wyodrębnić w interfejsie. Można wybrać dowolną liczbę, jak chcesz. |


4. Wybierz **OK**.

   Gdy interfejs został utworzony w pliku o nazwie określonej. Ponadto klasy, którą wybrano implementuje ten interfejs.

   - C#:

      ![Klasa wynikowa — C# ](media/extractinterface-class-cs.png) ![wynikowy interfejs —C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Klasa wynikowa — języka Visual Basic](media/extractinterface-class-vb.png) ![wynikowy interfejs - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)