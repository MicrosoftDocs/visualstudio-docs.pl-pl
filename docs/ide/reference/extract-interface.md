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
ms.openlocfilehash: 261ddf457ad117812be9971b630c2fcd3b75b550
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651304"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnianie interfejsu Refaktoryzacja

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia utworzenie interfejsu przy użyciu istniejących członków z klasy, struktury lub interfejsu.

**Kiedy:** Masz członków klasy, struktury lub interfejsu, który może być dziedziczona przez inne klasy, struktury lub interfejsów.

**Dlaczego:** Interfejsy są doskonałe konstrukcje projekty zorientowane obiektowo. Wyobraź sobie, mających klasy dla różnych zwierząt (psów i kotów, Bird), które mogą mieć typowych metod, takich jak Eat, napoju, usypiania/budzenia. Przy użyciu interfejsu, takich jak IAnimal pozwoliłoby pies, Cat i Bird mają wspólne "signature" dotyczącej tych metod.

## <a name="extract-an-interface-refactoring"></a>Wyodrębnianie interfejsu Refaktoryzacja

1. Umieść kursor w polu Nazwa klasy.

   - C#:

       ![Wyróżniony kod-C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/extractinterface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + I**. (Skrót klawiaturowy mogą być inne niż oparte na profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Wyodrębnij interfejs**.
      - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz opcję **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.

3. W **Wyodrębnij interfejs** okno dialogowe, które się pojawi, wprowadź informacje monit:

   ![Wyodrębnij interface](media/extractinterface-dialog-same-file.png)

   | Pole | Opis |
   | - | - |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. Nazwy będą domyślnie I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranego powyżej. |
   | **Nowa nazwa pliku** | Nazwę wygenerowanego pliku, który będzie zawierał interfejsu. Zgodnie z nazwą interfejsu, ta nazwa domyślnie I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranego powyżej. Można również wybrać opcję, aby **dodać do bieżącego pliku**. |
   | **Wybierz publiczne elementy członkowskie do interfejsu formularza** | Elementy, które można wyodrębnić w interfejsie. Można wybrać dowolną liczbę, jak chcesz. |

4. Wybierz **OK**.

   Gdy interfejs został utworzony w pliku o nazwie określonej. Ponadto klasy, którą wybrano implementuje ten interfejs.

   - C#:

      ![Klasa wynikowa —C#](media/extractinterface-class-cs.png)

      ![Wynikowy interfejs —C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Klasa wynikowa — języka Visual Basic](media/extractinterface-class-vb.png)

      ![Interfejs wynikowy - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
