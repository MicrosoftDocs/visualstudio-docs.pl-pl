---
title: Dodawanie parametru do metody szybka akcja
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6720421fd5188688214665d85de682542b1c1357
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595868"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Dodawanie parametru do metody przy użyciu szybkiej akcji

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia automatyczne dodawanie parametru do metody na podstawie użycia.

**Kiedy:** Należy dodać parametr do metody i chcesz poprawnie zadeklarować go automatycznie.

**Dlaczego?** Można dodać parametr do deklaracji metody przed wywołaniem go, jednak ta funkcja dodaje go automatycznie na podstawie wywołania metody.

## <a name="how-to-use-it"></a>Korzystanie

1. Dodaj dodatkowy argument do wywołania metody.

   Czerwony squiggle pojawia się pod nazwą metody, w której go wywołasz.

2. Umieść wskaźnik myszy na czerwonym fali, aż pojawi się menu Szybkie akcje. Zaznacz **strzałkę w dół** w menu Szybkie akcje, a następnie wybierz polecenie **Dodaj parametr do [method]**.

   ![Dodawanie parametru do metody szybkiej akcji w programie Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Dostęp do menu Szybkie akcje można również uzyskać, umieszczając kursor w wierszu wywołania metody, a następnie naciskając klawisz **Ctrl**+**.** (kropka) lub wybranie ikony żarówki na marginesie pliku.

   Visual Studio dodaje nowy parametr do deklaracji metody.

> [!NOTE]
> Jeśli masz inne wywołania metody, mogą one powodować błędy po użyciu tej szybkiej akcji, ponieważ nie określają one argument dla nowo dodanego parametru.

## <a name="see-also"></a>Zobacz też

- [Dodawanie parametru do konstruktora](generate-constructor.md#addparameter)
