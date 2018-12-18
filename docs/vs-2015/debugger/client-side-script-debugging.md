---
title: Debugowanie skryptu po stronie klienta | Dokumentacja firmy Microsoft
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
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3aa04ab77b6e3dc6264a517c83c4ed319f36d686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817805"
---
# <a name="client-side-script-debugging"></a>Debugowanie skryptu po stronie klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio zapewnia kompleksowe środowisko debugowania do znajdowania i poprawiania błędów w skryptach po stronie klienta na stronach ASP.NET.  
  
## <a name="opening-script-documents"></a>Otwieranie dokumentów skryptu  
 Można wyświetlić listy dokumentów skryptów po stronie serwera i klienta w **Eksploratora rozwiązań** do wyświetlenia. Możesz otworzyć dowolny dokument skryptu z **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie dokumentów skryptu](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mapowanie punktów przerwania  
 W programie Visual Studio nie można bezpośrednio debugować kodu po stronie serwera, ale można ustawić punkt przerwania w pliku po stronie serwera. Visual Studio automatycznie mapuje punkt przerwania do odpowiedniej lokalizacji w pliku po stronie klienta i tworzy mapowany punkt przerwania w kodzie po stronie klienta.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Ręczne lub automatyczne dołączanie do skryptu  
 Aby rozpocząć debugowanie skryptu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], debuger należy dołączyć do skryptu, który chcesz debugować. Można to zrobić ręcznie lub automatycznie.  
  
 Można przyłączyć ręcznie używając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu debugera do wybrania czynnego procesu skryptu, którego chcesz dołączyć do. Aby uzyskać więcej informacji, zobacz [porady: dołączanie do skryptu](../debugger/how-to-attach-to-script.md).  
  
 Debuger automatycznie dołącza do skryptu, gdy wystąpi jedno z następujących czynności:  
  
- Zostanie trafiony punkt przerwania w skrypcie.  
  
- Osiągasz instrukcję VBScript `Stop` lub instrukcję JScript `debugger` instrukcji w kodzie skryptu.  
  
- Przeglądarka lub serwer napotyka składni lub uruchom błąd w skrypcie. W takiej sytuacji pojawi się okno dialogowe i mogli rozpocząć debugowanie.  
  
  Po dołączeniu ręcznie do skryptu, proces skryptu będzie nadal działać do momentu zatrzymywania. Można to zatrzymać wybierając **Przerwij** na **debugowania** menu.  
  
  Gdy automatycznie dołączany jest debuger, wykonywanie skryptu jest zatrzymywane w wierszu gdzie punkt przerwania, `Stop` instrukcji lub `debugger` instrukcji lub błąd wystąpił, lub w momencie, gdy wybrano opcję Rozpocznij debugowanie w programie Internet Explorer.  
  
  W tym momencie można użyć normalnych obiektów debugera, aby rozpocząć debugowanie. Na przykład, można użyć **kroku** poleceń, aby kontynuować wykonywanie kodu wiersz po wierszu. Możesz użyć **stos wywołań** okna do przeglądania i kontrolowania przepływu skryptu. Można użyć okien zmiennej lub **bezpośrednie** okna, aby wyświetlić lub zmienić zmienne i właściwości.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Ulepszone komunikaty o błędach dotyczące debugowania skryptów  
 Visual Studio zapewnia ulepszone komunikaty o błędach dla typowych problemów debugowania skryptu. Te komunikaty nie są wyświetlane, jeśli nie dołączysz do programu Internet Explorer ręcznie. Jeśli wystąpi błąd, po otwarciu programu Internet Explorer automatycznie, spróbuj ręcznego dołączania, dzięki czemu można zobaczyć komunikaty o błędach.  
  
## <a name="debugging-ajax-script-applications"></a>Aplikacje debugowania skryptów AJAX  
 Aplikacje sieci Web z włączoną obsługą technologii AJAX intensywnie korzystają z kod skryptu i stanowią szczególne wyzwanie dla debugowania. Aby uzyskać informacje na temat technik debuggowania AJAX zobacz  
  
 [Debugowanie i śledzenie — Przegląd aplikacji Ajax](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Ograniczenia debugowania skryptu](../debugger/limitations-on-script-debugging.md)   
 [Windows zmiennej](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Okno bezpośrednie](../ide/reference/immediate-window.md)   
 [Debugowanie i śledzenie Ajax aplikacje — Przegląd](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)



