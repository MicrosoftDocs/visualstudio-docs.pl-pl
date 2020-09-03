---
title: Refaktoryzacja generowania parametrów
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094349"
---
# <a name="generate-parameter"></a>Generowanie parametru

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Automatycznie generuje parametr metody.

**Kiedy:** Odwołanie do zmiennej w metodzie, która nie istnieje w bieżącym kontekście i otrzymywanie błędu; można wygenerować parametr jako poprawkę kodu. 

**Dlaczego:** Możesz szybko zmodyfikować sygnaturę metody bez utraty kontekstu.

## <a name="how-to"></a>Porady

1. Umieść kursor w nazwie zmiennej i naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
1. Wybierz pozycję **Generuj parametr**.

   ![Generowanie parametru](media/generate-parameter.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
