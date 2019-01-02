---
title: POPDIRLISTFUNC | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69278a0faca0d31ae5afbf4b84dbc78efad1bf06
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926203"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Jest to funkcja wywołania zwrotnego do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) funkcję, aby zaktualizować kolekcję katalogów i (opcjonalnie) nazw plików, aby dowiedzieć się, które są pod kontrolą źródła.  
  
 `POPDIRLISTFUNC` Wywołania zwrotnego powinna być wywoływana tylko w przypadku katalogów i nazwy plików (na liście umożliwiającej `SccPopulateDirList` funkcji) rzeczywistości będące pod kontrolą źródła.  
  
## <a name="signature"></a>Podpis  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] Wartość użytkownika do [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 polecenie bOpcje folderów  
 [in] `TRUE` Jeśli nazwy w `lpDirectoryOrFileName` jest katalogiem; w przeciwnym razie nazwa jest nazwą pliku.  
  
 lpDirectoryOrFileName  
 [in] Pełną ścieżkę lokalną do nazwa katalogu lub pliku, który jest pod kontrolą kodu źródłowego.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca kod odpowiedni komunikat o błędzie:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuować przetwarzanie.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Wszelkie błędy kontroli odpowiedniego źródła należy zatrzymać przetwarzanie.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `fOptions` parametru `SccPopulateDirList` funkcja zawiera `SCC_PDL_INCLUDEFILES` Flaga, a następnie zawierać będzie lista prawdopodobnie nazw plików, a także nazwy katalogów.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Kody błędów](../extensibility/error-codes.md)