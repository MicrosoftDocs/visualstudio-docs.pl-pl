---
title: Wprowadzenie do narzędzia Spy + + | Microsoft Docs
description: Przeczytaj o narzędziu do debugowania programu Spy + +. Wyświetla graficzne drzewo relacji obiektu systemowego. Pobierz właściwości wybranych okien, wątków, procesów lub komunikatów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eefc69d7dbd7d05eaadc3e9fe8976c0ff03c9a30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910018"
---
# <a name="introducing-spy"></a>Wprowadzenie programu Spy++
Program Spy + + umożliwia wykonywanie następujących zadań:

- Wyświetlanie graficznego drzewa relacji między obiektami systemowymi. Obejmują one [procesy](../debugger/processes-view.md), [wątki](../debugger/threads-view.md)i [okna](../debugger/windows-view.md).

- Wyszukaj określone [okna](../debugger/how-to-search-for-a-window-in-windows-view.md), [wątki](../debugger/how-to-search-for-a-thread-in-threads-view.md), [procesy](../debugger/how-to-search-for-a-process-in-processes-view.md)lub [komunikaty](../debugger/how-to-search-for-a-message-in-messages-view.md).

- Wyświetlanie właściwości wybranych [okien](../debugger/how-to-display-window-properties.md), [wątków](../debugger/how-to-display-thread-properties.md), [procesów](../debugger/how-to-display-process-properties.md)lub [komunikatów](../debugger/how-to-display-message-properties.md).

- Wybierz okno, wątek, proces lub komunikat bezpośrednio w widoku.

- Użyj [Narzędzia wyszukiwania](../debugger/how-to-use-the-finder-tool.md) , aby wybrać okno według położenia wskaźnika myszy.

- Ustaw [opcję wiadomości](../debugger/how-to-open-messages-view-from-find-window.md) za pomocą złożonych parametrów wyboru dziennika komunikatów.

  W programie Spy + + znajduje się pasek narzędzi i hiperlinki ułatwiające szybsze działanie. Udostępnia również polecenie **Refresh** służące do aktualizowania aktywnego widoku, narzędzia do **wyszukiwania okna** , które ułatwia przez, oraz okna dialogowego **czcionka** do dostosowywania okien wyświetlania. Ponadto program Spy + + umożliwia zapisanie i przywrócenie preferencji użytkownika.

  W różnych oknach systemu Spy + + można kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów często używanych poleceń. Które polecenia są wyświetlane, zależy od tego, gdzie znajduje się wskaźnik. Na przykład, jeśli klikniesz prawym przyciskiem myszy wpis w widoku okna, a wybrane okno jest widoczne, a następnie klikniesz polecenie **wyróżnienie** w menu skrótów powoduje, że obramowanie wybranego okna ma być łatwiejsze do zlokalizowania.

> [!NOTE]
> Istnieją dwa inne narzędzia podobne do Spy + +: PView, które przedstawiają szczegółowe informacje o procesach i wątkach oraz DDESPY.EXE, które umożliwiają monitorowanie komunikatów dynamicznej wymiany danych (DDE).

## <a name="64-bit-operating-systems"></a>64-bitowe systemy operacyjne
 Istnieją dwie wersje programu Spy + +. Pierwsza wersja o nazwie Spy + + (spyxx.exe) została zaprojektowana tak, aby wyświetlała komunikaty wysyłane do okna działającego w procesie 32-bitowym. Na przykład program Visual Studio działa w procesie 32-bitowym. W związku z tym możesz użyć programu Spy + + do wyświetlania komunikatów wysyłanych do **Eksplorator rozwiązań**. Ponieważ konfiguracja domyślna dla większości kompilacji w programie Visual Studio jest uruchamiana w procesie 32-bitowym, ta pierwsza wersja programu Spy + + jest taka, która jest dostępna w menu **Narzędzia** w programie Visual Studio, jeśli [wymagane składniki są zainstalowane](../debugger/how-to-start-spy-increment.md).

 Druga wersja o nazwie Spy + + (64-bitowa) (spyxx_amd64.exe) została zaprojektowana tak, aby wyświetlała komunikaty wysyłane do okna, które jest uruchomione w procesie 64-bitowym. Na przykład w 64-bitowym systemie operacyjnym Notatnik działa w procesie 64-bitowym. W związku z tym możesz użyć programu Spy + + (64-bitowe) do wyświetlania komunikatów wysyłanych do Notatnika. Spy + + (64-bitowe) zwykle znajduje się w

 ..\\\Common7\Tools\spyxx_amd64.exe *folderu instalacyjnego programu Visual Studio* .

 Każdą wersję programu Spy + + można uruchomić bezpośrednio z wiersza polecenia.

> [!NOTE]
> Mimo że nazwa pliku Spy + + (64-bitowa) zawiera wartość "AMD", jest uruchamiana w dowolnym systemie operacyjnym Windows w wersji x64.

## <a name="see-also"></a>Zobacz też
- [Porady: korzystanie z programu Spy++](../debugger/how-to-start-spy-increment.md)
- [Korzystanie z programu Spy++](../debugger/using-spy-increment.md)
- [Spy++ — Widoki](../debugger/spy-increment-views.md)
- [Spy++ — Odwołanie](../debugger/spy-increment-reference.md)