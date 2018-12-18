---
title: Debugowanie wątków i procesów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d0a42ed90275bb8988bb6bedc0b707aec21ab3b8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802619"
---
# <a name="debug-threads-and-processes"></a>Debugowanie wątków i procesów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wątki * i *procesy* to pojęcia pokrewne w dziedzinie informatyki. Oba reprezentują sekwencje instrukcji, które muszą być wykonywane w określonej kolejności. Instrukcje w oddzielnych wątkach lub procesach można jednak wykonać równolegle.  
  
 Procesy istnieją w systemie operacyjnym i odpowiadają co użytkownicy widzą jako programy lub aplikacje. Wątek, z drugiej strony, istnieje w ramach procesu. Z tego powodu wątki są czasami określane jako *procesami lekkimi*. Każdy proces składa się z jednego lub więcej wątków.  
  
 Istnienie wielu procesów umożliwia komputerowi wykonywanie więcej niż jedno zadanie naraz. Istnienie wielu wątków Umożliwia procesowi oddzielenie pracy do wykonania w sposób równoległy. Na komputerze z komputerów wieloprocesorowych procesy i wątki można uruchomić na różnych procesorach. Pozwala to na prawdziwe przetwarzanie równoległe.  
  
 Doskonałe przetwarzania równoległe nie zawsze jest możliwe. Wątki czasami muszą być synchronizowane. Jeden wątek może być konieczne odczekanie na wynik z innego wątku, lub jeden wątek wymaga wyłącznego dostępu do zasobu, który używa innego wątku. Problemy z synchronizacją są typową przyczyną błędów w aplikacjach wielowątkowych. Czasami wątki mogą kończyć się, oczekując na zasób, który nigdy nie stanie się dostępny. Skutkuje to warunkiem o nazwie *zakleszczenia*.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Debugera zapewnia zaawansowane, ale łatwe w użyciu narzędzia do debugowania wątków i procesów.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Narzędzia do debugowania wątków i procesów w programie Visual Studio  
 Podstawowe narzędzia do pracy z procesami w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] są **dołączyć do procesu** okno dialogowe **procesy** oknie i **Lokalizacja debugowania** paska narzędzi. Podstawowe narzędzia do debugowania wątków to **wątków** okna, znaczniki wątków w oknach źródłowych i **Lokalizacja debugowania** paska narzędzi.  
  
 Podstawowe narzędzia do debugowania aplikacji wielowątkowych to **stosów równoległych** i **zadań równoległych**, **równoległego wyrażenia kontrolnego**, i **wątków GPU** systemu windows.  
  
 W poniższej tabeli przedstawiono dostępne informacje i akcje można wykonać w każdym z tych miejsc:  
  
