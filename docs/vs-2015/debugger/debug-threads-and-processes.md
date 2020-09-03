---
title: Debuguj wątki i procesy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202561"
---
# <a name="debug-threads-and-processes"></a>Debugowanie wątków i procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wątki * i *procesy* to powiązane koncepcje w nauce komputerowej. Obie reprezentują sekwencje instrukcji, które muszą być wykonywane w określonej kolejności. Jednak instrukcje w oddzielnych wątkach lub procesach mogą być wykonywane równolegle.  
  
 Procesy istnieją w systemie operacyjnym i odpowiadają tym, co użytkownicy widzą jako programy lub aplikacje. Wątek, z drugiej strony, istnieje w ramach procesu. Z tego powodu wątki są czasami nazywane *procesami lekkimi*. Każdy proces składa się z co najmniej jednego wątku.  
  
 Istnienie wielu procesów umożliwia komputerowi wykonywanie więcej niż jednego zadania jednocześnie. Istnienie wielu wątków pozwala procesowi na rozdzielenie pracy do wykonania równolegle. Na komputerze z wieloprocesorowymi procesy lub wątki mogą działać na różnych procesorach. Pozwala to na prawdziwe przetwarzanie równoległe.  
  
 Doskonałe przetwarzanie równoległe nie zawsze jest możliwe. Wątki czasami muszą być zsynchronizowane. Jeden wątek może być oczekiwał na wynik z innego wątku lub jeden wątek może potrzebować wyłącznego dostępu do zasobu, który jest używany przez inny wątek. Problemy z synchronizacją to typowa przyczyna błędów w aplikacjach wielowątkowych. Czasami wątki mogą kończyć się w trakcie oczekiwania na zasoby, które nigdy nie staną się dostępne. W wyniku tego powstaje warunek o nazwie *zakleszczenie*.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Debuger zapewnia zaawansowane, ale łatwe w użyciu narzędzia do debugowania wątków i procesów.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Narzędzia do debugowania wątków i procesów w programie Visual Studio  
 Podstawowe narzędzia do pracy z procesami w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] to okno dialogowe **Dołącz do procesu** , okno **procesy** i pasek narzędzi **Lokalizacja debugowania** . Podstawowe narzędzia do debugowania wątków to okno **wątków** , znaczniki wątków w oknach źródłowych i pasek narzędzi **Lokalizacja debugowania** .  
  
 Podstawowe narzędzia do debugowania aplikacji wielowątkowych to **stosy równoległe** i **równoległe zadania**, **zegarki równoległe**i **wątki GPU** .  
  
 W poniższej tabeli przedstawiono dostępne informacje oraz akcje, które można wykonać w każdym z następujących miejsc:  
  
