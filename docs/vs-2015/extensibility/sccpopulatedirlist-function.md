---
title: Funkcja SccPopulateDirList | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6078f0fd90855c432b333fd5967367460d0a364e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200022"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja określa, które katalogi i (opcjonalnie) pliki są przechowywane w kontroli źródła, z uwzględnieniem listy katalogów do sprawdzenia.  
  
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
 podczas Wskaźnik kontekstu wtyczki kontroli źródła.  
  
 nDirs  
 podczas Liczba ścieżek katalogów w `lpDirPaths` tablicy.  
  
 lpDirPaths  
 podczas Tablica ścieżek katalogów do sprawdzenia.  
  
 pfnPopulate  
 podczas Funkcja wywołania zwrotnego do wywołania dla każdej ścieżki katalogu i (opcjonalnie) filename w `lpDirPaths` (zobacz [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) , aby uzyskać szczegółowe informacje).  
  
 pvCallerData  
 podczas Wartość, która ma zostać przeniesiona bez zmian do funkcji wywołania zwrotnego.  
  
 fOptions  
 podczas Kombinacja wartości kontrolujących sposób przetwarzania katalogów (zobacz sekcję "flagi PopulateDirList" [Bitflags używanych przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md) dla możliwych wartości).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pomyślnie ukończono operację.|  
|SCC_E_UNKNOWNERROR|Wystąpił błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko te katalogi i (opcjonalnie) nazwy plików, które faktycznie znajdują się w repozytorium kontroli źródła są przesyłane do funkcji wywołania zwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags używane przez określone polecenia](../extensibility/bitflags-used-by-specific-commands.md)   
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)   
 [Kody błędów](../extensibility/error-codes.md)
