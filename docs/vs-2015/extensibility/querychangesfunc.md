---
title: QUERYCHANGESFUNC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cca0b3ce30ece454567db25dca1f950098f39d8d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917282"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jest to funkcja wywołania zwrotnego używane przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operację, aby wyliczyć Kolekcja nazw plików i ustalić stan każdego pliku.  
  
 `SccQueryChanges` Funkcji znajduje się lista plików i wskaźnik do `QUERYCHANGESFUNC` wywołania zwrotnego. Wtyczka do kontroli źródła wylicza za pośrednictwem danej listy i zawiera stan (za pośrednictwem tego wywołania zwrotnego) dla każdego pliku na liście.  
  
## <a name="signature"></a>Podpis  
  
```cpp#  
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
  
```cpp#  
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
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Kody błędów](../extensibility/error-codes.md)

