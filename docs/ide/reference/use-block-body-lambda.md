---
title: Używanie wyrażenia lambda lub treści bloku
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531916"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Użyj treści wyrażenia lub treści bloku dla wyrażeń lambda

To Refaktoryzacja dotyczy:

- C#

**Co:** Umożliwia refaktoryzację wyrażenia lambda, aby użyć treści wyrażenia lub treści bloku.

**Kiedy:** Preferuj wyrażenia lambda, aby użyć treści wyrażenia lub treści bloku.

**Dlaczego:** Wyrażenia lambda można refaktoryzację, aby zwiększyć czytelność zgodnie z preferencjami użytkownika.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Treść wyrażenia lambda lub Refaktoryzacja treści bloku

1. Umieść kursor po prawej stronie operatora lambda.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

  ![Użyj wyrażenia lambda/treści bloku](media/block-body-lambda.png)

3. Wybierz opcję **Użyj treści bloku dla wyrażeń lambda** lub **Użyj treści wyrażenia dla wyrażeń lambda**.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)