---
title: Karta Ogólne, okno dialogowe właściwości wątku | Microsoft Docs
description: Wyświetl okno dialogowe właściwości wątku, aby uzyskać informacje na temat wątku, w tym nazwę modułu, identyfikator wątku, identyfikator procesu, stan wątku, przyczynę oczekiwania i czas procesora CPU.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- threading [Visual Studio], thread properties
- thread properties
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02ba7d14dad8e4755170ffca7853aa9cc6c85a19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870548"
---
# <a name="general-tab-thread-properties-dialog-box"></a>Karta ogólna, okno dialogowe właściwości wątku
Użyj tego okna dialogowego, aby dowiedzieć się więcej o określonym wątku. Aby wyświetlić to okno dialogowe, Przenieś fokus do okna [Widok wątków](../debugger/threads-view.md) lub Otwórz [komunikaty Wyświetl](../debugger/messages-view.md) i rozwiń komunikat. Wybierz dowolny węzeł wątku w drzewie, a następnie wybierz polecenie **Właściwości** z menu **Widok** .

 Okno dialogowe **Właściwości wątku** zawiera jedno okienko, kartę **Ogólne** . Dostępne są następujące ustawienia:

|Wpis|Opis|
|-----------|-----------------|
|**Nazwa modułu**|Nazwa modułu.|
|**Identyfikator wątku**|Unikatowy identyfikator tego wątku. Zwróć uwagę, że numery identyfikatorów wątków są ponownie używane; identyfikują one wątek tylko dla okresu istnienia tego wątku.|
|**Identyfikator procesu**|Unikatowy identyfikator tego procesu. Numery identyfikatorów procesów są ponownie używane, aby identyfikować proces tylko w okresie istnienia tego procesu. Typ obiektu procesu jest tworzony podczas uruchamiania programu. Wszystkie wątki w procesie mają tę samą przestrzeń adresową i mają dostęp do tych samych danych. Wybierz tę wartość, aby wyświetlić właściwości identyfikatora procesu.|
|**Stan wątku**|Bieżący stan wątku. Uruchomiony wątek korzysta z procesora; wątek gotowości ma używać jednego z nich. Wątek gotowy oczekuje na użycie procesora, ponieważ jeden z nich nie jest bezpłatny. Wątek w przejściu czeka na wykonanie zasobu, na przykład oczekiwanie na stronicowanie jego stosu na dysku. Wątek oczekujący nie potrzebuje procesora, ponieważ oczekuje na ukończenie operacji urządzenia zewnętrznego lub zasób, który zostanie zwolniony.|
|**Przyczyna oczekiwania**|Ma to zastosowanie tylko wtedy, gdy wątek jest w stanie oczekiwania. Pary zdarzeń są używane do komunikowania się z chronionymi podsystemami.|
|**Czas procesora CPU**|Łączny czas procesora CPU poświęcony na ten proces i jego wątki. Równy czasowi użytkownika + czas uprzywilejowany.|
|**Czas użytkownika**|Łączny czas, który upłynął, gdy ten wątek poświęca wykonywanie kodu w trybie użytkownika. Aplikacje są wykonywane w trybie użytkownika, jak w przypadku podsystemów, takich jak Menedżer okien i aparat grafiki.|
|**Uprzywilejowany czas**|Łączny czas, który upłynął, gdy ten wątek poświęca wykonywanie kodu w trybie uprzywilejowanym. Gdy wywoływana jest usługa systemowa systemu Windows, usługa będzie często uruchamiana w trybie uprzywilejowanym, aby uzyskać dostęp do danych z systemu. Takie dane są chronione przed dostępem przez wątki wykonywane w trybie użytkownika. Wywołania systemu mogą być jawne lub mogą być niejawne, na przykład w przypadku wystąpienia błędu strony lub przerwania.|
|**Czas, który upłynął**|Łączny czas, który upłynął (w sekundach) działania tego wątku.|
|**Bieżący priorytet**|Bieżący priorytet dynamiczny tego wątku. Wątki w ramach procesu mogą podnieść i obniżyć swój własny priorytet podstawowy względem priorytetu podstawowego procesu.|
|**Priorytet podstawowy**|Bieżący Priorytet podstawowy tego wątku.|
|**Adres początkowy**|Początkowy adres wirtualny dla tego wątku.|
|**KOMPUTER użytkownika**|Licznik programu użytkownika dla wątku.|
|**Przełączenia kontekstu**|Liczba przełączników z jednego wątku do innego. Przełączniki wątków mogą wystąpić w ramach jednego procesu lub między procesami. Przełącznik wątku może być spowodowany przez jeden wątek, który prosi o informacje lub wątek jest zastępujący, gdy wątek o wyższym priorytecie stanie się gotowy do uruchomienia.|