|Interfejs użytkownika|Dostępne informacje|Akcje, które można wykonać|  
|--------------------|---------------------------|-----------------------------|  
|Okno dialogowe **dołączanie do procesu**|Dostępne procesy, do których można dołączyć:<br /><br /> -Process Name (. exe)<br />-Proces numer IDENTYFIKACYJNy<br />-Pasek tytułu<br />-Type (Managed v 4.0; Managed v 2.0, v 1.1, v 1.0; wyposażone procesorów IA64<br />-Nazwa użytkownika (nazwa konta)<br />-Numer sesji|Wybierz proces do dołączenia<br /><br /> Wybierz komputer zdalny<br /><br /> Zmień typ transportu na potrzeby łączenia się z komputerami zdalnymi|  
|Okno **procesów**|Dołączone procesy:<br /><br /> -Process Name<br />-Proces numer IDENTYFIKACYJNy<br />-Ścieżka do pliku Process. exe<br />-Pasek tytułu<br />-State (Break. Uruchomion<br />-Debugowanie (natywne, zarządzane itp.)<br />-Transport Type (domyślnie natywny bez uwierzytelniania)<br />-Kwalifikator transportu (komputer zdalny)|Narzędzi<br /><br /> -Dołącz<br />-Odłącz<br />-Zakończ<br /><br /> Menu skrótów:<br /><br /> -Dołącz<br />-Odłącz<br />-Odłącz po zatrzymaniu debugowania<br />-Zakończ|  
|Okno **wątków**|Wątki w bieżącym procesie:<br /><br /> -Identyfikator wątku<br />— Identyfikator zarządzany<br />-Category (główny wątek, wątek interfejsu, procedura obsługi zdalnego wywołania procedury lub wątek roboczy)<br />-Nazwa wątku<br />— Lokalizacja, w której jest tworzony wątek<br />— Priorytet<br />— Maska koligacji<br />— Liczba wstrzymanych<br />-Process Name<br />— Wskaźnik flagi<br />-Wstrzymany wskaźnik|Narzędzi<br /><br /> — Wyszukiwanie<br />— Stos wywołań wyszukiwania<br />-Flaga Tylko mój kod<br />-Oflaguj niestandardowy wybór modułów<br />-Grupuj według<br />-Kolumny<br />-Rozwiń/Zwiń stosy wywołań<br />-Rozwiń/Zwiń grupy<br />-Zamrażanie/odblokowywanie wątków<br /><br /> Menu skrótów:<br /><br /> -Pokaż wątki w źródle<br />-Przełącz do wątku<br />-Zablokuj uruchomiony wątek<br />-Odblokowywanie zablokowanego wątku<br />-Oflaguj wątek do dodatkowego badania<br />-Usuń flagę wątku<br />-Zmień nazwę wątku<br />-Pokaż i Ukryj wątki<br /><br /> Inne akcje:<br /><br /> -Wyświetlanie stosu wywołań dla wątku w etykietki danych|  
|Okno źródłowe|Wskaźniki wątku na lewym marginesie wskazują jeden lub wiele wątków (domyślnie wyłączone przy użyciu menu skrótów w oknie **wątków** )|Menu skrótów:<br /><br /> -Przełącz do wątku<br />-Oflaguj wątek do dodatkowego badania<br />-Usuń flagę wątku|  
|Pasek narzędzi **lokalizacji debugowania**|— Bieżący proces<br />-Wstrzymywanie aplikacji<br />-Wznów działanie aplikacji<br />— Wstrzymywanie i zamykanie aplikacji<br />-Bieżący wątek<br />-Przełącz bieżący stan flagi wątku<br />-Pokaż tylko Oflagowane wątki<br />-Pokaż tylko bieżący proces<br />— Bieżąca Ramka stosu|-Przełącz do innego procesu<br />-Wstrzymywanie, wznawianie lub zamykanie aplikacji<br />-Przełącz do innego wątku w bieżącym procesie<br />-Przełącz do innej ramki stosu w bieżącym wątku<br />-Oflaguj lub Usuń flagę bieżących wątków<br />-Pokaż tylko Oflagowane wątki<br />-Pokaż tylko bieżący proces|  
|Okno **stosów równoległych**|-Stosy wywołań dla wielu wątków w jednym oknie.<br />— Aktywna Ramka stosu dla każdego wątku.<br />-Wywołania i wywoływane dla dowolnej metody.|-Filtruj określone wątki<br />-Przełącz do widoku zadań równoległych<br />-Flagowanie lub usuwanie flagi wątku<br />-Zoom|  
|Okno **zadań równoległych**|— Umożliwia wyświetlenie informacji o <xref:System.Threading.Tasks.Task> obiektach, w tym o identyfikatorze zadania, stanie zadania (zaplanowane, uruchomione, oczekujące, zakleszczenie) i który wątek jest przypisany do zadania.<br />— Bieżąca lokalizacja w stosie wywołań.<br />-Delegat przeszedł do zadania w czasie tworzenia|-Przełącz do bieżącego zadania<br />-Oflaguj lub Usuń flagę zadania<br />-Blokowanie lub odblokowywanie zadania|  
|Okno **czujki równoległej**|— Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę.<br />— Kolumna Frame, w której Strzałka wskazuje wybraną ramkę.<br />-Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelek, zadanie i wątek.|-Flagowanie lub usuwanie flagi wątku<br />-Wyświetla tylko Oflagowane wątki<br />-Przełącz ramki<br />-Sortuj kolumnę<br />-Grupuj wątki<br />-Zamrażanie lub odblokowywanie wątków<br />— Wyeksportuj dane w okno wyrażeń kontrolnych równoległym|  
|Okno **wątków GPU**|— Kolumna flagi, w której można oznaczyć wątek, do którego chcemy zwrócić szczególną uwagę.<br />-Kolumna aktywnego wątku, w której żółta strzałka wskazuje aktywny wątek. Strzałka wskazuje wątek, w którym wykonywanie zostało zerwane w debugerze.<br />— Kolumna **Liczba wątków** , która wyświetla liczbę wątków w tej samej lokalizacji.<br />— Kolumna **wiersz** , która wyświetla wiersz kodu, w którym znajduje się każda grupa wątków.<br />— Kolumna **Address** , w której jest wyświetlany adres instrukcji, w której znajduje się każda grupa wątków.<br />— Kolumna **Location** , która jest lokalizacją w kodzie adresu.<br />— Kolumna **stan** , która pokazuje, czy wątek jest aktywny, czy zablokowany.<br />-Kolumna **kafelka** , która pokazuje indeks kafelków dla wątków w wierszu.|-Zmień na inny aktywny wątek<br />-Wyświetlanie określonego kafelka i wątku<br />-Wyświetlanie lub ukrywanie kolumny<br />-Sortuj według kolumny<br />-Grupuj wątki<br />-Zamrażanie lub odblokowywanie wątków<br />-Flagowanie lub usuwanie flagi wątku<br />-Wyświetla tylko Oflagowane wątki|  
  
## <a name="see-also"></a>Zobacz też  
 [Dołącz do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md)
