---
title: Dodaj sprawdzanie wartości null dla wszystkich (parametrów)
description: Dowiedz się, jak tworzyć i dodawać instrukcje if do kodu, który sprawdza wartość null wszystkich niesprawdzonych parametrów.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870966"
---
# <a name="add-null-checks-for-all-parameters"></a>Dodawanie kontroli pod kątem wartości null dla wszystkich parametrów 

To Refaktoryzacja dotyczy: 

- C# 

**Co:** Tworzy i dodaje `if` instrukcje, które sprawdzają wartość null wszystkich niesprawdzonych parametrów. 

**Kiedy:** Chcesz szybko dodać sprawdzanie wartości null dla wszystkich odpowiednich parametrów metody.

**Dlaczego:** Pisanie czeków null dla wielu parametrów może być czasochłonne i powtarzane. Korzystanie z tego refaktoryzacji jest szybkie i sprawia, że program jest bardziej niezawodny.  

## <a name="how-to"></a>Porady 

1. Umieść kursor na dowolnym parametrze w metodzie.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Szybkie akcje i refaktoryzacje](media/add-null-checks-for-all-parameters.png)
   
3. Wybierz opcję, aby **dodać sprawdzanie wartości null dla wszystkich parametrów**.

   ![Dodaj sprawdzanie wartości null dla wszystkich](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Zobacz także 

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
