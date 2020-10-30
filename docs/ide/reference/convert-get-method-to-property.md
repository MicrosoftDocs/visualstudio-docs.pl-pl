---
title: Konwertuj metodę get na lub z właściwości
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad628f8727ed16c882129c5642c77748cb767908
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045778"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertuj metodę get na właściwość/Convert na wartość w celu uzyskania refaktoryzacji metod

Te refaktoryzacji mają zastosowanie do:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Konwertowanie metody Get na właściwość

**Co:** Umożliwia konwertowanie metody get na Właściwość (i opcjonalnie metodę Set).

**Kiedy:** Masz metodę get, która nie zawiera żadnych logiki.

### <a name="how-to"></a>Porady

1. Umieść kursor w nazwie metody get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz opcję **Zastąp metodę z właściwością** w menu podręcznym okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Zastąp metodę z właściwością** w menu podręcznym okna podglądu.

1. Obowiązkowe Jeśli masz metodę Set, możesz również skonwertować metodę Set w tym momencie, wybierając **Zastąp metodę get i Set Method with Property** .

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

### <a name="how-to"></a>Porady

1. Umieść kursor w nazwie metody get.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Zamień właściwość z metodami** w menu podręcznym okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Zamień właściwość z metodami** w menu podręcznym okna podglądu.

1. Jeśli jesteś zadowolony ze zmian w wersji zapoznawczej, naciśnij klawisz **Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
