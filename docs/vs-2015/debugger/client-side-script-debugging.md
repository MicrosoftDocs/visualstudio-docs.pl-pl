---
title: Debugowanie skryptu po stronie klienta | Microsoft Docs
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6405a35068b7be7ac93eb91f4d9100e6a840b0bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702376"
---
# <a name="client-side-script-debugging"></a>Debugowanie skryptu po stronie klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio oferuje kompleksowe środowisko debugowania do znajdowania i poprawiania błędów w skryptach po stronie klienta na stronach ASP.NET.  
  
## <a name="opening-script-documents"></a>Otwieranie dokumentów skryptów  
 Można wyświetlić listy dokumentów skryptów po stronie serwera i klienta w **Eksplorator rozwiązań** do wyświetlenia. Możesz otworzyć dowolny dokument skryptu z **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [How to: View Document scripts](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapowanie punktów przerwania  
 W programie Visual Studio nie można bezpośrednio debugować kodu po stronie serwera, ale można ustawić punkt przerwania w pliku po stronie serwera. Program Visual Studio automatycznie mapuje punkt przerwania do odpowiedniej lokalizacji w pliku po stronie klienta i tworzy zamapowany punkt przerwania w kodzie po stronie klienta.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Ręczne lub automatyczne dołączanie do skryptu  
 Aby rozpocząć debugowanie skryptu w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , debuger musi dołączyć do skryptu, który chcesz debugować. Może to nastąpić ręcznie lub automatycznie.  
  
 Możesz ręcznie dołączyć przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu debugera, aby wybrać uruchomiony proces skryptu, do którego chcesz dołączyć. Aby uzyskać więcej informacji, zobacz [jak: dołączanie do skryptu](../debugger/how-to-attach-to-script.md).  
  
 Debuger automatycznie dołącza do skryptu, gdy wystąpi jedno z następujących rzeczy:  
  
- Osiągnięto zestaw punktów przerwania w skrypcie.  
  
- Trafimy do instrukcji języka VBScript `Stop` lub `debugger` instrukcji języka JScript w kodzie skryptu.  
  
- Przeglądarka lub serwer napotyka błąd składni lub czasu wykonania w skrypcie. W takim przypadku zostanie wyświetlone okno dialogowe z opcją rozpoczęcia debugowania.  
  
  Po ręcznym dołączeniu do skryptu proces skryptu zostanie uruchomiony do momentu jego zatrzymania. Można go zatrzymać, wybierając pozycję **Przerwij** w menu **Debuguj** .  
  
  Gdy debuger automatycznie dołączy, wykonywanie skryptu jest zatrzymywane w wierszu, w którym wystąpił punkt przerwania, `Stop` instrukcję lub `debugger` instrukcję lub w punkcie, w którym wybrano rozpoczęcie debugowania w programie Internet Explorer.  
  
  W tym momencie można rozpocząć debugowanie przy użyciu zwykłych obiektów debugera. Można na przykład użyć poleceń **Steps** , aby kontynuować wykonywanie kodu w wierszu. Można użyć okna **stosu wywołań** do wyświetlania i kontrolowania przepływu skryptu. Można użyć okien zmiennych lub okien **bezpośrednich** do wyświetlania lub zmiany zmiennych i właściwości.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Ulepszone komunikaty o błędach dotyczące debugowania skryptów  
 Program Visual Studio udostępnia Ulepszone komunikaty o błędach dla typowych problemów z debugowaniem skryptów. Te komunikaty nie są wyświetlane, chyba że ręcznie dołączysz się do programu Internet Explorer. Jeśli wystąpi błąd podczas automatycznego otwierania programu Internet Explorer, spróbuj ręcznie dołączyć, aby wyświetlić komunikaty o błędach.  
  
## <a name="debugging-ajax-script-applications"></a>Debugowanie aplikacji skryptów AJAX  
 Aplikacje sieci Web obsługujące technologię AJAX wykorzystują duże wykorzystanie kodu skryptu i stanowią specjalne wyzwania dotyczące debugowania. Aby uzyskać informacje na temat technik debugowania AJAX, zobacz  
  
 [Debugowanie i śledzenie aplikacji Ajax — Omówienie](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Ograniczenia dotyczące debugowania skryptów](../debugger/limitations-on-script-debugging.md)   
 [Zmienne okna](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Debugowanie i śledzenie aplikacji Ajax — Omówienie](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
