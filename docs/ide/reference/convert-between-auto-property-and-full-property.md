---
title: Konwersja między właściwością auto a pełną właściwością
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395413"
---
# <a name="convert-between-auto-property-and-full-property"></a>Konwersja między właściwością auto a pełną właściwością

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Konwertuj między właściwością automatycznie zaimplementowane na pełną właściwość.

**Kiedy:** Logika właściwości uległa zmianie.

**Dlaczego?** Można ręcznie przekonwertować między właściwością zaimplementowane automatycznie na pełną właściwość, jednak ta funkcja automatycznie wykona pracę za Ciebie. 

## <a name="how-to"></a>Porady

1. Umieść kursor na nazwie właściwości.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz jedną z następujących dwóch opcji: 

    Wybierz **opcję Konwertuj na pełną właściwość**.

   ![Konwertowanie właściwości auto na pełną właściwość](media/convert-auto-property-to-full-property.png) 

    Wybierz **pozycję Użyj właściwości auto**. 

    ![Konwertowanie pełnej właściwości na właściwość auto](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
