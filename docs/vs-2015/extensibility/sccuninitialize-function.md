---
title: Funkcja SccUninitialize | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190847"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja czyści wszelkie alokacje lub otwiera połączenia utworzone przez poprzednie wywołanie do [SccInitialize](../extensibility/sccinitialize-function.md) w celu zamknięcia wtyczki kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 podczas Wskaźnik do struktury kontekstu wtyczki kontroli źródła utworzony w [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Czyszczenie zostało ukończone pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Wtyczka do kontroli źródła jest odpowiedzialna za przygotowanie się do wyłączenia i zwolnienia pamięci, którą wtyczka przydzieliła dla struktury kontekstu. Funkcja jest wywoływana jednokrotnie dla każdego danego wystąpienia wtyczki. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza to wywołanie. Nie można nadal otwierać projektów w czasie wywołania do `SccUninitialize` .  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
