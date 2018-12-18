---
title: Funkcja SccBeginBatch | Dokumentacja firmy Microsoft
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
- SccBeginBatch
helpviewer_keywords:
- SccBeginBatch function
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31064e0bc746ecc6fb67f5e2feacbd9ae91ca7bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724349"
---
# <a name="sccbeginbatch-function"></a>SccBeginBatch, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja zostanie uruchomiony sekwencji operacji kontroli źródła. [SccEndBatch](../extensibility/sccendbatch-function.md) zostanie wywołana w celu zakończenia zadania wsadowego. Partie te nie mogą być zagnieżdżone.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Batch operacji rozpoczęło się pomyślnie.|  
|SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Partie kontroli źródła są używane do wykonania tych samych operacji między wieloma projektami lub wieloma kontekstów. Partie można wyeliminować okna dialogowe projektu nadmiarowe od środowiska użytkownika podczas operacji wsadowej. `SccBeginBatch` Funkcji i [SccEndBatch](../extensibility/sccendbatch-function.md) są używane jako pary funkcji do wskazania rozpoczęcie i zakończenie operacji. Nie można zagnieżdżać ich. `SccBeginBatch` Ustawia flagę wskazującą, że trwa wykonywanie operacji przetwarzania wsadowego.  
  
 Podczas operacji zbiorczej jest włączone, wtyczka do kontroli źródła należy co najwyżej jedno okno dialogowe dla pytań użytkownik widzi i zastosować odpowiedzi z tego okna dialogowego na wszystkie kolejne operacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)

