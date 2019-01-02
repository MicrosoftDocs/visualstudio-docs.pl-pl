---
title: Funkcja SccAdd | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fc2b74b32c0fb90a578644df0065e24eb8e373f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830907"
---
# <a name="sccadd-function"></a>Funkcja SccAdd
Ta funkcja dodaje nowe pliki do systemu kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Niepowodzeń  
 [in] Liczba plików wybranych do dodania do bieżącego projektu, jak podano `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica z w pełni kwalifikowane nazwy lokalnych plików do dodania.  
  
 lpComment  
 [in] Komentarz, który ma zostać zastosowany do wszystkich plików dodawane.  
  
 pfOptions  
 [in] Tablica flag poleceń, podane na zasadzie każdego pliku.  
  
 pvOptions  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja Dodaj zakończyła się pomyślnie.|  
|SCC_E_FILEALREADYEXISTS|Wybrany plik jest już pod kontrolą źródła.|  
|SCC_E_TYPENOTSUPPORTED|Typ pliku (na przykład binarny) nie jest obsługiwana przez system kontroli źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; Dodaj, nie jest wykonywane.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Pliku lub projektu wymaga ponownego załadowania.|  
|SCC_E_FILENOTEXIST|Nie można odnaleźć pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle `fOptions` zastępuje się tutaj tablicy, `pfOptions`, za pomocą jednego `LONG` opcji specyfikacji każdego pliku. Jest to spowodowane typ pliku mogą się różnić między plikami.  
  
> [!NOTE]
>  Można określić zarówno `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` opcje dla tego samego pliku, ale jest prawidłowy do określenia żadnego z tych celów. Ustawienie nie jest taka sama jak ustawienie `SCC_FILETYPE_AUTO`, w którym to przypadku źródło sterowania wtyczka automatycznie wykrywa typ pliku.  
  
 Poniżej znajduje się lista flagi używane do `pfOptions` tablicy:  
  
|Opcja|Wartość|Znaczenie|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Wtyczka do kontroli źródła, należy wykryć typu pliku.|  
|SCC_FILETYPE_TEXT|0x01|Wskazuje plik tekstowy ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Wskazuje typ plików innych niż tekst w formacie ASCII.|  
|SCC_ADD_STORELATEST|0x04|Przechowuje najnowszą kopię pliku nie różnic.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Traktuje plik jako tekst ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Traktuje plik jako tekst w formacie Unicode w formacie UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Traktuje plik jako tekst w formacie Unicode w UTF16 format nieco Endian.|  
|SCC_FILETYPE_UTF16BE|0x40|Traktuje plik jako tekst w formacie Unicode w Big Endian UTF16 spowoduje formatu.|  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)