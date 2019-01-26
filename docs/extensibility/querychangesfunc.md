---
title: QUERYCHANGESFUNC | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d281de537d55fad74538df9ed34efc662acaab0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037034"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Jest to funkcja wywołania zwrotnego używane przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operację, aby wyliczyć Kolekcja nazw plików i ustalić stan każdego pliku.  
  
 `SccQueryChanges` Funkcji znajduje się lista plików i wskaźnik do `QUERYCHANGESFUNC` wywołania zwrotnego. Wtyczka do kontroli źródła wylicza za pośrednictwem danej listy i zawiera stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.  
  
## <a name="signature"></a>Podpis  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] `pvCallerData` Parametr przekazany przez wywołującego (IDE) do [SccQueryChanges](../extensibility/sccquerychanges-function.md). Wtyczka do kontroli źródła, powinien zawierać żadnych założeń dotyczących zawartości tej wartości.  
  
 pChangesData  
 [in] Wskaźnik do [struktury QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) struktury, opisująca zmiany w pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 IDE zwraca kod odpowiedni komunikat o błędzie:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Kontynuować przetwarzanie.|  
|SCC_I_OPERATIONCANCELED|Zatrzymaj przetwarzanie.|  
|SCC_E_xxx|Wszelkie odpowiedni komunikat o błędzie SCC należy zatrzymać przetwarzanie.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> Struktura QUERYCHANGESDATA  
 Struktura przekazane dla każdego pliku wygląda podobnie do poniższego:  
  
```cpp  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 niezerowego  
 Rozmiar tej struktury (w bajtach).  
  
 lpFileName  
 Oryginalna nazwa pliku dla tego elementu.  
  
 dwChangeType  
 Kod, wskazujący stan pliku:  
  
|Kod|Opis|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Nie wiadomo, co zmieniło się.|  
|`SCC_CHANGE_UNCHANGED`|Bez zmian nazw dla tego pliku.|  
|`SCC_CHANGE_DIFFERENT`|Plik z różnych tożsamości, ale takiej samej nazwie istnieje w bazie danych.|  
|`SCC_CHANGE_NONEXISTENT`|Plik nie istnieje w bazie danych lub lokalnie.|  
|`SCC_CHANGE_DATABASE_DELETED`|Plik został usunięty z bazy danych.|  
|`SCC_CHANGE_LOCAL_DELETED`|Plik został usunięty lokalnie, ale plik nadal istnieje w bazie danych. Jeśli nie można ustalić, zwracają `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Plik dodane do bazy danych, ale nie istnieje lokalnie.|  
|`SCC_CHANGE_LOCAL_ADDED`|Plik nie istnieje w bazie danych i jest plikiem lokalnym.|  
|`SCC_CHANGE_RENAMED_TO`|Plik przeniesiony lub w bazie danych jako `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Plik przeniesiony lub z bazy danych z `lpLatestName`; Jeśli jest to zbyt kosztowne śledzić, zwracają różne flagi, takich jak `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Bieżąca nazwa pliku dla tego elementu.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Kody błędów](../extensibility/error-codes.md)