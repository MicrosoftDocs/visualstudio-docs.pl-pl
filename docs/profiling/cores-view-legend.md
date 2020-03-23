---
title: Rdzenie Zobacz Legendę | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea3184fbcd3561b88521f7dbdf4bf44c925150d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62553166"
---
# <a name="cores-view-legend"></a>Rdzenie Zobacz legendę
Legenda widoku rdzeni identyfikuje każdy wątek według koloru i nazwy. Zawiera kolumny, które pokazują liczby dla przełączników kontekstu między rdzeniami, przełączników kontekstu całkowitego i procent przełączników kontekstu, które przecinają rdzenie. Wiersze w legendzie są sortowane według liczby przełączników kontekstu między rdzeniami w kolejności malejącej.

 Można wybrać wiersze w legendzie, aby filtrować wątki, które są wyświetlane na osi czasu. Tylko wybrane wątki są wyświetlane na osi czasu. Jeśli nie zaznaczono żadnych wierszy, wszystkie wiersze są wyświetlane na osi czasu.

 Przełączniki kontekstu międzyrdzeniowego kosztują więcej w obciążenie i wydajność niż przełączniki, które pozostają na tym samym rdzeniu logicznym. Podczas przełączania kontekstu rejestry procesora są zapisywane i przywracane, wykonywany jest kod jądra systemu operacyjnego, wpisy buforu wyglądu tłumaczenia są ponownie ładowane, a potok procesora jest opróżniany. Przełączniki kontekstu między rdzeniem może być nawet droższe niż inne przełączniki kontekstu, ponieważ dane pamięci podręcznej nie jest prawidłowy dla tego wątku na innym rdzeniu. Z drugiej strony jeśli wątek jest kontekstem przełączane na rdzeń, który wcześniej prowadził na, jest prawdopodobne, że przydatne dane są nadal w pamięci podręcznej. Gdy przełączniki kontekstu między rdzeniami zostały zwiększone przez próby zarządzania koligacji wątku i wydajność jest obniżona, należy rozważyć, czy rozwiązać ten problem. Zacznij od wyeliminowania koligacji wątku, a następnie obserwuj wynikowe zachowanie międzyrdzeniowe.

 W poniższej tabeli opisano elementy legendy.

|Element|Definicja|
|-------------|----------------|
|Nazwa wątku|Pokazuje kolor wątku na osi czasu poprzednich rdzeni i nazwę tego wątku.|
|Międzyrdzeniowe przełączniki kontekstowe|Liczba przełączników kontekstu dla wątku, który również przełączał się z jednego rdzenia logicznego do drugiego. Nie rozróżnia między przełącznikami kontekstu między rdzeniami, które krzyżują się z jednego procesora die do drugiego w porównaniu z tymi, które pozostają na tej samej matrycy.|
|Przełączniki kontekstu całkowitego|Całkowita liczba przełączników kontekstu dla danego wątku w okresie próbkowania. Za każdym razem, gdy wątek zmienia kontekst (na przykład od wykonywania do synchronizacji) jeden przełącznik kontekstu jest zliczany.|
|Procent przełączników kontekstowych przecinanych rdzeni|Oblicza się jako wartość procentową przez podzielenie liczby przełączników kontekstu między rdzeniami przez liczbę całkowitych przełączników kontekstu. Im wyższy procent, tym większy ogólny wpływ narzutów kontekstu międzyrdzeniowego przełącza na wydajność tego wątku.|

## <a name="see-also"></a>Zobacz też
- [Widok rdzeni](../profiling/cores-view.md)