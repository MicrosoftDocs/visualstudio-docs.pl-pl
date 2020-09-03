---
title: Stos wywołań zdarzeń grafiki | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8344050d26286263e0c33974b976e4ae25ff18de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192751"
---
# <a name="graphics-event-call-stack"></a>Stos wywołań zdarzeń grafiki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stos wywołań zdarzeń grafiki w analizator grafiki programu Visual Studio ułatwia Mapowanie relacji między problematycznymi zdarzeniami graficznymi a kodem źródłowym aplikacji.  
  
 To jest okno stosu wywołań zdarzeń:  
  
 ![Stos wywołań poprzedzający zdarzenie DrawIndexed.](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Zrozumienie stosu wywołań zdarzeń grafiki  
 Możesz użyć stosu wywołań zdarzeń, aby zrozumieć przepływ wykonywania, który doprowadził do określonego zdarzenia Direct3D. Jest podobna do okna stosu wywołań programu Visual Studio, z tą różnicą, że zamiast wyświetlania bieżącego stosu wywołań aktywnego wątku w działającej aplikacji jest wyświetlany stos wywołań, który istniał w momencie wystąpienia wybranego zdarzenia Direct3D. Ze stosu wywołań zdarzeń można przejść do witryny wywołania wybranego zdarzenia Direct3D, aby sprawdzić otaczający kod.  
  
 Przy użyciu stosu wywołań zdarzeń do identyfikowania ścieżki kodu, z której pochodzi zdarzenie problemu, można użyć swojej bazy kodu w celu wywnioskowania potencjalnych źródeł problemu lub dodać punkty przerwania w kodzie źródłowym aplikacji, aby można było użyć tradycyjnych technik debugowania do sprawdzenia, jak stan aplikacji lub parametrów zdarzeń powoduje niezachowanie zdarzenia. Ta analiza może pomóc w znalezieniu problemów w kodzie źródłowym, które są w manifeście tylko jako problemy z renderowaniem.  
  
### <a name="graphics-event-call-stack-information"></a>Informacje o stosie wywołań zdarzeń grafiki  
 Stos wywołań zdarzeń nie obsługuje zdarzeń przed ramkami ani zdarzeń zdefiniowanych przez użytkownika. Stos wywołań zdarzeń grafiki jest wyświetlany w formacie tabeli.  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**Nazwa**|Symbol, który jednoznacznie identyfikuje funkcję, która zawiera lokację wywołania. Symbol debugowania dla funkcji jest wyświetlany, gdy jest dostępny; w przeciwnym razie zostanie wyświetlone przesunięcie funkcji.|  
|**Plik**|Nazwa pliku kodu źródłowego lub pliku biblioteki, który zawiera lokację wywołania.|  
|**Lokalizacja**|Numer wiersza dla witryny wywołania.|  
  
### <a name="links-to-graphics-objects"></a>Linki do obiektów graficznych  
 Aby zrozumieć wybrane zdarzenie grafiki, można potrzebować informacji o obiektach Direct3D, które są z nim skojarzone. Okno **stosu wywołań zdarzeń grafiki** zawiera linki do tych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)
