---
description: Ta funkcja sprawdza, czy wtyczka kontroli źródła umożliwia wyewidencjonowanie wielu plików.
title: SccIsMultiCheckoutEnabled, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b9fc81a20e3a8078a2d4cebbc6a8db10c2e2e49
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902517"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled, funkcja
Ta funkcja sprawdza, czy wtyczka kontroli źródła umożliwia wyewidencjonowanie wielu plików.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[in] Struktura kontekstu wtyczki kontroli źródła.

 pbMultiCheckout

[out] Określa, czy dla tego projektu włączono wiele wyewidencjonowań (niezerowe oznacza, że wiele wyewidencjonowań jest obsługiwanych).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Sprawdzenie powiodło się.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Ide wykonuje dwa testy, aby określić, czy pliki mogą być wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze system kontroli źródła musi obsługiwać wiele wyewidencjonowań. Wtyczka kontroli źródła może określić tę możliwość podczas inicjowania, określając `SCC_CAP_MULTICHECKOUT` . Następnie, w ramach drugiego sprawdzenia, ide wywołuje tę funkcję, aby określić, czy bieżący projekt obsługuje wiele wyewidencjonowań. Jeśli dla wybranego projektu jest obsługiwanych wiele wyewidencjonowań, wtyczka zwraca kod powodzenia i ustawia wartość `pbMultiCheckout` niezerową ( `TRUE` ) lub `FALSE` .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
