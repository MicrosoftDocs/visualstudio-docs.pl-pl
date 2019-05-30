---
title: Funkcja SccCloseProject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333935"
---
# <a name="scccloseproject-function"></a>Funkcja SccCloseProject
Ta funkcja powoduje zamknięcie projektu oznaczenia końca określonej sesji.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametry
 pvContext strukturę context wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie zamknięty.|
|SCC_E_PROJNOTOPEN|Projekt nie jest obecnie otwarty.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 [SccOpenProject](../extensibility/sccopenproject-function.md) zawsze jest wywoływany przed tej funkcji. Wywołanie tej funkcji po niej wywołania `SccOpenProject` funkcji lub [SccUninitialize](../extensibility/sccuninitialize-function.md), która całkowicie zakończy połączenie do systemu kontroli źródła.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)