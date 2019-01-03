---
title: Karta Ogólne, okno dialogowe właściwości wątku | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f06fb3d5af44a220a1eb88fd7a4df53bc589972
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989338"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości wątku
Użyj tego okna dialogowego, aby dowiedzieć się więcej na temat określonego wątku. Aby wyświetlić to okno dialogowe, Przenieś fokus do [Widok wątków](../debugger/threads-view.md) okna lub Otwórz [widoku komunikatów](../debugger/messages-view.md) i rozwiń wiadomość. Zaznacz dowolny węzeł wątku w drzewie, a następnie wybierz **właściwości** z **widoku** menu.  
  
 **Właściwości wątku** okno dialogowe zawiera jedno okienko **ogólne** kartę. Dostępne są następujące ustawienia:  
  
|Wpis|Opis|  
|-----------|-----------------|  
|**Nazwa modułu**|Nazwa modułu.|  
|**Identyfikator wątku**|Unikatowy identyfikator tego wątku. Należy pamiętać, że numery identyfikatorów wątku są ponownie; identyfikują one wątku, tylko w przypadku okres istnienia tego wątku.|  
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są używane ponownie, więc identyfikują one proces tylko w przypadku istnienia tego procesu. Typ obiektu procesu jest tworzony po uruchomieniu programu. Wszystkie wątki w procesie udostępnianie tej samej przestrzeni adresowej i mieć dostęp do tych samych danych. Wybierz tę wartość, aby wyświetlić właściwości identyfikatora procesu.|  
|**Stan wątku**|Bieżący stan wątku. Używa uruchomionych wątków procesora; Wątek wstrzymania jest chwilę. Gotowy wątek czeka do użycia procesora, ponieważ jeden z nich jest bezpłatna. Wątek w trakcie przechodzenia czeka, aż zasób do wykonania, takie jak oczekiwanie na swój stos wykonywania stanie z dysku. Wątek oczekiwanie nie wymaga procesora, ponieważ trwa oczekiwanie na zakończenie operacji peryferyjne lub zasobu, aby zwolnić.|  
|**Przyczyna oczekiwania**|Dotyczy to tylko wtedy, gdy wątek jest w stanie oczekiwania. Pary zdarzeń są używane do komunikowania się z chronionym podsystemów.|  
|**Czas procesora CPU**|Łączny czas Procesora poświęcony ten proces i wątków. Taki sam jak czas użytkownika + czasu uprzywilejowanego.|  
|**Czas użytkownika**|Całkowity czas spędzony ten wątek wykonywania kodu w trybie użytkownika. Aplikacje są wykonywane w trybie użytkownika, tak jak podsystemy, takich jak Menedżer okien i aparat grafiki.|  
|**Czas uprzywilejowany**|Całkowity czas spędzony ten wątek wykonywania kodu w trybie uprzywilejowanym. Po wywołaniu usługi systemu Windows usługi często będzie uruchamiany w trybie uprzywilejowanym w celu uzyskania dostępu do prywatnych danych systemu. Takie dane są chronione przed dostępem przez wątków działających w trybie użytkownika. Wywołania systemu może być jawne lub może być niejawne, np. gdy wystąpi błąd strony lub przerwania.|  
|**Czas, który upłynął**|Całkowity czas (w sekundach) ten wątek został uruchomiony.|  
|**Bieżący priorytet**|Bieżący priorytet dynamiczny tego wątku. Wątków w procesie można zwiększyć i zmniejszyć własne podstawowy priorytet względem podstawowego priorytetu procesu.|  
|**Priorytet podstawowy**|Bieżący priorytet bazowy tego wątku.|  
|**Adres początkowy**|Początkowy adres wirtualny dla tego wątku.|  
|**Komputer użytkownika**|Licznik programu użytkownika dla wątku.|  
|**Przełączenia kontekstu**|Liczba przełączników z jednego wątku do innego. Przełączniki wątek może wystąpić wewnątrz pojedynczego procesu lub między procesami. Przełączenie wątku może być spowodowane przez jeden wątek, pytanie o innej informacji lub wątku jest przerywane, jeśli wątek wyższy priorytet staje się gotowe do uruchomienia.|