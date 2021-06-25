---
description: Ta funkcja zamyka projekt, oznaczając koniec określonej sesji.
title: SccCloseProject, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 859b1ddea99e74cc1c1dec999611e50216c3c98a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904698"
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
 pvContext Struktura kontekstu wtyczki kontroli źródła.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Projekt został pomyślnie zamknięty.|
|SCC_E_PROJNOTOPEN|Żaden projekt nie jest obecnie otwarty.|
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|

## <a name="remarks"></a>Uwagi
 Przed tą funkcją zawsze jest wywoływana funkcja [SccOpenProject.](../extensibility/sccopenproject-function.md) Po wywołaniu tej funkcji następuje wywołanie funkcji lub `SccOpenProject` [funkcji SccUninitialize,](../extensibility/sccuninitialize-function.md)która całkowicie kończy połączenie z systemem kontroli źródła.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
