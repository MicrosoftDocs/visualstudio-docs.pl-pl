---
title: Konwertuj metodę Pobierz na właściwość; konwertowanie właściwości na Metodę Pobierz
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
ms.openlocfilehash: af507a8b437a20e3d4f4807d582abab6f9a12e27
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094203"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertuj metodę Pobierz na właściwość / Convert właściwość na refaktoryzowania metody Pobierz

Te refaktoryzowania mają zastosowanie do:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Konwertowanie metody Get na właściwość

**Co:** Umożliwia konwertowanie Get metody do właściwości (i opcjonalnie Set metody).

**Kiedy:** Masz Get metody, która nie zawiera żadnej logiki.

### <a name="how-to"></a>Porady

1. Umieść kursor w nazwie metody Pobierz.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybierz polecenie **Zamień metodę właściwością** z okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Zamień metodę właściwością** z okna podglądu.

1. (Opcjonalnie) Jeśli masz set metody, można również przekonwertować set metody w tej chwili, wybierając **Zamień Pobierz metody i Ustaw metodę z właściwością**.

1. Jeśli jesteś zadowolony ze zmiany w podglądzie kodu, naciśnij **klawisz Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

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

## <a name="convert-property-to-get-method"></a>Konwertuj właściwość na metodę Pobierz

**Co:** Umożliwia konwertowanie właściwości na metodę Get

**Kiedy:** Masz właściwość, która obejmuje więcej niż natychmiast ustawienie i uzyskanie wartości

### <a name="how-to"></a>Porady

1. Umieść kursor w nazwie metody Pobierz.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **polecenie Zamień właściwość metodami** z okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Zamień właściwość metodami** z okna podglądu.

1. Jeśli jesteś zadowolony ze zmiany w podglądzie kodu, naciśnij **klawisz Enter** lub kliknij poprawkę z menu, a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
