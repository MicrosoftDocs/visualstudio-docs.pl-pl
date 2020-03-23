---
title: Dodawanie wartości null dla wszystkich (parametrów)
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782308"
---
# <a name="add-null-checks-for-all-parameters"></a>Dodawanie kontroli pod kątem wartości null dla wszystkich parametrów 

Ten refaktoryzator ma zastosowanie do: 

- C# 

**Co:** Tworzy i `if` dodaje instrukcje, które sprawdzają nieważność wszystkich niepodjętych, nieczekanych parametrów. 

**Kiedy:** Chcesz szybko dodać null kontroli dla wszystkich parametrów metody odpowiednie.

**Dlaczego?** Zapisywanie kontroli zerowych dla wielu parametrów może być czasochłonne i powtarzalne. Korzystanie z tego refaktoryzacji jest szybkie i sprawia, że program jest bardziej niezawodny.  

## <a name="how-to"></a>Porady 

1. Umieść kursor na dowolnym parametrze w metodzie.

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Szybkie akcje i refaktoryzowania](media/add-null-checks-for-all-parameters.png)
   
3. Wybierz opcję **Dodaj wartości null dla wszystkich parametrów**.

   ![Dodaj czeki zerowe dla wszystkich](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Zobacz też 

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
