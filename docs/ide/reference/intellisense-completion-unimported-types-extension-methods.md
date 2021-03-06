---
title: Uzupełnianie IntelliSense dla typów & metod rozszerzenia
description: Jak używać funkcji IntelliSense dla typów i metod rozszerzających, które nie zostały jeszcze zaimportowane do `using` dyrektywy.
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2b73b4d73c36215b70b7551298492e39b69e179f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852339"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Uzupełnianie IntelliSense dla nieimportowanych typów i metod rozszerzających

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Technologia IntelliSense zapewnia uzupełnianie dla nieimportowanych typów i metod rozszerzających.

**Kiedy:** Chcesz użyć typu lub metod rozszerzenia, które mają już zależność w projekcie, ale instrukcja using nie została jeszcze dodana do pliku.

**Dlaczego:** Nie trzeba ręcznie dodawać instrukcji using do pliku.

## <a name="how-to"></a>Porady

1. Po rozpoczęciu wpisywania nazwy typu lub metody rozszerzenia, która ma zależność w projekcie, funkcja IntelliSense udzieli sugestii. Elementy z nieimportowanych przestrzeni nazw byłyby wyświetlane jako sufiksy.

   > [!TIP]
   > Można pokazać/ukryć elementy z nieimportowanych przestrzeni nazw na żądanie przy użyciu **przycisku Ekspander (Alt + A)** , który pojawia się w lewym dolnym rogu listy uzupełniania. Aby zmienić zachowanie domyślne, przejdź do pozycji **Narzędzia**  >  **Opcje**  >  **Edytor tekstu**  >  **C#**  /  **podstawowa**  >  **technologia IntelliSense** i Wyszukaj pozycję **Pokaż elementy z nieimportowanych przestrzeni nazw**.

2. Wybierz i zatwierdź nieimportowany element.

   Instrukcja using zostanie automatycznie dodana do pliku.

   ![Uzupełnianie IntelliSense dla nieimportowanych typów](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Zobacz też

- [Technologia](../using-intellisense.md)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
