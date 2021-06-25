---
description: Ta funkcja pobiera z kontroli źródła każdy z określonych plików bez interakcji z użytkownikiem.
title: SccBackgroundGet, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 316a02e84b4d51f309aecdd98d0409c85ccbdbef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901243"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet, funkcja
Ta funkcja pobiera z kontroli źródła każdy z określonych plików bez interakcji z użytkownikiem.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parametry
 Pcontext

[in] Wskaźnik kontekstu wtyczki kontroli źródła.

 nFiles

[in] Liczba plików określona w `lpFileNames` tablicy.

 lpFileNames

[in, out] Tablica nazw plików do pobrania.

> [!NOTE]
> Nazwy muszą być w pełni kwalifikowane lokalne nazwy plików.

 Dwflags

[in] Flagi poleceń ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

[in] Unikatowa wartość skojarzona z tą operacją.

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła dla tej funkcji zwraca jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została zakończona pomyślnie.|
|SCC_E_BACKGROUNDGETINPROGRESS|Pobieranie w tle jest już w toku (wtyczka kontroli źródła powinna zwracać ją tylko wtedy, gdy nie obsługuje równoczesnych operacji wsadowych).|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest zawsze wywoływana w wątku innym niż ten, który załadował wtyczkę kontroli źródła. Ta funkcja nie zostanie zwrócona, dopóki nie zostanie wykonana. Jednak może być wywoływana wiele razy z wieloma listami plików, a wszystko to w tym samym czasie.

 Użycie argumentu `dwFlags` jest takie samo jak [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
