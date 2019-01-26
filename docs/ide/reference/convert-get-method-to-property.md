---
title: Konwertowanie metody Get na właściwość i konwersja właściwości na metodę Get
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bd3e534aec6ca1a8bbebfb5e1437d13e97d36e70
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990956"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertowanie metody Get na właściwość / skonwertować właściwości refaktoryzacje metody Get

Dotyczą te operacje refaktoryzacji:

- C#

## <a name="convert-get-method-to-property"></a>Konwertowanie metody Get na właściwość

**Co:** Umożliwia konwertowanie metody Get na właściwości (i opcjonalnie swoje metody Set).

**Kiedy:** Masz metody Get, który nie zawiera żadnych logiki.

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **zastąpić metodę z właściwością** z menu podręcznego okna podglądu.
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

**Co:** Służy do konwertowania właściwości na metodę Get

**Kiedy:** Ma właściwość, która obejmuje więcej niż natychmiast ustawiania i pobierania wartości

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody Get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zamień właściwości metody** z menu podręcznego okna podglądu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zamień właściwości metody** z menu podręcznego okna podglądu.

1. Jeśli jesteś zadowolony z zmiany w wersji zapoznawczej kodu, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)