---
title: POPDIRLISTFUNC, | Microsoft Docs
description: Dowiedz się więcej o funkcji wywołania zwrotnego POPDIRLISTFUNC, która jest przekazywana do katalogów aktualizacji, aby dowiedzieć się, które są pod kontrolą źródła.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c98b35d9f915e16072333c72df2e1e045850f5d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900398"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego nadana funkcji [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w celu zaktualizowania kolekcji katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.

 Wywołanie zwrotne powinno być wywoływane tylko dla katalogów i nazw plików (na liście danej funkcji), które są faktycznie pod `POPDIRLISTFUNC` `SccPopulateDirList` kontrolą źródła.

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

[in] Wartość użytkownika nadana [właściwości SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` Jeśli nazwa w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.

 lpDirectoryOrFileName

[in] Pełna ścieżka lokalna do katalogu lub nazwy pliku, który jest pod kontrolą kodu źródłowego.

## <a name="return-value"></a>Wartość zwracana
 Ide zwraca odpowiedni kod błędu:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuuj przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Wszelkie odpowiednie błędy kontroli źródła powinny przestać przetwarzać.|

## <a name="remarks"></a>Uwagi
 Jeśli parametr funkcji zawiera flagę , lista prawdopodobnie będzie zawierać nazwy `fOptions` `SccPopulateDirList` `SCC_PDL_INCLUDEFILES` plików, a także nazwy katalogów.

## <a name="see-also"></a>Zobacz też
- [Funkcje wywołania zwrotnego implementowane przez ide](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kody błędów](../extensibility/error-codes.md)
