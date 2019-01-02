---
title: Funkcja SccEnumChangedFiles | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 708f8aeff15511a7c1ab877391e0f4ee8449480e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942271"
---
# <a name="sccenumchangedfiles-function"></a>Funkcja SccEnumChangedFiles
Podana lista plików lokalnych, ta funkcja sprawdza pliki, które różnią się od odpowiedniej wersji w bazie danych kontroli kodu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 cFiles  
 [in] Liczby nazw plików określonych w `lpFileNames` tablicy. Również określa rozmiar `plIsFileDifferent` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plik lokalny do sprawdzenia.  
  
 plIsFileDifferent  
 [out w] Tablica wartości wskazujący stan różnica każdego pliku (Tablica musi mieć co najmniej `cFiles` wpisy). Wartość różną od zera oznacza, że plik jest inny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja została ukończona pomyślnie.|  
|SCC_UNSPECIFIEDERROR|Błąd ogólny.|  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)