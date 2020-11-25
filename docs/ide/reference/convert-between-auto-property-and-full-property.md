---
title: Konwertowanie między właściwością automatyczną a pełną właściwością
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje do konwersji między właściwością zaimplementowaną i pełną właściwością.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b53f337b538ff1c0aef84272eea7d9e032eb2c1d
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040839"
---
# <a name="convert-between-auto-property-and-full-property"></a>Konwertowanie między właściwością automatyczną a pełną właściwością

To Refaktoryzacja dotyczy:

- C#

**Co:** Konwertuj między właściwością zaimplementowaną na pełną właściwość.

**Kiedy:** Logika właściwości została zmieniona.

**Dlaczego:** Można wykonać konwersję między automatycznie implementowaną właściwością do pełnej właściwości, jednak ta funkcja automatycznie wykonuje tę czynność. 

## <a name="how-to"></a>Porady

1. Umieść kursor na nazwie właściwości.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz jedną z dwóch następujących opcji: 

    Wybierz pozycję **Konwertuj na pełną Właściwość**.

   ![Konwertuj Właściwość autoproperty na Właściwość pełna](media/convert-auto-property-to-full-property.png) 

    Wybierz pozycję **Użyj właściwości autoproperty**. 

    ![Konwertuj pełną właściwość na Właściwość autoproperty](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
