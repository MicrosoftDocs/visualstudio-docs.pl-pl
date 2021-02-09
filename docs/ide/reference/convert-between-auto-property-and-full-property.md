---
title: Konwertowanie między właściwością automatyczną a pełną właściwością
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje do konwersji między właściwością zaimplementowaną i pełną właściwością.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907597"
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
