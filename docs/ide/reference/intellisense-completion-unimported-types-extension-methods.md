---
title: Uzupełnianie IntelliSense dla nieimportowanych typów i metod rozszerzających
description: Jak używać funkcji IntelliSense dla typów i metod rozszerzających, które nie zostały jeszcze zaimportowane do `using` dyrektywy.
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d6112bc3894424b9dfd3d060ed390960243b0f98
ms.sourcegitcommit: 4a77403b6bd33c5a6e66a3eefd42c81c39fb67ca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/28/2020
ms.locfileid: "87330988"
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

## <a name="see-also"></a>Zobacz także

- [IntelliSense](../using-intellisense.md)
- [Refaktoryzacja](../refactoring-in-visual-studio.md)
