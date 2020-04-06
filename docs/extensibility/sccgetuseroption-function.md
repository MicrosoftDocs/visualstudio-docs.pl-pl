---
title: Funkcja SccGetUserOption | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700686"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption, funkcja
Ta funkcja pobiera wiele opcji specyficznych dla użytkownika.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Parametry
 Pcontext

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 nOpcja

[w] Opcja pobierania (zobacz Uwagi dotyczące możliwych opcji).

 lpVal (ł.

[na zewnątrz] Wartość skojarzona z opcją.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Opcja została pobrana pomyślnie.|
|SCC_E_OPNOTSUPPORTED|Opcja nie jest obsługiwana.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Następujące opcje są obsługiwane przez to polecenie:

|Opcja użytkownika|Opis|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce wyewidencjonować lokalną wersję plików. `lpVal``SCC_USEROPT_COLV_YES` (użytkownik chce wyewidencjonować pliki `SCC_USEROPT_COLV_NO`lokalne) lub .|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
