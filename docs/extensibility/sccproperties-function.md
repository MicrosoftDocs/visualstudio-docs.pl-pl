---
title: Funkcja SccProperties | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 519a17e7596a9cea479eeb24799724919d49bd45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433048"
---
# <a name="sccproperties-function"></a>SccProperties, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkcja ta wyświetla właściwości kontroli źródła dla pliku lub projektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 hWnd  
 [in] Uchwyt okna środowiska IDE, które wtyczka do kontroli źródła można użyć jako element nadrzędny dla wszystkie okna dialogowe, które zawiera.  
  
 lpFileName  
 [in] W pełni kwalifikowana nazwa pliku lub projektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Właściwości pomyślnie były wyświetlane.|  
|SCC_I_RELOADFILE|System kontroli wersji zmodyfikował właściwości pliku, więc IDE należy załadować ponownie ten plik.|  
|SCC_E_PROJNOTOPEN|Określony projekt nie został otwarty w kontroli źródła.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma autoryzacji do wyświetlania właściwości tego pliku lub projektu.|  
|SCC_E_FILENOTCONTROLLED|Określony plik lub projektu nie jest pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieznany lub ogólny błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła Wyświetla właściwości swoje własne w oknie dialogowym.  
  
 Właściwości są definiowane przez wtyczka do kontroli źródła i może różnić się od wtyczki do wtyczki. Jeśli wtyczka pozwala użytkownikowi na zmianę właściwości kontroli źródła pliku, powinna zwrócić `SCC_I_RELOAD` celu sygnalizowania, że środowisko IDE, wymagających ponownego załadowania tego pliku lub projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
