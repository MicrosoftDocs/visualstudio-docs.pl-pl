---
title: Funkcja SccBackgroundGet | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae32f7b0c9eea907c830a3cc62e0e53e87803177
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826880"
---
# <a name="sccbackgroundget-function"></a>Funkcja SccBackgroundGet
Ta funkcja pobiera z kontroli źródła każdego określonych plików bez interakcji użytkownika.  
  
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
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [out w] Tablica nazwy plików do pobrania.  
  
> [!NOTE]
>  Nazwy muszą być w pełni kwalifikowanej nazwy lokalnego.  
  
 Flagidw  
 [in] Polecenie flagi (`SCC_GET_ALL`, `SCC_GET_RECURSIVE`).  
  
 dwBackgroundOperationID  
 [in] Unikatowa wartość skojarzonego z tą operacją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_E_BACKGROUNDGETINPROGRESS|Pobieranie w tle jest już w toku (wtyczka do kontroli źródła powinna zwrócić to tylko wtedy, gdy nie obsługuje operacji wsadowych jednocześnie).|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończenie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja zawsze jest wywoływana w wątku, inny niż ten, który załadowany wtyczka do kontroli źródła. Ta funkcja nie powinien zwrócić, dopóki zakończy działania; jednak może ona zostać wywołana wiele razy przy użyciu wielu list plików, wszystko w tym samym czasie.  
  
 Korzystanie z `dwFlags` argument jest taka sama jak [SccGet](../extensibility/sccget-function.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)