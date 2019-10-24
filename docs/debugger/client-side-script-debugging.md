---
title: Debugowanie skryptu po stronie klienta | Microsoft Docs
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
ms.openlocfilehash: f9f66d757f5f46530619be1424eb0810ce546ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745701"
---
# <a name="client-side-script-debugging"></a>Debugowanie skryptu po stronie klienta
Debuger programu Visual Studio oferuje kompleksowe środowisko debugowania do znajdowania i poprawiania błędów w skryptach po stronie klienta na stronach ASP.NET.

## <a name="opening-script-documents"></a>Otwieranie dokumentów skryptów
Można wyświetlić listy dokumentów skryptów po stronie serwera i klienta w **Eksplorator rozwiązań** do wyświetlenia. Możesz otworzyć dowolny dokument skryptu z **Eksplorator rozwiązań**. Aby uzyskać więcej informacji, zobacz [How to: View Document scripts](../debugger/how-to-view-script-documents.md).

## <a name="breakpoint-mapping"></a>Mapowanie punktów przerwania
 W programie Visual Studio nie można bezpośrednio debugować kodu po stronie serwera, ale można ustawić punkt przerwania w pliku po stronie serwera. Program Visual Studio automatycznie mapuje punkt przerwania do odpowiedniej lokalizacji w pliku po stronie klienta i tworzy zamapowany punkt przerwania w kodzie po stronie klienta.

## <a name="manually-or-automatically-attaching-to-script"></a>Ręczne lub automatyczne dołączanie do skryptu
 Aby rozpocząć debugowanie skryptu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debuger musi dołączyć do skryptu, który chcesz debugować. Może to nastąpić ręcznie lub automatycznie.

 Możesz ręcznie dołączyć przy użyciu interfejsu debugera [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aby wybrać uruchomiony proces skryptu, do którego chcesz dołączyć. Aby uzyskać więcej informacji, zobacz [jak: dołączanie do skryptu](../debugger/how-to-attach-to-script.md).

 Debuger automatycznie dołącza do skryptu, gdy wystąpi jedno z następujących rzeczy:

- Osiągnięto zestaw punktów przerwania w skrypcie.

- W kodzie skryptu trafimy instrukcję VBScript `Stop` lub instrukcję `debugger` języka JScript.

- Przeglądarka lub serwer napotyka błąd składni lub czasu wykonania w skrypcie. W takim przypadku zostanie wyświetlone okno dialogowe z opcją rozpoczęcia debugowania.

  Po ręcznym dołączeniu do skryptu proces skryptu zostanie uruchomiony do momentu jego zatrzymania. Można go zatrzymać, wybierając pozycję **Przerwij** w menu **Debuguj** .

  Gdy debuger automatycznie dołączy, wykonywanie skryptu jest zatrzymywane w wierszu, w którym wystąpił punkt przerwania, instrukcję `Stop` lub instrukcję `debugger` lub błąd lub w punkcie, w którym wybrano rozpoczęcie debugowania w programie Internet Explorer.

  W tym momencie można rozpocząć debugowanie przy użyciu zwykłych obiektów debugera. Można na przykład użyć poleceń **Steps** , aby kontynuować wykonywanie kodu w wierszu. Można użyć okna **stosu wywołań** do wyświetlania i kontrolowania przepływu skryptu. Można użyć okien zmiennych lub okien **bezpośrednich** do wyświetlania lub zmiany zmiennych i właściwości.

## <a name="enhanced-error-messages-for-script-debugging"></a>Ulepszone komunikaty o błędach dotyczące debugowania skryptów
 Program Visual Studio udostępnia Ulepszone komunikaty o błędach dla typowych problemów z debugowaniem skryptów. Te komunikaty nie są wyświetlane, chyba że ręcznie dołączysz się do programu Internet Explorer. Jeśli wystąpi błąd podczas automatycznego otwierania programu Internet Explorer, spróbuj ręcznie dołączyć, aby wyświetlić komunikaty o błędach.

## <a name="debugging-ajax-script-applications"></a>Debugowanie aplikacji skryptów AJAX
 Aplikacje sieci Web obsługujące technologię AJAX wykorzystują duże wykorzystanie kodu skryptu i stanowią specjalne wyzwania dotyczące debugowania. Aby uzyskać informacje na temat technik debugowania AJAX, zobacz

 [Debugowanie i śledzenie aplikacji Ajax — Omówienie](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).

## <a name="see-also"></a>Zobacz także

- [Debugowanie aplikacji ASP.NET i AJAX](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)
- [Ograniczenia dotyczące debugowania skryptu](../debugger/limitations-on-script-debugging.md)
- [Zmienne okna](../debugger/debugger-windows.md)
- [Okno bezpośrednie](../ide/reference/immediate-window.md)
- [Debugowanie i śledzenie aplikacji Ajax — Omówienie](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)