---
description: Ta funkcja określa, które katalogi i (opcjonalnie) pliki są przechowywane w kontroli źródła, na podstawie listy katalogów do zbadania.
title: SccPopulateDirList, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf2620ff42106be7c858c5104dbf9cb2521252ab
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902361"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
Ta funkcja określa, które katalogi i (opcjonalnie) pliki są przechowywane w kontroli źródła, na podstawie listy katalogów do zbadania.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 nDirs

[in] Liczba ścieżek katalogów w `lpDirPaths` tablicy.

 lpDirPaths

[in] Tablica ścieżek katalogów do zbadania.

 pfnPopulate

[in] Funkcja wywołania zwrotnego do wywołania dla każdej ścieżki katalogu i (opcjonalnie) nazwy pliku w pliku `lpDirPaths` (zobacz [POPDIRLISTFUNC,](../extensibility/popdirlistfunc.md) aby uzyskać szczegółowe informacje).

 pvCallerData

[in] Wartość, która ma zostać przekazana bez zmian do funkcji wywołania zwrotnego.

 Foptions

[in] Kombinacja wartości, które kontrolują sposób przetwarzania katalogów (zobacz sekcję "PopulateDirList flagi" [bitflags](../extensibility/bitflags-used-by-specific-commands.md) używane przez określone polecenia dla możliwych wartości).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie ukończono operację.|
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|

## <a name="remarks"></a>Uwagi
 Tylko te katalogi i (opcjonalnie) nazwy plików, które faktycznie znajdują się w repozytorium kontroli źródła, są przekazywane do funkcji wywołania zwrotnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Kody błędów](../extensibility/error-codes.md)
