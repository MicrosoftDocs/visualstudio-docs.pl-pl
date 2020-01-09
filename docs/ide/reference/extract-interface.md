---
title: Wyodrębnianie interfejsu Refaktoryzacja
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5055f50d07cf9362c9be1bdc8135e31240a7cc66
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595673"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnianie interfejsu Refaktoryzacja

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

**Co:** Umożliwia utworzenie interfejsu przy użyciu istniejących członków z klasy, struktury lub interfejsu.

**Kiedy:** Istnieją elementy członkowskie klasy, struktury lub interfejsu, które mogą być dziedziczone przez inne klasy, struktury lub interfejsy.

**Dlaczego:** interfejsy są doskonałe konstrukcje projekty zorientowane obiektowo. Wyobraź sobie, mających klasy dla różnych zwierząt (psów i kotów, Bird), które mogą mieć typowych metod, takich jak Eat, napoju, usypiania/budzenia. Przy użyciu interfejsu, takich jak IAnimal pozwoliłoby pies, Cat i Bird mają wspólne "signature" dotyczącej tych metod.

## <a name="extract-an-interface-refactoring"></a>Wyodrębnianie interfejsu Refaktoryzacja

1. Umieść kursor w nazwie klasy.

   - C#:

       ![Wyróżniony kod-C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/extractinterface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + I**. (Skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Wyodrębnij interfejs**.
      - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz opcję **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij interfejs** z menu podręcznego okna podglądu.

3. W **Wyodrębnij interfejs** okno dialogowe, które się pojawi, wprowadź informacje monit:

   ![Wyodrębnij interface](media/extractinterface-dialog-same-file.png)

   | Pole | Opis |
   | - | - |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. Nazwa będzie domyślnie równa I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranej powyżej. |
   | **Nowa nazwa pliku** | Nazwa wygenerowanego pliku, który będzie zawierać interfejs. Podobnie jak w przypadku nazwy interfejsu, ta nazwa będzie domyślnie równa I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranej powyżej. Możesz również wybrać opcję, która ma zostać **dodana do bieżącego pliku**. |
   | **Wybierz publiczne elementy członkowskie do interfejsu formularza** | Elementy, które można wyodrębnić w interfejsie. Można wybrać dowolną liczbę, jak chcesz. |

4. Wybierz **OK**.

   Gdy interfejs został utworzony w pliku o nazwie określonej. Ponadto klasy, którą wybrano implementuje ten interfejs.

   - C#:

      ![Klasa będąca wynikiemC#](media/extractinterface-class-cs.png)

      ![Interfejs wynikającyC#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Klasa będąca wynikiem Visual Basic](media/extractinterface-class-vb.png)

      ![Interfejs uzyskany Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
