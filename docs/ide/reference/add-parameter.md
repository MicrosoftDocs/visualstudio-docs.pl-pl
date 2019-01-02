---
title: Dodaj parametr do metody szybka akcja
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: da435d5bf4e0b7239b984263838c275d3b5c9ab3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920222"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>Dodaj parametr do metody za pomocą szybkich akcji

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** Umożliwia automatyczne dodawanie parametru do metody, na podstawie użycia.

**Kiedy:** Należy dodać parametr do metody i poprawnie Zadeklaruj go automatycznie.

**Dlaczego:** Można dodać parametr do deklaracji metody przed wywołaniem, jednak ta funkcja dodaje go automatycznie na podstawie wywołania metody.

## <a name="how-to-use-it"></a>Jak z niej korzystać

1. Dodaj dodatkowy argument do wywołania metody.

   Czerwony znak "falista" pojawia się w obszarze Nazwa metody, gdy wywołujesz.

2. Umieść wskaźnik myszy na czerwony "falista", aż pojawi się w menu Szybkie akcje. Wybierz **Strzałka w dół** w menu Szybkie akcje, a następnie wybierz **Dodaj parametr do [Metoda]**.

   ![Dodaj parametr do metody szybkich działań w programie Visual Studio](media/add-parameter-to-method.png)

   > [!TIP]
   > Można także uzyskać dostęp w menu Szybkie akcje, umieszczając kursor w wierszu wywołania metody, a następnie albo naciskając **Ctrl**+**.** lub wybierając ikonę żarówki na marginesie pliku.

   Visual Studio dodaje nowy parametr do deklaracji metody.

> [!NOTE]
> W przypadku innych wywołań do metody ich może powodować błędy po użyciu tej szybkiej akcji, ponieważ nie określają argumentu dla parametru nowo dodane.

## <a name="see-also"></a>Zobacz także

- [Dodaj parametr do konstruktora](generate-constructor.md#addparameter)