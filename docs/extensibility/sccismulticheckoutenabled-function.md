---
title: Funkcja SccIsMultiCheckoutEnabled | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700584"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled, funkcja
Ta funkcja sprawdza, czy wtyczka kontroli źródła umożliwia wiele wyewidencjonowania w pliku.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[w] Struktura kontekstu wtyczki formantu źródła.

 pbMultiCheckout

[na zewnątrz] Określa, czy dla tego projektu jest włączonych wiele wyewidencjonowania (wartość niezerowa oznacza, że obsługiwane są wiele wyewidencjonowanych transakcji).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Kontrola zakończyła się pomyślnie.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 IDE sprawia, że dwa kontrole, aby ustalić, czy pliki mogą być wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze, system kontroli źródła musi obsługiwać wiele wyewidencjonowania. Wtyczka formantu źródła może określić tę możliwość `SCC_CAP_MULTICHECKOUT`podczas inicjowania, określając program . Następnie jako drugi check IDE wywołuje tę funkcję, aby ustalić, czy bieżący projekt obsługuje wiele wyewidencjonowania. Jeśli dla wybranego projektu obsługiwanych jest wiele wyewidencjonowania, `pbMultiCheckout` wtyczka zwraca`TRUE`kod `FALSE`sukcesu i ustawia wartość niezerowa ( ) lub .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
