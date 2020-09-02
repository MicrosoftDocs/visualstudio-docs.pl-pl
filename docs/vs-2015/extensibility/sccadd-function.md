---
title: Funkcja SccAdd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daac15bbb7829d510db17ba02057a2dc86c55990
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791948"
---
# <a name="sccadd-function"></a>SccAdd, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja dodaje nowe pliki do systemu kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 nFiles  
 podczas Liczba plików, które zostały wybrane do dodania do bieżącego projektu, zgodnie z podanym w `lpFileNames` tablicy.  
  
 lpFileNames  
 podczas Tablica w pełni kwalifikowanych lokalnych nazw plików do dodania.  
  
 lpComment  
 podczas Komentarz, który ma zostać zastosowany do wszystkich dodawanych plików.  
  
 pfOptions  
 podczas Tablica flag poleceń dostarczonych dla poszczególnych plików.  
  
 pvOptions  
 podczas Opcje dotyczące wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja dodawania zakończyła się pomyślnie.|  
|SCC_E_FILEALREADYEXISTS|Wybrany plik znajduje się już pod kontrolą źródła.|  
|SCC_E_TYPENOTSUPPORTED|Typ pliku (na przykład Binary) nie jest obsługiwany przez system kontroli źródła.|  
|SCC_E_OPNOTSUPPORTED|System kontroli źródła nie obsługuje tej operacji.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd; nie wykonano operacji dodawania.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
|SCC_I_RELOADFILE|Plik lub projekt musi zostać ponownie załadowany.|  
|SCC_E_FILENOTEXIST|Nie znaleziono pliku lokalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj `fOptions` są one zastępowane przez tablicę, `pfOptions` z jedną `LONG` specyfikacją opcji na plik. Wynika to z faktu, że typ pliku może się różnić od pliku do pliku.  
  
> [!NOTE]
> Nie można określić obu `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` opcji i dla tego samego pliku, ale jest on prawidłowy do określenia żadnego z nich. Ustawienie nie jest takie samo jak ustawienie `SCC_FILETYPE_AUTO` , a w takim przypadku Wtyczka kontroli źródła automatycznie wykrywa typ pliku.  
  
 Poniżej znajduje się lista flag użytych w `pfOptions` tablicy:  
  
|Opcja|Wartość|Znaczenie|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Wtyczka do kontroli źródła powinna wykryć typ pliku.|  
|SCC_FILETYPE_TEXT|0x01|Wskazuje plik tekstowy ASCII.|  
|SCC_FILETYPE_BINARY|0x02|Wskazuje typ pliku inny niż tekst ASCII.|  
|SCC_ADD_STORELATEST|0x04|Przechowuje tylko najnowszą kopię pliku, bez różnic.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Traktuje plik jako tekst ANSI.|  
|SCC_FILETYPE_UTF8|0x10|Traktuje plik jako tekst Unicode w formacie UTF8.|  
|SCC_FILETYPE_UTF16LE|0x20|Traktuje plik jako tekst w formacie Unicode w UTF16 little endian.|  
|SCC_FILETYPE_UTF16BE|0x40|Traktuje plik jako tekst Unicode w formacie UTF16 big endian.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
