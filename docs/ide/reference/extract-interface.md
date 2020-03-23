---
title: Wyodrębnianie refaktoryzacji interfejsu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595673"
---
# <a name="extract-an-interface-refactoring"></a>Wyodrębnianie refaktoryzacji interfejsu

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia utworzenie interfejsu przy użyciu istniejących elementów członkowskich z klasy, struktury lub interfejsu.

**Kiedy:** Masz członków w klasie, struktury lub interfejsu, które mogą być dziedziczone przez inne klasy, struktury lub interfejsów.

**Dlaczego?** Interfejsy są świetnymi konstrukcjami dla projektów obiektowych. Wyobraź sobie, że masz zajęcia dla różnych zwierząt (Pies, Kot, Ptak), które mogą mieć wspólne metody, takie jak Jeść, Pić, Spać. Przy pomocy an złącze standardowe podobny IAnimal byłby uznawać Pies, Kot, i Ptak wobec mieć pewien wspólny " podpis" pod kątem tych metody.

## <a name="extract-an-interface-refactoring"></a>Wyodrębnianie refaktoryzacji interfejsu

1. Umieść kursor w nazwie klasy.

   - C#:

       ![Wyróżniony kod - C #](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/extractinterface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl+R**, a następnie **klawisze Ctrl+I**. (Skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **opcję Wyodrębnij interfejs** z okna podglądu.
   - **Mysz**
      - Wybierz **pozycję Edytuj > refaktoryzatora > interfejs wyodrębniania**.
      - Kliknij prawym przyciskiem myszy nazwę klasy, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Wyodrębnij interfejs** z okna podglądu.

3. W oknie dialogowym **Wyodrębnianie interfejsu,** które się pojawia, wprowadź żądane informacje:

   ![Wyodrębnij interface](media/extractinterface-dialog-same-file.png)

   | Pole | Opis |
   | - | - |
   | **Nowa nazwa interfejsu** | Nazwa interfejsu, który ma zostać utworzony. Nazwa domyślnie ma wartość I*ClassName*, gdzie *Nazwa klasy* jest nazwą klasy wybranej powyżej. |
   | **Nowa nazwa pliku** | Nazwa wygenerowanego pliku, który będzie zawierał interfejs. Podobnie jak w przypadku nazwy interfejsu, ta nazwa będzie domyślnie I*ClassName*, gdzie *ClassName* jest nazwą klasy wybranej powyżej. Można również wybrać opcję **Dodaj do bieżącego pliku**. |
   | **Wybieranie elementów członkowskich do utworzenia interfejsu** | Elementy, które mają być wyodrębnione do interfejsu. Możesz wybrać dowolną liczbę. |

4. Wybierz pozycję **OK**.

   Interfejs jest tworzony w pliku o określonej nazwie. Ponadto wybrana klasa implementuje ten interfejs.

   - C#:

      ![Klasa wynikowa - C #](media/extractinterface-class-cs.png)

      ![Wynikowy interfejs - C #](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Wynikowa klasa — visual basic](media/extractinterface-class-vb.png)

      ![Wynikowy interfejs — Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
