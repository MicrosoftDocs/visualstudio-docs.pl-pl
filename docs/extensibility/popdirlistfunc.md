---
title: POPDIRLISTFUNC | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fef3ab783c736fd2573e8d9df1a513e25d37020
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326134"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funkcję, aby zaktualizować kolekcję katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.

 `POPDIRLISTFUNC` Wywołania zwrotnego powinna być wywoływana tylko w przypadku katalogów i nazwy plików (na liście umożliwiającej `SccPopulateDirList` funkcji) rzeczywistości będące pod kontrolą źródła.

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

[in] Wartość użytkownika do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` Jeśli nazwy w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.

 lpDirectoryOrFileName

[in] Pełną ścieżkę lokalną do nazwa katalogu lub pliku, który jest pod kontrolą kodu źródłowego.

## <a name="return-value"></a>Wartość zwracana
 IDE zwraca kod odpowiedni komunikat o błędzie:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontynuować przetwarzanie.|
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|
|SCC_E_xxx|Wszelkie błędy kontroli odpowiedniego źródła należy zatrzymać przetwarzanie.|

## <a name="remarks"></a>Uwagi
 Jeśli `fOptions` parametru `SccPopulateDirList` funkcja zawiera `SCC_PDL_INCLUDEFILES` Flaga, a następnie zawierać będzie lista prawdopodobnie nazw plików, a także nazwy katalogów.

## <a name="see-also"></a>Zobacz także
- [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Kody błędów](../extensibility/error-codes.md)