---
description: Ta funkcja zwraca dodatkowe możliwości obsługiwane przez wtyczkę kontroli źródła.
title: Funkcja SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1409753559088c0f8129ebacd17387bfb7d111e
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220784"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities, funkcja
Ta funkcja zwraca dodatkowe możliwości obsługiwane przez wtyczkę kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parametry
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 lSccExCaps

podczas Flaga określająca rozszerzoną funkcję, która ma zostać przetestowana (zobacz tabelę kodu możliwości rozszerzonej w [flagach możliwości](../extensibility/capability-flags.md) dla możliwych flag).

 pbSupported

określoną Zwraca wartość różną od zera ( `TRUE` ), jeśli określona funkcja jest obsługiwana; w przeciwnym razie zwraca wartość zero ( `FALSE` ).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja pobrania możliwości została ukończona pomyślnie.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Wystąpił nieznany lub nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana na żądanie; oznacza to, że w przypadku potrzeby przetestowania możliwości ta metoda jest wywoływana w celu ustalenia, czy ta funkcja jest obsługiwana. Określono tylko jedną flagę w danym czasie.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
