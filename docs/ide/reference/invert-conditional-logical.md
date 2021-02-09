---
title: Odwracanie wyrażeń warunkowych i operacji logicznych
description: Dowiedz się, jak za pomocą menu szybkie akcje i refaktoryzacje odwrócić wyrażenie warunkowe lub operator warunkowy i/OR.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852248"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Odwróć wyrażenia warunkowe i operatory warunkowe i/OR

To Refaktoryzacja dotyczy:

- C#
- Visual Basic

**Co:** Umożliwia odwracanie wyrażenia warunkowego lub operatora warunkowego i/lub.

**Kiedy:** Istnieje wyrażenie warunkowe lub operator warunkowy i/OR, które byłyby lepiej zrozumiałe w przypadku odwrócenia.

**Dlaczego:** Odwracanie wyrażenia lub operatora warunkowego i/OR przez ręczne może zająć dużo czasu i może spowodować błędy. Ta poprawka kodu ułatwia automatyczne przeprowadzenie tego refaktoryzacji.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Odwróć wyrażenia warunkowe i refaktoryzacje warunkowe i/OR

1. Umieść kursor w wyrażeniu warunkowym lub operator warunkowy i/OR.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz opcję **Odwróć warunkowo** lub **Zastąp element "&&" elementem "| |"**

    ![Zrzut ekranu opcji odwrotnej.](media/invert-conditional.png)

    ![Zrzut ekranu przedstawiający && Zamień na element | | zaznaczyć.](media/invert-logical-operator.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
