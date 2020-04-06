---
title: Funkcja SccBackgroundGet | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701229"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet, funkcja
Ta funkcja pobiera ze źródła kontrolę każdego z określonych plików bez interakcji użytkownika.

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

[w] Wskaźnik kontekstu wtyczki formantu źródła.

 nFiles

[w] Liczba plików określonych `lpFileNames` w tablicy.

 lpFileNames

[w, na zewnątrz] Tablica nazw plików do pobrania.

> [!NOTE]
> Nazwy muszą być w pełni kwalifikowanymi lokalnymi nazwami plików.

 Dwflags

[w] Flagi poleceń (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).

 dwBackgroundOperationID

[w] Unikatowa wartość skojarzona z tą operacją.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Operacja została zakończona pomyślnie.|
|SCC_E_BACKGROUNDGETINPROGRESS|Pobieranie w tle jest już w toku (wtyczka kontroli źródła powinna zwracać to tylko wtedy, gdy nie obsługuje jednoczesnych operacji wsadowych).|
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed zakończeniem.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest zawsze wywoływana na wątku innym niż ten, który załadował wtyczkę formantu źródła. Ta funkcja nie powinien wrócić, dopóki nie zostanie wykonana; Jednak można go nazwać wiele razy z wieloma listami plików, wszystkie w tym samym czasie.

 Użycie argumentu `dwFlags` jest taka sama jak [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
