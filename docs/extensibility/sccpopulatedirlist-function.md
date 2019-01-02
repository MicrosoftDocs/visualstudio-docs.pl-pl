---
title: Funkcja SccPopulateDirList | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 477d18f3cb5f187b61d78d779339e2c43c402a43
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854740"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
Ta funkcja określa, które pliki i katalogi (opcjonalnie) są przechowywane w kontroli źródła, biorąc pod uwagę listę katalogów do sprawdzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccPopulateDirList(  
   LPVOID        pContext,  
   LONG          nDirs,  
   LPCSTR*       lpDirPaths,  
   POPDIRLISTFUNCpfnPopulate,  
   LPVOID        pvCallerData,  
   LONG          fOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 nDirs  
 [in] Liczba ścieżek katalogów w `lpDirPaths` tablicy.  
  
 lpDirPaths  
 [in] Tablica ścieżek katalogów do sprawdzenia.  
  
 pfnPopulate  
 [in] Funkcja wywołania zwrotnego do wywołania dla każdej ścieżki katalogu i (opcjonalnie) Nazwa pliku w `lpDirPaths` (zobacz [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Aby uzyskać szczegółowe informacje).  
  
 pvCallerData  
 [in] Niezmieniona wartość, która zostanie przekazany do funkcji wywołania zwrotnego.  
  
 fOptions  
 [in] Kombinacja wartości, które kontrolują, jak są przetwarzane katalogów (zobacz sekcję "PopulateDirList flags" [flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) uzyskać odpowiednie wartości).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko te katalogi i (opcjonalnie) nazw plików, które są rzeczywiście repozytorium kontroli źródła są przekazywane do funkcji wywołania zwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Flagi bitowe używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Kody błędów](../extensibility/error-codes.md)