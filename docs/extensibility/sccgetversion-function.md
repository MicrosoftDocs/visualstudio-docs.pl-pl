---
title: Funkcja SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721480"
---
# <a name="sccgetversion-function"></a>SccGetVersion, funkcja
Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli źródła obsługiwanego przez wtyczkę kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 @No__t_0 typ danych, który zawiera numer wersji obsługiwanego interfejsu API Plug-in kontroli źródła:

|WORD|Opis|
|----------|-----------------|
|HIWORD|Wersja główna|
|LOWORD|Wersja pomocnicza|

## <a name="remarks"></a>Uwagi
 Na przykład jeśli wtyczka do kontroli źródła obsługuje wersję 1,3 interfejsu API dodatku plug-in kontroli źródła, ta funkcja zwróci 0x0103.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)