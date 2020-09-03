---
title: Funkcja SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71df385bc0cf42c2437abfd117c2f84bda5b5432
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701050"
---
# <a name="scccloseproject-function"></a>SccCloseProject, funkcja
Ta funkcja zamyka projekt, zaznaczając koniec określonej sesji.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametry
 pvContext strukturę kontekstu wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie zamknięty.|
|SCC_E_PROJNOTOPEN|Żaden projekt nie jest obecnie otwarty.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 [SccOpenProject](../extensibility/sccopenproject-function.md) jest zawsze wywoływana przed tą funkcją. Po wywołaniu tej funkcji następuje wywołanie `SccOpenProject` funkcji lub [SccUninitialize](../extensibility/sccuninitialize-function.md), co spowoduje całkowite zakończenie połączenia z systemem kontroli źródła.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
