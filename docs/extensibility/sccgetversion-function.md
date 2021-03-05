---
description: Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli źródła obsługiwanego przez wtyczkę kontroli źródła.
title: Funkcja SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a71d3374ffd65e0e7b9a7b2e654885d84e370a9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220602"
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
 `LONG`Typ danych, który zawiera numer wersji obsługiwanego interfejsu API Plug-in kontroli źródła:

|WORD|Opis|
|----------|-----------------|
|HIWORD|Wersja główna|
|LOWORD|Wersja pomocnicza|

## <a name="remarks"></a>Uwagi
 Na przykład jeśli wtyczka do kontroli źródła obsługuje wersję 1,3 interfejsu API dodatku plug-in kontroli źródła, ta funkcja zwróci 0x0103.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
