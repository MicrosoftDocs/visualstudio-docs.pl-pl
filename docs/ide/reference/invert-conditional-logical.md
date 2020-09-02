---
title: Odwracanie wyrażeń warunkowych i operacji logicznych
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531675"
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

    ![Odwróć warunkowo](media/invert-conditional.png)

    ![Odwróć warunkowo](media/invert-logical-operator.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
