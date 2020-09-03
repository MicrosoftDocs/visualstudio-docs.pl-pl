---
title: Funkcja SccGetEvents | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d975570334aeab7c6709db92f3240a8e8d06b131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200111"
---
# <a name="sccgetevents-function"></a>SccGetEvents, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ta funkcja pobiera zdarzenie stanu z kolejki.  
  
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
 podczas Struktura kontekstu wtyczki kontroli źródła.  
  
 lpFileName  
 [in. out] Bufor, w którym wtyczka do kontroli źródła umieszcza zwracaną nazwę pliku (do _MAX_PATH znaków).  
  
 lpStatus  
 [in. out] Zwraca kod stanu (zobacz [kod stanu pliku](../extensibility/file-status-code-enumerator.md) dla możliwych wartości).  
  
 pnEventsRemaining  
 [in. out] Zwraca liczbę wpisów pozostałych w kolejce po tym wywołaniu. Jeśli ta liczba jest duża, obiekt wywołujący może zdecydować się na wywołanie [SccQueryInfo](../extensibility/sccqueryinfo-function.md) , aby uzyskać wszystkie informacje jednocześnie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinna zwracać jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Pobieranie zdarzeń zakończyło się pomyślnie.|  
|SCC_E_OPNOTSUPPORTED|Ta funkcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana podczas przetwarzania bezczynności, aby sprawdzić, czy istnieją jakiekolwiek aktualizacje stanu dla plików objętych kontrolą źródła. Wtyczka do kontroli źródła utrzymuje stan wszystkich plików, o których wie, i zawsze, gdy zmiana stanu jest zapisywana przez wtyczkę, stan i skojarzony plik są przechowywane w kolejce. Gdy `SccGetEvents` jest wywoływana, zostanie pobrany i zwrócony górny element kolejki. Ta funkcja jest ograniczona do zwrócenia tylko wcześniej buforowanych informacji i musi mieć bardzo szybki szybkością oferowaną (czyli brak odczytywania dysku lub do systemu kontroli źródła dla stanu); w przeciwnym razie wydajność IDE może ulec obniżeniu.  
  
 Jeśli nie ma aktualizacji stanu do raportu, wtyczka do kontroli źródła przechowuje pusty ciąg w buforze wskazywanym przez `lpFileName` . W przeciwnym razie wtyczka przechowuje pełną nazwę ścieżki pliku, dla którego informacje o stanie uległy zmianie i zwraca odpowiedni kod stanu (jedna z wartości szczegółowych w [kodzie stanu pliku](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
