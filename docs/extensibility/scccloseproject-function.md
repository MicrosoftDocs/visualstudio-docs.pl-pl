---
title: Funkcja SccCloseProject | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701050"
---
# <a name="scccloseproject-function"></a>SccCloseProject, funkcja
Ta funkcja zamyka projekt, oznaczając koniec określonej sesji.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametry
 pvContext Struktura kontekstu wtyczki formantu źródła.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie zamknięty.|
|SCC_E_PROJNOTOPEN|Żaden projekt nie jest obecnie otwarty.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 [SccOpenProject](../extensibility/sccopenproject-function.md) jest zawsze wywoływana przed tą funkcją. Po wywołaniu tej funkcji następuje wywołanie `SccOpenProject` funkcji lub [SccUninitialize](../extensibility/sccuninitialize-function.md), które całkowicie kończy połączenie z systemem kontroli źródła.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
