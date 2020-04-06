---
title: Funkcja SccGetVersion | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700674"
---
# <a name="sccgetversion-function"></a>SccGetVersion, funkcja
Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli źródła obsługiwane przez wtyczkę kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Typ `LONG` danych zawierający numer wersji obsługiwanego interfejsu API wtyczki kontroli źródła:

|WORD|Opis|
|----------|-----------------|
|Hiword ( HIWORD )|Wersja główna|
|LOWORD ( LOWORD )|Wersja pomocnicza|

## <a name="remarks"></a>Uwagi
 Na przykład jeśli wtyczka kontroli źródła obsługuje wersję 1.3 interfejsu API dodatku dodatku Dodatku Kontroli źródła, ta funkcja zwróci 0x0103.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
