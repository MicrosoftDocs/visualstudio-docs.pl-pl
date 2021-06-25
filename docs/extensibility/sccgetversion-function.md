---
description: Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli kodu źródłowego obsługiwanego przez wtyczkę kontroli źródła.
title: SccGetVersion, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f49d33ebe70390a364d0ae8336e7f69549b6876f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901087"
---
# <a name="sccgetversion-function"></a>SccGetVersion, funkcja
Ta funkcja pobiera numer wersji interfejsu API wtyczki kontroli kodu źródłowego obsługiwanego przez wtyczkę kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parametry
 Brak.

## <a name="return-value"></a>Wartość zwracana
 Typ `LONG` danych zawierający numer wersji obsługiwanego interfejsu API wtyczki kontroli kodu źródłowego:

|WORD|Opis|
|----------|-----------------|
|HIWORD (HASŁO)|Wersja główna|
|REKORD NISKI|Wersja pomocnicza|

## <a name="remarks"></a>Uwagi
 Jeśli na przykład wtyczka kontroli źródła obsługuje wersję 1.3 interfejsu API wtyczki kontroli kodu źródłowego, ta funkcja zwróci 0x0103.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
