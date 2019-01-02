---
title: Stos wywołań zdarzeń grafiki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5201fbbe9cdd5e452621233b10ccf31119a642a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939852"
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
Stos wywołań zdarzenia grafiki w analizatora grafiki programu Visual Studio ułatwia mapowanie relacji między zdarzenia grafiki problematyczne i kod źródłowy aplikacji.  
  
 Jest to okno stosu wywołań zdarzeń:  
  
 ![Stos wywołań zdarzeń DrawIndexed poprzedzającego. ](media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Opis stos wywołań zdarzeń grafiki  
 Stos wywołań zdarzenia można użyć, aby zrozumieć przepływ wykonania, która doprowadziła do konkretnego zdarzenia Direct3D. Jest on podobny okna stosu wywołań programu Visual Studio, z tą różnicą, że zamiast bieżącego stosu wywołań bieżącego wątku w uruchomionej aplikacji, wyświetla stos wywołań istniał wybrane zdarzenia Direct3D. Z stos wywołań zdarzenia można przejść do witryny wywołania wybranego zdarzenia Direct3D, aby sprawdzić otaczającym kodem.  
  
 Za pomocą stos wywołań zdarzenia, aby zidentyfikować ścieżki kodu, z której pochodzi zdarzenie problemu, swojej wiedzy na temat kodu można użyć, aby wywnioskował potencjalnych źródeł problemu, lub dodać punkty przerwania w kodzie źródłowym aplikacji tak, aby można było używać tradycyjny debugowanie techniki, aby sprawdzić, jak stan aplikacji lub zdarzeń parametrów powodują zdarzenia w celu błędne działanie. W ten sposób może pomóc w znalezieniu problemów w kodzie źródłowym, który tylko dyskowe widoczne jako problemów z renderowaniem.  
  
### <a name="graphics-event-call-stack-information"></a>Informacje stosu wywołań zdarzeń grafiki  
 Stos wywołań zdarzeń nie obsługuje wstępne ramki lub zdarzenia zdefiniowane przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlana w formacie tabeli.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Symbol, który unikatowo identyfikuje funkcji, która zawiera wywołania. Symbol debugowania dla tej funkcji jest wyświetlane, gdy jest ona dostępna; w przeciwnym razie zostanie wyświetlony przesunięcie funkcji.|  
|**Plik**|Nazwa pliku, plik kodu źródłowego lub plik biblioteki, który zawiera wywołania.|  
|**Lokalizacja**|Numer wiersza wywołania.|  
  
### <a name="links-to-graphics-objects"></a>Łącza do obiektów graficznych  
 Aby zrozumieć zdarzenia wybranego grafiki, może być konieczne informacje o obiektach Direct3D, które są skojarzone z nim. **Stos wywołań zdarzenia grafiki** okno zawiera łącza do tych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków](walkthrough-missing-objects-due-to-vertex-shading.md)