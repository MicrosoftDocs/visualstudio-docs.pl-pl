---
title: OPTNAMECHANGEPFN | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702250"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Jest to funkcja wywołania zwrotnego określona w wywołaniu `SCC_OPT_NAMECHANGEPFN` [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji) i służy do przekazywania zmian nazw wprowadzonych przez wtyczkę formantu źródła z powrotem do IDE.

## <a name="signature"></a>Sygnatura

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[w] Wartość użytkownika określona w poprzednim wywołaniu [opcji SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji `SCC_OPT_USERDATA`).

 pszOldName

[w] Oryginalna nazwa pliku.

 pszNewName

[w] Nazwa pliku została zmieniona na.

## <a name="return-value"></a>Wartość zwracana
 Brak.

## <a name="remarks"></a>Uwagi
 Jeśli nazwa pliku zostanie zmieniona podczas operacji kontroli źródła, wtyczka kontroli źródła może powiadomić IDE o zmianie nazwy za pośrednictwem tego wywołania zwrotnego.

 Jeśli IDE nie obsługuje tego wywołania zwrotnego, nie będzie wywoływać [SccSetOption,](../extensibility/sccsetoption-function.md) aby go określić. Jeśli dodatek nie obsługuje tego wywołania zwrotnego, `SCC_E_OPNOTSUPPORTED` `SccSetOption` powróci z funkcji, gdy IDE próbuje ustawić wywołanie zwrotne.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
