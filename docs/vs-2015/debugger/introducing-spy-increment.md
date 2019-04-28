---
title: Wprowadzenie programu Spy ++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35e9fa2d75528549f8c55f5b52dbd4c4aa2271a6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431456"
---
# <a name="introducing-spy"></a>Wprowadzenie programu Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spy ++ umożliwia wykonywanie następujących zadań:  
  
- Wyświetla graficzny drzewa relacji między obiektami systemu. Obejmują one [procesy](../debugger/processes-view.md), [wątków](../debugger/threads-view.md), i [windows](../debugger/windows-view.md).  
  
- Wyszukaj określone [windows](../debugger/how-to-search-for-a-window-in-windows-view.md), [wątków](../debugger/how-to-search-for-a-thread-in-threads-view.md), [procesy](../debugger/how-to-search-for-a-process-in-processes-view.md), lub [wiadomości](../debugger/how-to-search-for-a-message-in-messages-view.md).  
  
- Wyświetl właściwości wybranego [windows](../debugger/how-to-display-window-properties.md), [wątków](../debugger/how-to-display-thread-properties.md), [procesy](../debugger/how-to-display-process-properties.md), lub [wiadomości](../debugger/how-to-display-message-properties.md).  
  
- Wybierz okno, wątek, proces lub komunikatów bezpośrednio w widoku.  
  
- Użyj [Wyszukiwarka](../debugger/how-to-use-the-finder-tool.md) wybrać okna, umieszczając wskaźnik myszy.  
  
- Ustaw **komunikatów opcje** przy użyciu złożonych komunikatu dziennika wybór parametrów.  
  
  Spy ++ zawiera pasek narzędzi i hiperłączy, które pozwalają pracować szybciej. Zapewnia także **Odśwież** polecenie, aby zaktualizować widoku aktywnego **narzędzie Window Finder** umożliwiają łatwiejsze w obsłudze, szpiegowanie i **czcionki** okno dialogowe, aby dostosować widok systemu windows. Ponadto narzędzie Spy ++ umożliwia zapisywanie i przywracanie preferencji użytkownika.  
  
  W różnych Spy ++ w systemie windows możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów z najczęściej używanymi poleceniami. Polecenia, które są wyświetlane, zależy od tego, gdzie jest wskaźnik. Na przykład kliknij prawym przyciskiem myszy wpis w widoku okna, a wybrane okno jest widoczne, następnie kliknięcie **wyróżnić** na skrót menu powoduje, że obramowania okna wybranego do flash, aby można go odnaleźć łatwiejsze.  
  
> [!NOTE]
> Istnieją dwa narzędzia, które przypominają Spy ++: PView, który przedstawia szczegółowe informacje dotyczące procesów i wątków oraz DDESPY. Plik EXE, który umożliwia monitorowanie komunikatów dynamicznej wymiany danych (DDE).  
  
## <a name="64-bit-operating-systems"></a>64-bitowych systemach operacyjnych  
 Istnieją dwie wersje programu Spy ++. Pierwsza wersja, o nazwie Spy ++ (spyxx.exe) jest przeznaczony do wyświetlania komunikatów wysłanych do okno, w którym jest uruchomiony w procesie 32-bitowym. Na przykład programu Visual Studio działa w procesie 32-bitowych. W związku z tym, służy narzędzie Spy ++ do wyświetlania komunikatów wysłanych do **Eksploratora rozwiązań**. Ponieważ konfigurację domyślną dla większości kompilacje w programie Visual Studio jest uruchamiane w procesie 32-bitowych, pierwszej wersji programu Spy ++ jest ten, który jest dostępny na **narzędzia** menu w programie Visual Studio.  
  
 Druga wersja, o nazwie Spy ++ (64-bitowy) (spyxx_amd64.exe) jest przeznaczony do wyświetlania komunikatów wysłanych do okno, w którym jest uruchomiony w procesie 64-bitowym. Na przykład na 64-bitowym systemie operacyjnym Notatnik działa w procesie 64-bitowych. W związku z tym służy narzędzie Spy ++ (64-bitowy) aby wyświetlić komunikaty wysyłane do Notatnika. Spy ++ (64-bitowy) znajduje się w  
  
 .. \\ *Folder instalacji programu visual Studio*\Common7\Tools\spyxx_amd64.exe.  
  
 Uruchom z dowolnej wersji programu Spy ++, bezpośrednio z poziomu wiersza polecenia.  
  
> [!NOTE]
> Mimo że Spy ++ (64-bitowy) nazwa zawiera "amd", działa na dowolnej x64 systemu operacyjnego Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z programu Spy ++](../debugger/using-spy-increment.md)   
 [Widoków programu Spy ++](../debugger/spy-increment-views.md)   
 [Spy++ — dokumentacja](../debugger/spy-increment-reference.md)
