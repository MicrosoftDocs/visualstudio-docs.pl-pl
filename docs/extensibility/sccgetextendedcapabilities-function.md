---
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700722"
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
