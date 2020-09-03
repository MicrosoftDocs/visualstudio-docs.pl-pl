---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194052"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jest to funkcja wywołania zwrotnego nadana funkcji [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) w celu zaktualizowania kolekcji katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które znajdują się pod kontrolą źródła.  
  
 `POPDIRLISTFUNC`Wywołanie zwrotne powinno być wywoływane tylko dla tych katalogów i nazw plików (znajdujących się na liście `SccPopulateDirList` funkcji), które faktycznie podlegają kontroli źródła.  
  
## <a name="signature"></a>Podpis  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 podczas Wartość użytkownika nadana [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [w] `TRUE` Jeśli nazwa w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.  
  
 lpDirectoryOrFileName  
 podczas Pełna ścieżka lokalna do katalogu lub nazwy pliku, który znajduje się pod kontrolą kodu źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca odpowiedni kod błędu:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuuj przetwarzanie.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Każdy odpowiedni błąd kontroli źródła powinien zatrzymać przetwarzanie.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `fOptions` parametr `SccPopulateDirList` funkcji zawiera `SCC_PDL_INCLUDEFILES` flagę, lista będzie prawdopodobnie zawierać nazwy plików, a także nazwy katalogów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowane przez IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Kody błędów](../extensibility/error-codes.md)
