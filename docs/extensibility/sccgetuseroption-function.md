---
description: Ta funkcja pobiera różne opcje specyficzne dla użytkownika.
title: Funkcja SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 262a15069f840c048f574396d5a7ec076760d77e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063958"
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
 pContext

podczas Wskaźnik kontekstu wtyczki kontroli źródła.

 nOption

podczas Opcja pobrania (Zobacz uwagi dotyczące możliwych opcji).

 lpVal

określoną Wartość skojarzona z opcją.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pomyślnie pobrano opcję.|
|SCC_E_OPNOTSUPPORTED|Opcja nie jest obsługiwana.|
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Następujące opcje są obsługiwane przez to polecenie:

|Opcja użytkownika|Opis|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce wyewidencjonować lokalną wersję plików. `lpVal` jest przypisany `SCC_USEROPT_COLV_YES` (użytkownik chce wyewidencjonować pliki lokalne) lub `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [Kody błędów](../extensibility/error-codes.md)
