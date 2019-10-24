---
title: Funkcja SccPopulateDirList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720894"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
Ta funkcja określa, które katalogi i (opcjonalnie) pliki są przechowywane w kontroli źródła, z uwzględnieniem listy katalogów do sprawdzenia.

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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nDirs

podczas Liczba ścieżek katalogów w tablicy `lpDirPaths`.

 lpDirPaths

podczas Tablica ścieżek katalogów do sprawdzenia.

 pfnPopulate

podczas Funkcja wywołania zwrotnego do wywołania dla każdej ścieżki katalogu i (opcjonalnie) filename w `lpDirPaths` (zobacz [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) , aby uzyskać szczegółowe informacje).

 pvCallerData

podczas Wartość, która ma zostać przeniesiona bez zmian do funkcji wywołania zwrotnego.

 fOptions

podczas Kombinacja wartości kontrolujących sposób przetwarzania katalogów (zobacz sekcję "flagi PopulateDirList" [Bitflags używanych przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) dla możliwych wartości).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie ukończono operację.|
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|

## <a name="remarks"></a>Uwagi
 Tylko te katalogi i (opcjonalnie) nazwy plików, które faktycznie znajdują się w repozytorium kontroli źródła są przesyłane do funkcji wywołania zwrotnego.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Kody błędów](../extensibility/error-codes.md)