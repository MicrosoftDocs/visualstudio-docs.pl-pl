---
title: Funkcja SccGetExtendedCapabilities | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
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
 Pcontext

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 lSccExCaps

[w] Flaga określająca rozszerzoną możliwość, dla której można przetestować (zobacz tabelę Rozszerzony kod możliwości w [flagi możliwości](../extensibility/capability-flags.md) dla możliwych flag).

 pbSupportowane

[na zewnątrz] Zwraca wartość niezerową (`TRUE`), jeśli obsługiwana jest określona funkcja; w przeciwnym razie`FALSE`zwraca zero ( ).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja get capability została pomyślnie ukończona.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Wystąpił nieznany lub nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana na żądanie; oznacza to, że gdy funkcja musi być testowany, ta metoda jest wywoływana w celu określenia, czy ta funkcja jest obsługiwana. Określono tylko jedną flagę naraz.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
