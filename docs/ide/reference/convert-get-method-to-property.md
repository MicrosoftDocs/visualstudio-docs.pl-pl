---
title: Konwertuj metodę get na Właściwość; Konwertuj właściwość na metodę get
ms.date: 01/26/2018
ms.topic: reference
ms.devlang: csharp
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ac33db013a8cea11b373e4104bf2d58a1b22cef4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654522"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertuj metodę get na właściwość/Convert na wartość w celu uzyskania refaktoryzacji metod

Te refaktoryzacji mają zastosowanie do:

- C#

## <a name="convert-get-method-to-property"></a>Konwertuj metodę get na Właściwość

**Co:** Umożliwia konwertowanie metody get na Właściwość (i opcjonalnie metodę Set).

**Kiedy:** Masz metodę get, która nie zawiera żadnych logiki.

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz opcję **Zastąp metodę z właściwością** w menu podręcznym okna podglądu.
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zastąp metodę z właściwością** w menu podręcznym okna podglądu.

1. Obowiązkowe Jeśli masz metodę Set, możesz również skonwertować metodę Set w tym momencie, wybierając **Zastąp metodę get i Set Method with Property**.

1. Jeśli jesteś zadowolony ze zmian w wersji zapoznawczej, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

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

## <a name="convert-property-to-get-method"></a>Konwertuj właściwość na metodę get

**Co:** Umożliwia przekonwertowanie właściwości na metodę get

**Kiedy:** Masz właściwość, która obejmuje więcej niż natychmiastowe ustawienie i pobieranie wartości

### <a name="how-to"></a>Instrukcje

1. Umieść kursor w nazwie metody get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Zamień właściwość z metodami** w menu podręcznym okna podglądu.
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Zamień właściwość z metodami** w menu podręcznym okna podglądu.

1. Jeśli jesteś zadowolony ze zmian w wersji zapoznawczej, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)