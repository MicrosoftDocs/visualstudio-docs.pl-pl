---
description: Ta funkcja kończy partię operacji kontroli źródła.
title: SccEndBatch, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ff596f19d3a98b929f9346bbf579e0ad1258c5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904594"
---
# <a name="sccendbatch-function"></a>SccEndBatch, funkcja
Ta funkcja kończy partię operacji kontroli źródła. Te partie mogą nie być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie ukończono partię operacji.|
|SCC_E_UNKNOWNERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonywania tych samych operacji kontroli źródła w wielu projektach lub w wielu kontekstach. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych ze strony użytkownika podczas operacji wsadowych. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i funkcja są używane jako para, aby wskazać `SccEndBatch` początek i koniec operacji. Nie mogą być zagnieżdżone.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
