---
title: Funkcja SccWillCreateSccFile | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147960"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja sprawdza, czy wtyczka do kontroli źródła obsługuje tworzenie MSSCCPRJ. Plik SCC dla każdego danego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
