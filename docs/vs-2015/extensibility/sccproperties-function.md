---
title: Funkcja SccProperties | Microsoft Docs
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
ms.openlocfilehash: f4e8452465873cb66883abd347406d17b469e90a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200003"
---
# <a name="sccproperties-function"></a>SccProperties, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja wyświetla właściwości kontroli źródła dla pliku lub projektu.  
  
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
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 Właściwość  
 podczas Uchwyt okna środowiska IDE, który może być używany przez wtyczkę kontroli źródła jako element nadrzędny dla dowolnych okien dialogowych, które zapewnia.  
  
 lpFileName  
 podczas W pełni kwalifikowana nazwa ścieżki pliku lub projektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Właściwości zostały pomyślnie wyświetlone.|  
|SCC_I_RELOADFILE|System kontroli wersji zmodyfikował właściwości pliku, więc IDE powinien ponownie załadować ten plik.|  
|SCC_E_PROJNOTOPEN|Określony projekt nie został otwarty w kontroli źródła.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie ma uprawnień do wyświetlania właściwości tego pliku lub projektu.|  
|SCC_E_FILENOTCONTROLLED|Określony plik lub projekt nie znajduje się pod kontrolą źródła.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieznany lub ogólny błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła wyświetla właściwości w osobnym oknie dialogowym.  
  
 Właściwości są definiowane przez wtyczkę kontroli źródła i mogą się różnić od wtyczki do wtyczki. Jeśli wtyczka zezwala użytkownikowi na zmianę właściwości kontroli źródła pliku, powinien zwrócić `SCC_I_RELOAD` sygnał, aby SYGNALIZOWAĆ IDE, że ten plik lub projekt musi zostać ponownie załadowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
