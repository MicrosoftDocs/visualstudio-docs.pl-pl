---
title: OPTNAMECHANGEPFN | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702250"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Jest to funkcja wywołania zwrotnego określona w wywołaniu [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji `SCC_OPT_NAMECHANGEPFN` ) i służy do przekazywania zmian nazw dokonanych przez wtyczkę kontroli źródła z powrotem do IDE.

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

podczas Wartość użytkownika określona w poprzednim wywołaniu [SccSetOption](../extensibility/sccsetoption-function.md) (opcja using `SCC_OPT_USERDATA` ).

 pszOldName

podczas Oryginalna nazwa pliku.

 pszNewName

podczas Nazwa pliku, do którego zmieniono nazwę.

## <a name="return-value"></a>Wartość zwracana
 Brak.

## <a name="remarks"></a>Uwagi
 Jeśli nazwa pliku została zmieniona podczas operacji kontroli źródła, wtyczka do kontroli źródła może powiadomić IDE o zmianie nazwy za pomocą tego wywołania zwrotnego.

 Jeśli IDE nie obsługuje tego wywołania zwrotnego, nie wywoła [SccSetOption](../extensibility/sccsetoption-function.md) , aby go określić. Jeśli wtyczka nie obsługuje tego wywołania zwrotnego, nastąpi powrót `SCC_E_OPNOTSUPPORTED` z funkcji, `SccSetOption` gdy IDE podejmie próbę ustawienia wywołania zwrotnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
