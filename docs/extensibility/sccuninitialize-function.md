---
description: Ta funkcja czyści wszelkie alokacje lub otwiera połączenia utworzone przez poprzednie wywołanie do SccInitialize w celu zamknięcia wtyczki kontroli źródła.
title: Funkcja SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 187451aba5151c95d8947bd4f5a1419894cc65e7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221330"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
Ta funkcja czyści wszelkie alokacje lub otwiera połączenia utworzone przez poprzednie wywołanie do [SccInitialize](../extensibility/sccinitialize-function.md) w celu zamknięcia wtyczki kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

podczas Wskaźnik do struktury kontekstu wtyczki kontroli źródła utworzony w [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Czyszczenie zostało ukończone pomyślnie.|

## <a name="remarks"></a>Uwagi
 Wtyczka do kontroli źródła jest odpowiedzialna za przygotowanie się do wyłączenia i zwolnienia pamięci, którą wtyczka przydzieliła dla struktury kontekstu. Funkcja jest wywoływana jednokrotnie dla każdego danego wystąpienia wtyczki. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza to wywołanie. Nie można nadal otwierać projektów w czasie wywołania do `SccUninitialize` .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
