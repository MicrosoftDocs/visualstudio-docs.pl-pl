---
title: Konwertowanie metody Get na właściwość i konwersja właściwości na metodę Get
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c5e7cc7be759991647a9bd40415639ab3b08fa1d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056350"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Konwertowanie metody Get na właściwość / skonwertować właściwości refaktoryzacje metody Get

Dotyczą te operacje refaktoryzacji:

- C#

## <a name="convert-get-method-to-property"></a>Konwertowanie metody Get na właściwość

**Co:** umożliwia konwertowanie metody Get na właściwości (i opcjonalnie swoje metody Set).

**Kiedy:** mają metody Get, który nie zawiera żadnych logiki.

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

**Co:** umożliwia konwertowanie właściwości na metodę Get

**Kiedy:** mają właściwość, która obejmuje więcej niż natychmiast ustawiania i pobierania wartości

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