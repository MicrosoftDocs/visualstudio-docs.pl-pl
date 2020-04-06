---
title: Funkcja SccEndBatch | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700923"
---
# <a name="sccendbatch-function"></a>SccEndBatch, funkcja
Ta funkcja kończy serię operacji kontroli źródła. Te partie nie mogą być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Partia operacji została pomyślnie zakończona.|
|SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji kontroli źródła w wielu projektach lub wielu kontekstach. Partie mogą służyć do wyeliminowania nadmiarowych okien dialogowych z środowiska użytkownika podczas operacji wsadowej. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i `SccEndBatch` funkcja są używane jako para, aby wskazać początek i koniec operacji. Nie można ich zagnieździć.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
