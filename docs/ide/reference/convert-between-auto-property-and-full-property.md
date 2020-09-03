---
title: Konwertowanie między właściwością automatyczną a pełną właściwością
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395413"
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
