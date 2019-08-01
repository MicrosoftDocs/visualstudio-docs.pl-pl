---
title: Dodaj sprawdzanie wartości null dla wszystkich (parametrów)
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68713347"
---
# <a name="add-null-checks-for-all-parameters"></a>Dodaj sprawdzanie wartości null dla wszystkich parametrów 

Ta Refaktoryzacja mają zastosowanie do: 

- C# 

**Whatman** Tworzy i dodaje `if` instrukcje, które sprawdzają wartość null wszystkich niesprawdzonych parametrów. 

**Czasie** Chcesz szybko dodać sprawdzanie wartości null dla wszystkich odpowiednich parametrów metody.

**Zalet** Pisanie czeków null dla wielu parametrów może być czasochłonne i powtarzane. Korzystanie z tego refaktoryzacji jest szybkie i sprawia, że program jest bardziej niezawodny.  

## <a name="how-to"></a>Instrukcje 

1. Umieść kursor na dowolnym parametrze w metodzie.

2. Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   ![Szybkie akcje i refaktoryzacje](media/add-null-checks-for-all-parameters.png)
   
3. Wybierz opcję, aby **dodać sprawdzanie wartości null dla wszystkich parametrów**.

   ![Dodaj sprawdzanie wartości null dla wszystkich](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Zobacz także 

- [Refaktoryzacja](../refactoring-in-visual-studio.md) 
