---
title: Funkcja SccEndBatch | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e915a2e0c508e62a8d34d8d8a5b4fdcd734bbf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353690"
---
# <a name="sccendbatch-function"></a>Funkcja SccEndBatch
Ta funkcja kończy partię operacji kontroli źródła. Partie te nie mogą być zagnieżdżone.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Wsadowe operacji, które pomyślnie zakończone.|
|SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Partie kontroli źródła są używane do wykonania tych samych operacji kontroli źródła, między wieloma projektami lub wieloma kontekstów. Partie można wyeliminować nadmiarowy okien dialogowych z interfejsu użytkownika podczas operacji wsadowej. [SccBeginBatch](../extensibility/sccbeginbatch-function.md) i `SccEndBatch` do wskazywania początek i koniec operacji służą jako para funkcji. Nie można zagnieżdżać ich.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)