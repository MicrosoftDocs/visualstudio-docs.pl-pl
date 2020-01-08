---
title: Konwertuj metodę get na Właściwość; Konwertuj właściwość na metodę get
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 6e3807f3902cbd0d2718f249f15cd268fb81ac51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570235"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertowanie metody Get na właściwość / skonwertować właściwości refaktoryzacje metody Get

Dotyczą te operacje refaktoryzacji:

- Język C#

## <a name="convert-get-method-to-property"></a>Konwertowanie metody Get na właściwość

**Co:** umożliwia konwertowanie metody Get na właściwości (i opcjonalnie swoje metody Set).

**Kiedy:** mają metody Get, który nie zawiera żadnych logiki.

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zastąpić metodę z właściwością** z menu podręcznego okna podglądu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zastąpić metodę z właściwością** z menu podręcznego okna podglądu.

1. (Opcjonalnie) W przypadku metody Set można także przekonwertować swoje metody Set w tym momencie, wybierając **metody Get Zastąp i metody Set z właściwością**.

1. Jeśli jesteś zadowolony z zmiany w wersji zapoznawczej kodu, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

Przykład:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Konwertowanie właściwości na metodę Get

**Co:** umożliwia konwertowanie właściwości na metodę Get

**Kiedy:** mają właściwość, która obejmuje więcej niż natychmiast ustawiania i pobierania wartości

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zamień właściwości metody** z menu podręcznego okna podglądu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zamień właściwości metody** z menu podręcznego okna podglądu.

1. Jeśli jesteś zadowolony z zmiany w wersji zapoznawczej kodu, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
