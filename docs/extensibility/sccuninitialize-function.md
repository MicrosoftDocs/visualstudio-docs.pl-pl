---
title: Funkcja SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720130"
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
 Wtyczka do kontroli źródła jest odpowiedzialna za przygotowanie się do wyłączenia i zwolnienia pamięci, którą wtyczka przydzieliła dla struktury kontekstu. Funkcja jest wywoływana jednokrotnie dla każdego danego wystąpienia wtyczki. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza to wywołanie. W czasie wywołania do `SccUninitialize` nie można nadal otwierać projektów.

## <a name="see-also"></a>Zobacz także
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)