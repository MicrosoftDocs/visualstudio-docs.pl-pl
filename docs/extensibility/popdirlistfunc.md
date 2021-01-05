---
title: POPDIRLISTFUNC | Microsoft Docs
description: Dowiedz się więcej na temat funkcji wywołania zwrotnego POPDIRLISTFUNC, która jest przenoszona do katalogów aktualizacji, aby dowiedzieć się, które znajdują się pod kontrolą źródła.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 805d7a5c9250bc511692c497bc9083852dad2301
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863451"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego nadana funkcji [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w celu zaktualizowania kolekcji katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które znajdują się pod kontrolą źródła.

 `POPDIRLISTFUNC`Wywołanie zwrotne powinno być wywoływane tylko dla tych katalogów i nazw plików (znajdujących się na liście `SccPopulateDirList` funkcji), które faktycznie podlegają kontroli źródła.

## <a name="signature"></a>Podpis

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parametry
 pvCallerData

podczas Wartość użytkownika nadana [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[w] `TRUE` Jeśli nazwa w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.

 lpDirectoryOrFileName

podczas Pełna ścieżka lokalna do katalogu lub nazwy pliku, który znajduje się pod kontrolą kodu źródłowego.

## <a name="return-value"></a>Wartość zwracana
 IDE zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Każdy odpowiedni błąd kontroli źródła powinien zatrzymać przetwarzanie.|

## <a name="remarks"></a>Uwagi
 Jeśli `fOptions` parametr `SccPopulateDirList` funkcji zawiera `SCC_PDL_INCLUDEFILES` flagę, lista będzie prawdopodobnie zawierać nazwy plików, a także nazwy katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kody błędów](../extensibility/error-codes.md)
