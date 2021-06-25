---
description: Ta funkcja zwraca dodatkowe możliwości obsługiwane przez wtyczkę kontroli źródła.
title: SccGetExtendedCapabilities, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc047fee2c92f47c181aef455b8175a4e7998176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905595"
---
# <a name="sccgetextendedcapabilities-function"></a>Funkcja SccGetExtendedCapabilities
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

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 lSccExCaps

[in] Flaga określająca rozszerzoną możliwość do testowania (zobacz tabelę Extended Capability Code (Kod możliwości rozszerzonych) w [teście Capability flags (Flagi](../extensibility/capability-flags.md) możliwości), aby uzyskać informacje o możliwych flagach.

 pbSupported

[out] Zwraca wartość niezerową `TRUE` (), jeśli określona możliwość jest obsługiwana. W przeciwnym razie zwraca wartość zero ( `FALSE` ).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja pobierz możliwość została ukończona pomyślnie.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Wystąpił nieznany lub nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana na żądanie; oznacza to, że gdy trzeba przetestować możliwość, ta metoda jest wywoływana w celu określenia, czy ta możliwość jest obsługiwana. W tym samym czasie jest określona tylko jedna flaga.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
- [Flagi możliwości](../extensibility/capability-flags.md)