|Interfejs użytkownika|Dostępne informacje|Akcje, które można wykonać|  
|--------------------|---------------------------|-----------------------------|  
|**Dołącz do procesu** okno dialogowe|Dostępne procesy, które można dołączyć do:<br /><br /> — Nazwa procesu (.exe)<br />-Przetwarzanie numer identyfikacyjny<br />-Tytuł paska menu<br />— Typ (Managed v4.0; Managed v2.0, v1.1, v1.0; x86; x64; IA64)<br />-User Name (nazwa konta)<br />-Liczba sesji|Wybierz proces do dołączenia<br /><br /> Wybierz komputer zdalny<br /><br /> Zmień typ transportu dla łączenia z komputerami zdalnymi|  
|**Procesy** okna|Dołączone procesy:<br /><br /> — Nazwa procesu<br />-Przetwarzanie numer identyfikacyjny<br />— Ścieżka do przetwarzania .exe<br />-Tytuł paska menu<br />-Stan (przerwanie. Uruchomienie)<br />-Debugowania (natywne i zarządzane itd.)<br />— Typ (ustawienie domyślne, natywnie bez uwierzytelnienia) transportu<br />-Kwalifikator transportu (komputer zdalny)|Narzędzia:<br /><br /> — Dołączanie<br />-Odłączenia<br />— Zakończenie<br /><br /> Menu skrótów:<br /><br /> — Dołączanie<br />-Odłączenia<br />-Odłącz po zatrzymaniu debugowania<br />— Zakończenie|  
|**Wątki** okna|Wątki w bieżącym procesie:<br /><br /> — Identyfikator wątku<br />-Zarządzany identyfikator<br />— Kategoria (główny wątek, wątek interfejsu, obsługa wywołania procedury zdalnej lub Wątek roboczy)<br />— Nazwa wątku<br />— Lokalizacja gdy tworzony jest wątek<br />— Priorytet<br />-Maska koligacji<br />-Licznik wstrzymany<br />— Nazwa procesu<br />-Wskaźnik flagi<br />-Wskaźnik wstrzymany|Narzędzia:<br /><br /> -Search<br />-Przeszukaj stos wywołań<br />-Flaguj tylko mój kod<br />-Oflaguj niestandardowy wybór modułów<br />-Grupuj według<br />-Kolumn<br />-Rozwiń/Zwiń stosy wywołań<br />-Rozwiń/Zwiń grupy<br />— Zablokuj/Odblokuj wątki<br /><br /> Menu skrótów:<br /><br /> — Pokaż wątki w źródle<br />-Przełączanie do wątku<br />— Blokowanie uruchomionego wątku<br />-Odblokowywanie zablokowanego wątku<br />-Flagowanie wątku dla przeprowadzenia dodatkowych badań<br />-Usuń flagę wątku<br />— Zmień nazwę wątku<br />— Wyświetlanie i ukrywanie wątków<br /><br /> Inne akcje:<br /><br /> — Wyświetlanie stosu wywołań wątku w DataTip|  
|Okno źródłowe|Wskaźniki wątku na lewym marginesie na oprawę wskazują jeden lub wiele wątków (wyłączone domyślnie, włączone za pomocą menu skrótów na liście **wątków** okna)|Menu skrótów:<br /><br /> -Przełączanie do wątku<br />-Flagowanie wątku dla przeprowadzenia dodatkowych badań<br />-Usuń flagę wątku|  
|**Lokalizacja debugowania** paska narzędzi|-Bieżący proces<br />-Wstrzymywanie aplikacji<br />-Wznowić działanie aplikacji<br />-Wstrzymywanie i zamykanie aplikacji<br />-Bieżącego wątku<br />-Toggle bieżącego stanu flagi wątku<br />— Pokaż tylko oflagowane wątki<br />-Pokazywanie tylko bieżącego procesu<br />-Bieżącej ramki stosu|-Przełączanie do innego procesu<br />-Wstrzymać, wznowić lub zamykanie aplikacji<br />-Przełączyć się do innego wątku w bieżącym procesie<br />-Przełączyć się do innej ramki stosu w bieżącym wątku<br />-Flagowanie bieżących wątków lub flaga<br />— Pokaż tylko oflagowane wątki<br />-Pokazywanie tylko bieżącego procesu|  
|**Stosów równoległych** okna|-Stosy wywołań wielu wątków w jednym oknie.<br />-Aktywną ramkę stosu dla każdego wątku.<br />-Obiekty wywołujące i wywoływane dla dowolnej metody.|-Odfiltruj określone wątki<br />— Przejdź do widoku zadań równoległych<br />-Flagowanie lub wątek<br />-Powiększenia|  
|**Zadań równoległych** okna|— Wyświetlanie informacji o <xref:System.Threading.Tasks.Task> obiektów w tym identyfikator zadania: stan zadania (zaplanowane, uruchomiona, oczekujące, zakleszczone), i który wątek jest przydzielony do zadania.<br />-Bieżąca lokalizacja w stosie wywołań.<br />-Przekazany do zadania w czasie tworzenia delegata|-Przełączanie do bieżącego zadania<br />-Flagowanie lub zadania<br />— Blokowanie lub odblokowywanie zadania|  
|**Równoległe wyrażenie kontrolne** okna|-Kolumna flagi, w którym można oznaczyć wątek, który chcesz zwrócić szczególną uwagę.<br />-Kolumna ramki, w której Strzałka wskazuje wybraną ramkę.<br />-Konfigurowalna kolumna, która może wyświetlać maszynę, proces, kafelków, zadania i wątku.|-Flagowanie lub wątek<br />-Tylko wątki oflagowane<br />-Przełączanie ramek<br />-Sortowanie kolumny<br />-Grupa wątków<br />— Blokowanie lub odblokowywanie wątków<br />-Eksportowanie danych w oknie czujki równoległej|  
|**Wątki GPU** okna|-Kolumna flagi, w którym można oznaczyć wątek, który chcesz zwrócić szczególną uwagę.<br />-Kolumna aktywnego wątku, w której żółta strzałka wskazuje aktywny wątek. Strzałka wskazuje wątek, w którym wykonanie przerwało pracę debugera.<br />**Liczba wątków** kolumny, która wyświetla liczbę wątków w tej samej lokalizacji.<br />**Wiersza** kolumny, która wyświetla wiersz kodu, w którym znajduje się każda grupa wątków.<br />**Adres** kolumny, która wyświetla adres instrukcji, w którym znajduje się każda grupa wątków.<br />**Lokalizacji** kolumny, która jest lokalizacją w kodzie adresu.<br />**Stan** kolumny, która wskazuje, czy wątek jest aktywny, czy zablokowany.<br />**Kafelek** kolumny, która zawiera indeks kafelka dla wątków w wierszu.|-Zmienić na inny wątek aktywny<br />— Wyświetlanie określonego fragmentu i wątku<br />— Wyświetlanie lub ukrywanie kolumn<br />— Sortowanie według kolumny<br />-Grupa wątków<br />— Blokowanie lub odblokowywanie wątków<br />-Flagowanie lub wątek<br />-Tylko wątki oflagowane|  
  
## <a name="see-also"></a>Zobacz też  
 [Dołączanie do uruchomionego procesu](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie kodu GPU](../debugger/debugging-gpu-code.md)



