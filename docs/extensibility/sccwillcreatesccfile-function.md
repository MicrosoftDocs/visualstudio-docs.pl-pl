---
title: SccWillCreateSccFile Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b629b83aa329a4a3e25197236e33ee152e378472
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937210"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
Ta funkcja sprawdza, czy wtyczka do kontroli źródła obsługuje tworzenie MSSCCPRJ. Plik SCC dla każdego danego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 Niepowodzeń  
 [in] Liczba nazwy plików zawarte w `lpFileNames` tablicy, a także długość `pbSccFiles` tablicy.  
  
 lpFileNames  
 [in] Tablicy w pełni kwalifikowanych nazw do sprawdzenia (tablicy muszą być przydzielane przez wywołującego).  
  
 pbSccFiles  
 [out w] Tablica do przechowywania wyników.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Powodzenie.|  
|SCC_E_INVALIDFILEPATH|Jedna ze ścieżek używanych w tablicy jest nieprawidłowa.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana z listą plików w celu określenia, jeśli wtyczka do kontroli źródła zapewnia obsługę w MSSCCPRJ. Plik SCC dla każdego z plików danego (Aby uzyskać więcej informacji na temat MSSCCPRJ. Plik SCC zobacz [MSSCCPRJ. Plik SCC](../extensibility/mssccprj-scc-file.md)). Wtyczki kontroli źródła można zadeklarować, czy ma on możliwość tworzenia MSSCCPRJ. Pliki SCC przez zadeklarowanie `SCC_CAP_SCCFILE` podczas inicjowania. Zwraca wtyczki `TRUE` lub `FALSE` każdego pliku `pbSccFiles` tablicy, aby określić, które pliki danego ma MSSCCPRJ. Obsługa SCC. Jeśli wtyczka zwróci kod powodzenia z funkcji, wartości w tablicy zwracanej są uznawane. W przypadku awarii tablica jest ignorowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)