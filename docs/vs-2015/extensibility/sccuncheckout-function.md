---
title: Funkcja SccUncheckout | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ae5ecd7568a10936479f72f92e9914132f2dcdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190864"
---
# <a name="sccuncheckout-function"></a>SccUncheckout, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja cofa poprzednią operację wyewidencjonowania, a tym samym przywraca zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowania. Wszystkie zmiany wprowadzone do pliku od momentu ich wyewidencjonowania zostaną utracone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 nFiles  
 podczas Liczba plików określona w `lpFileNames` tablicy.  
  
 lpFileNames  
 podczas Tablica w pełni kwalifikowanych nazw ścieżek lokalnych dla plików, dla których ma zostać cofnięte wyewidencjonowanie.  
  
 fOptions  
 podczas Flagi poleceń (nieużywane).  
  
 pvOptions  
 podczas Opcje dotyczące wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Cofnięcie wyewidencjonowania zakończyło się pomyślnie.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie znajduje się pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem z uzyskaniem dostępu do systemu kontroli źródła prawdopodobnie z powodu problemów z siecią lub rywalizacją. Zalecana jest ponowna próba.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd. Cofnięcie wyewidencjonowania nie powiodło się.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma wyewidencjonowanego pliku.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Po wykonaniu tej operacji `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` flagi i zostaną wyczyszczone dla plików, na których wykonano wyewidencjonowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
