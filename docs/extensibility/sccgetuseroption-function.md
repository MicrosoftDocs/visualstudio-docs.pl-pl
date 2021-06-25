---
description: Ta funkcja pobiera różne opcje specyficzne dla użytkownika.
title: SccGetUserOption, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 622abc04609edf410214af6b8acf795f969e2fbc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901113"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption, funkcja
Ta funkcja pobiera różne opcje specyficzne dla użytkownika.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 nOption (nOption)

[in] Opcja do pobrania (zobacz Uwagi dotyczące możliwych opcji).

 lpVal

[out] Wartość skojarzona z opcją.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Opcja została pomyślnie pobrana.|
|SCC_E_OPNOTSUPPORTED|Opcja nie jest obsługiwana.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Następujące opcje są obsługiwane przez to polecenie:

|Opcja użytkownika|Opis|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce wyewidencjonać lokalną wersję plików. `lpVal` jest przypisany `SCC_USEROPT_COLV_YES` (użytkownik chce wyewidencjonowyć pliki lokalne) lub `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
