---
title: Funkcja SccGetEvents | Dokumentacja firmy Microsoft
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
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 821d8f565c4f8ebb926459da9031a055c6c7992f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807065"
---
# <a name="sccgetevents-function"></a>SccGetEvents, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja pobiera zdarzenia w kolejce stanu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 lpFileName  
 [out w] Bufor, w którym wtyczka do kontroli źródła umieszcza nazwa zwróconego pliku (do _MAX_PATH znaków).  
  
 lpStatus  
 [out w] Zwraca kod stanu (zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) uzyskać odpowiednie wartości).  
  
 pnEventsRemaining  
 [out w] Zwraca liczbę wpisów, które pozostanie w kolejce po tym wywołaniu. Jeśli ta liczba jest duża, obiekt wywołujący może podjąć [SccQueryInfo](../extensibility/sccqueryinfo-function.md) można pobrać wszystkich informacji naraz.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pobierz zdarzenia, które zakończyło się pomyślnie.|  
|SCC_E_OPNOTSUPPORTED|Ta funkcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana podczas przetwarzania bezczynności, aby zobaczyć, czy wystąpiły wszelkie aktualizacje stanu plików objętych kontrolą źródła. Wtyczka do kontroli źródła zachowuje stan wszystkich plików, który dysponuje informacjami i zawsze wtedy, gdy zmiany stanu jest oznaczone przez dodatek typu plug-in, stan i skojarzony plik są przechowywane w kolejce. Gdy `SccGetEvents` jest wywoływana, u góry element kolejki jest pobierana i zwracana. Ta funkcja jest ograniczona do zwrócenia tylko wcześniej buforowanych informacji i musi mieć bardzo sprawność (oznacza to, nie odczytu na dysku lub pytaniem systemu kontroli źródła dla stanu); w przeciwnym razie wydajność IDE może zostać uruchomiony zgłoszeniem nieprawidłowego działania.  
  
 Jeśli nie ma stanu aktualizacji do raportu, wtyczka do kontroli źródła są przechowywane pustego ciągu w bufor wskazywany przez `lpFileName`. W przeciwnym razie wtyczka przechowuje pełną nazwę ścieżki pliku, dla których informacje o stanie został zmieniony i zwraca kod stanu odpowiednie (jedna z wartości szczegółowo opisane w [kod stanu pliku](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)

