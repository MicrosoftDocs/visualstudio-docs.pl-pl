---
title: Wyodrębnianie refaktoryzacji interfejsu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 15da8bdf1a3df60a7ad4816ce578ec5672c85ecf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654413"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnianie refaktoryzacji interfejsu

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia utworzenie interfejsu przy użyciu istniejących członków z klasy, struktury lub interfejsu.

**Kiedy:** Istnieją elementy członkowskie klasy, struktury lub interfejsu, które mogą być dziedziczone przez inne klasy, struktury lub interfejsy.

**Dlaczego:** Interfejsy są doskonałymi konstrukcjami dla projektów zorientowanych obiektowo. Wyobraź sobie, że klasy dla różnych zwierząt (Dog, Cat, ptak), które mogą mieć wszystkie typowe metody, takie jak Eat, napoje, uśpienie. Użycie interfejsu, takiego jak IAnimal, zezwoli na dostęp do tych metod dla psów, Cat i ptaka.

## <a name="extract-an-interface-refactoring"></a>Wyodrębnianie refaktoryzacji interfejsu

1. Umieść kursor w nazwie klasy.

   - C#:

       ![Wyróżniony kod —C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/extractinterface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij **klawisze CTRL + R**, a następnie **Ctrl + I**. (Skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** , a następnie wybierz pozycję **Wyodrębnij interfejs** w oknie podręcznym okna podglądu.
   - **Wskaźnik**
      - Wybierz pozycję **edytuj > refaktoryzacja > Wyodrębnij interfejs**.
      - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Wyodrębnij interfejs** z menu podręcznego okna podglądu.

3. W oknie dialogowym **wyodrębnianie interfejsu** , które się pojawi, wprowadź wymagane informacje:

   ![Wyodrębnij interface](media/extractinterface-dialog-same-file.png)

   | Pole | Opis |
   | - | - |
   | **Nazwa nowego interfejsu** | Nazwa interfejsu, który ma zostać utworzony. Nazwa będzie domyślnie równa I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranej powyżej. |
   | **Nowa nazwa pliku** | Nazwa wygenerowanego pliku, który będzie zawierać interfejs. Podobnie jak w przypadku nazwy interfejsu, ta nazwa będzie domyślnie równa I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranej powyżej. Możesz również wybrać opcję, która ma zostać **dodana do bieżącego pliku**. |
   | **Wybierz publiczne elementy członkowskie do interfejsu formularza** | Elementy do wyodrębnienia do interfejsu. Możesz wybrać dowolną liczbę. |

4. Wybierz **przycisk OK**.

   Interfejs jest tworzony w pliku o podanej nazwie. Ponadto wybrana Klasa implementuje ten interfejs.

   - C#:

      ![Klasa będąca wynikiemC#](media/extractinterface-class-cs.png)

      ![Interfejs wynikającyC#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Klasa będąca wynikiem Visual Basic](media/extractinterface-class-vb.png)

      ![Interfejs uzyskany Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
