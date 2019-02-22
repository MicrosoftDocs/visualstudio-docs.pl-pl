---
title: Debugowanie skryptu po stronie klienta | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1501cd0243d6dc17cc627715eda85e755aec4502
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637103"
---
# <a name="client-side-script-debugging"></a>Debugowanie skryptu po stronie klienta
Debuger programu Visual Studio zapewnia kompleksowe środowisko debugowania do znajdowania i poprawiania błędów w skryptach po stronie klienta na stronach ASP.NET.

## <a name="opening-script-documents"></a>Otwieranie dokumentów skryptu
Można wyświetlić listy dokumentów skryptów po stronie serwera i klienta w **Eksploratora rozwiązań** do wyświetlenia. Możesz otworzyć dowolny dokument skryptu z **Eksploratora rozwiązań**. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie dokumentów skryptu](../debugger/how-to-view-script-documents.md).

## <a name="breakpoint-mapping"></a>Mapowanie punktów przerwania
 W programie Visual Studio nie można bezpośrednio debugować kodu po stronie serwera, ale można ustawić punkt przerwania w pliku po stronie serwera. Visual Studio automatycznie mapuje punkt przerwania do odpowiedniej lokalizacji w pliku po stronie klienta i tworzy mapowany punkt przerwania w kodzie po stronie klienta.

## <a name="manually-or-automatically-attaching-to-script"></a>Ręczne lub automatyczne dołączanie do skryptu
 Aby rozpocząć debugowanie skryptu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debuger należy dołączyć do skryptu, który chcesz debugować. Można to zrobić ręcznie lub automatycznie.

 Można przyłączyć ręcznie używając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu debugera do wybrania czynnego procesu skryptu, którego chcesz dołączyć do. Aby uzyskać więcej informacji, zobacz [jak: Dołączanie do skryptu](../debugger/how-to-attach-to-script.md).

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

 [Debugowanie i śledzenie — Przegląd aplikacji Ajax](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).

## <a name="see-also"></a>Zobacz też

- [Debugowanie aplikacji ASP.NET i AJAX](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)
- [Ograniczenia dotyczące debugowania skryptu](../debugger/limitations-on-script-debugging.md)
- [Windows zmiennej](../debugger/debugger-windows.md)
- [Okno bezpośrednie](../ide/reference/immediate-window.md)
- [Debugowanie i śledzenie Ajax aplikacje — Przegląd](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)