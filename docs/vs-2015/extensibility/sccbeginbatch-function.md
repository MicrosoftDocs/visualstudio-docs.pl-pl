---
title: Funkcja SccBeginBatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 264d9057bf4f17281d6d8a16ed3a6794004e0e21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189564"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja uruchamia sekwencję wsadową operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana w celu zakończenia zadania wsadowego. Te partie nie mogą być zagnieżdżane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Partia operacji została pomyślnie rozpoczęta.|  
|SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Partie kontroli źródła są używane do wykonywania tych samych operacji w wielu projektach lub wielu kontekstach. Partie mogą służyć do eliminowania nadmiarowych okien dialogowych na projekt ze środowiska użytkownika podczas operacji wsadowej. `SccBeginBatch`Funkcja i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako para funkcji do wskazywania początku i końca operacji. Nie mogą być zagnieżdżane. `SccBeginBatch` ustawia flagę wskazującą, że operacja wsadowa jest w toku.  
  
 Podczas wykonywania operacji wsadowej Wtyczka kontroli źródła powinna mieć co najwyżej jedno okno dialogowe dla każdego pytania do użytkownika i stosować odpowiedź z tego okna dialogowego we wszystkich kolejnych operacjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
