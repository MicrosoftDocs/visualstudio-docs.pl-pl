---
title: Funkcja SccUncheckout | Dokumentacja firmy Microsoft
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
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5769f68055985fc79cc821387f6bd75613d70777
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752720"
---
# <a name="sccuncheckout-function"></a>SccUncheckout, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja spowoduje cofnięcie poprzedniej operacji wyewidencjonowania, a tym samym Przywracanie zawartość wybranego pliku lub plików do stanu sprzed wyewidencjonowanie. Wszystkie zmiany wprowadzone do pliku, ponieważ wyewidencjonowanie zostaną utracone.  
  
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
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 Niepowodzeń  
 [in] Liczba plików określonych w `lpFileNames` tablicy.  
  
 lpFileNames  
 [in] Tablica nazw plików, do których chcesz cofnąć wyewidencjonowanie w pełni kwalifikowaną ścieżką lokalną.  
  
 fOptions  
 [in] Polecenie flagi (nieużywane).  
  
 pvOptions  
 [in] Opcje plug-określonych kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Cofnięcie wyewidencjonowania powiodło się.|  
|SCC_E_FILENOTCONTROLLED|Wybrany plik nie jest pod kontrolą kodu źródłowego.|  
|SCC_E_ACCESSFAILURE|Wystąpił problem podczas uzyskiwania dostępu do systemu kontroli źródła, prawdopodobnie z powodu problemów z siecią lub rywalizacji o zasoby. Ponowienie próby jest zalecane.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd. Cofnij wyewidencjonowanie nie powiodło się.|  
|SCC_E_NOTCHECKEDOUT|Użytkownik nie ma ten plik wyewidencjonowany.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_PROJNOTOPEN|Projekt nie został otwarty z kontroli źródła.|  
|SCC_I_OPERATIONCANCELED|Operacja została anulowana przed ukończeniem.|  
  
## <a name="remarks"></a>Uwagi  
 Po wykonaniu tej czynności `SCC_STATUS_CHECKEDOUT` i `SCC_STATUS_MODIFIED` flagi zostanie zarówno wyczyszczony dla plików, na których wykonano cofnięcie wyewidencjonowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)

