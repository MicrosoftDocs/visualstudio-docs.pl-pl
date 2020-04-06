---
title: POPDIRLISTFUNC | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702077"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego nadana funkcji [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w celu zaktualizowania kolekcji katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.

 Wywołanie zwrotne `POPDIRLISTFUNC` powinno być wywoływane tylko dla tych katalogów `SccPopulateDirList` i nazw plików (na liście podanej funkcji), które są faktycznie pod kontrolą źródła.

## <a name="signature"></a>Sygnatura

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

[w] Wartość użytkownika podana [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[w] `TRUE` jeśli nazwa `lpDirectoryOrFileName` w katalogu jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.

 lpDirectoryOrFileName

[w] Pełna ścieżka lokalna do katalogu lub nazwy pliku, która znajduje się pod kontrolą kodu źródłowego.

## <a name="return-value"></a>Wartość zwracana
 IDE zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Każdy odpowiedni błąd kontroli źródła powinien zatrzymać przetwarzanie.|

## <a name="remarks"></a>Uwagi
 Jeśli `fOptions` parametr `SccPopulateDirList` funkcji zawiera `SCC_PDL_INCLUDEFILES` flagę, lista prawdopodobnie będzie zawierać nazwy plików, a także nazwy katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kody błędów](../extensibility/error-codes.md)
