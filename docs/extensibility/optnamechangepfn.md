---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: Dowiedz się więcej o funkcji wywołania zwrotnego OPTNAMECHANGEPFN, która komunikuje zmiany nazw z wtyczki kontroli kodu źródłowego do Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 340012663ad7d21c0b5c2ef81283f5d780d6011c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901529"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Jest to funkcja wywołania zwrotnego określona w wywołaniu [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji ) i służy do przekazywania zmian nazw wprowadzonych przez wtyczkę kontroli źródła z powrotem do `SCC_OPT_NAMECHANGEPFN` środowiska IDE.

## <a name="signature"></a>Podpis

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[in] Wartość użytkownika określona w poprzednim wywołaniu [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji `SCC_OPT_USERDATA` ).

 pszOldName

[in] Oryginalna nazwa pliku.

 pszNewName

[in] Nazwa pliku została zmieniona na .

## <a name="return-value"></a>Wartość zwracana
 Brak.

## <a name="remarks"></a>Uwagi
 Jeśli nazwa pliku zostanie zmieniona podczas operacji kontroli źródła, wtyczka kontroli źródła może powiadomić ideę IDE o zmianie nazwy za pomocą tego wywołania zwrotnego.

 Jeśli idee nie obsługują tego wywołania zwrotnego, nie wywołają [SccSetOption w](../extensibility/sccsetoption-function.md) celu jego określenia. Jeśli wtyczka nie obsługuje tego wywołania zwrotnego, powróci z funkcji, gdy `SCC_E_OPNOTSUPPORTED` `SccSetOption` idee spróbują ustawić wywołanie zwrotne.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego implementowane przez ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
