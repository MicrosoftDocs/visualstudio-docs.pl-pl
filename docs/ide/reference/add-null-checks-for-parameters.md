---
title: Dodaj sprawdzanie wartości null dla wszystkich (parametrów)
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782308"
---
# <a name="add-null-checks-for-all-parameters"></a>Dodawanie kontroli pod kątem wartości null dla wszystkich parametrów 

To Refaktoryzacja dotyczy: 

- Język C# 

**Co:** Tworzy i dodaje instrukcje `if`, które sprawdzają wartość null wszystkich niesprawdzonych parametrów. 

**Kiedy:** Chcesz szybko dodać sprawdzanie wartości null dla wszystkich odpowiednich parametrów metody.

**Dlaczego:** Pisanie czeków null dla wielu parametrów może być czasochłonne i powtarzane. Korzystanie z tego refaktoryzacji jest szybkie i sprawia, że program jest bardziej niezawodny.  

## <a name="how-to"></a>Instrukcje 

1. Umieść kursor na dowolnym parametrze w metodzie.

2. Naciśnij klawisz **Ctrl**+ **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Szybkie akcje i refaktoryzacje](media/add-null-checks-for-all-parameters.png)
   
3. Wybierz opcję, aby **dodać sprawdzanie wartości null dla wszystkich parametrów**.

   ![Dodaj sprawdzanie wartości null dla wszystkich](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Zobacz także 

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
