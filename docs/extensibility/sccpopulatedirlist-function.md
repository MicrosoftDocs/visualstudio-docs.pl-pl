---
title: Funkcja SccPopulateDirList | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700553"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
Ta funkcja określa, które katalogi i (opcjonalnie) pliki są przechowywane w kontroli źródła, biorąc pod uwagę listę katalogów do zbadania.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccPopulateDirList(
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

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 nDirs (nDirs)

[w] Liczba ścieżek katalogu w `lpDirPaths` tablicy.

 lpDirPaths (lpDirPaths)

[w] Tablica ścieżek katalogu do zbadania.

 pfnPopuluj

[w] Wywołanie funkcji wywołania dla każdej ścieżki katalogu i (opcjonalnie) nazwy pliku w (szczegóły można znaleźć w `lpDirPaths` polu [POPDIRLISTFUNC).](../extensibility/popdirlistfunc.md)

 pvCallerData

[w] Wartość, która ma być przekazana bez zmian do funkcji wywołania zwrotnego.

 Foptions

[w] Kombinacja wartości, które kontrolują sposób przetwarzania katalogów (zobacz sekcję "Flagi Listy wypełnień" [w bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) dla możliwych wartości).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie zakończono operację.|
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|

## <a name="remarks"></a>Uwagi
 Tylko te katalogi i (opcjonalnie) nazwy plików, które znajdują się w repozytorium kontroli źródła są przekazywane do funkcji wywołania zwrotnego.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Kody błędów](../extensibility/error-codes.md)
