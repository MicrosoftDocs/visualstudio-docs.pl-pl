---
title: Debugowanie kontrolki WebView (systemu Windows UWP) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: d55023b97397fa7d1b134c246c25b0d0b37a4d18
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790111"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>Debugowanie kontrolki WebView w aplikacji platformy uniwersalnej systemu Windows

 Do inspekcji i debugowania `WebView` formantów w aplikacji środowiska wykonawczego Windows, można skonfigurować programu Visual Studio, aby dołączyć debuger skryptów, po uruchomieniu aplikacji. Użytkownik ma dwa sposoby interakcji z `WebView` kontrolki za pomocą debugera:

-   Otwórz [narzędzia DOM Explorer](../debugger/quickstart-debug-html-and-css.md) dla `WebView` wystąpienia i Sprawdzanie elementów DOM, badać problemy dotyczące stylów CSS i mają zostać przetestowane dynamicznie renderowanych zmiany stylów.

-   Wybierz stronę sieci Web lub `iFrame` wyświetlane w `WebView` wystąpienia jako cel w [konsoli JavaScript](../debugger/javascript-console-commands.md) okna, a następnie współdziałał z sieci Web za pomocą polecenia konsoli. Konsolę zapewnia dostęp do bieżącego kontekstu wykonywania skryptu.

### <a name="attach-the-debugger-c-visual-basic-c"></a>Dołącz debuger (C#, Visual Basic, C++)

1.  W programie Visual Studio, należy dodać `WebView` kontrolki do aplikacji środowiska wykonawczego Windows.

2.  W Eksploratorze rozwiązań Otwórz właściwości projektu, wybierając **właściwości** z menu skrótów dla projektu.

3.  Wybierz **debugowania**. W **proces aplikacji** wybierz **skryptu**.

     ![Dołączanie debugera skryptów](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4.  (Opcjonalnie) Wersji non-Express programu Visual Studio, należy wyłączyć debugowanie just-in-time (JIT), wybierając **Narzędzia > Opcje > debugowanie > Just-In-Time**, a następnie wyłączenie JIT debugowania skryptu.

    > [!NOTE]
    >  Debugowanie JIT jest wyłączona, można ukryć, okna dialogowe dla nieobsłużonych wyjątków, które występują w niektórych witrynach sieci Web. W programie Visual Studio Express debugowanie JIT zawsze jest wyłączona.

5.  Naciśnij klawisz F5, aby rozpocząć debugowanie.

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Skorzystaj z Eksploratora modelu DOM do inspekcji i debugowanie kontrolki WebView

1.  (C#, Visual Basic, C++) Dołączanie debugera skryptów do swojej aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.

2.  Jeśli jeszcze nie, Dodaj `WebView` kontrolę aplikacji, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.

3.  Przejdź do strony `Webview` kontrolkach.

4.  Otwórz okno Eksploratora DOM `WebView` kontroli, wybierając **debugowania**, **Windows**, **narzędzia DOM Explorer**, a następnie wybierz adres URL `WebView` , chcesz sprawdzić.

     ![Otwieranie Eksploratora DOM](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     Eksplorator DOM skojarzony z `WebView` pojawia się jako nowa karta w programie Visual Studio.

5.  Wyświetlanie i modyfikowanie elementów DOM na żywo i style CSS, zgodnie z opisem w [stylów CSS debugowania przy użyciu narzędzia DOM Explorer](/visualstudio/debugger/quickstart-debug-html-and-css).

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Korzystanie z okna konsoli języka JavaScript do inspekcji i debugowanie kontrolki WebView

1.  (C#, Visual Basic, C++) Dołączanie debugera skryptów do swojej aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.

2.  Jeśli jeszcze nie, Dodaj `WebView` kontrolę aplikacji, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.

3.  Otwieranie okna konsoli języka JavaScript dla `WebView` kontroli, wybierając **debugowania**, **Windows**, **konsoli JavaScript**.

     Zostanie wyświetlone okno konsoli JavaScript.

4.  Przejdź do strony `Webview` kontrolkach.

5.  W oknie konsoli, wybierz stronę sieci Web lub `iFrame` wyświetlane przez `WebView` w kontrolce **docelowej** listy.

     ![Docelowa wybierane w oknie konsoli JavaScript](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    >  Za pomocą konsoli, możesz wchodzić w interakcje za pomocą jednego `WebView`, `iFrame`, udostępnić kontraktu lub internetowych procesów roboczych w danym momencie. Każdy element wymaga oddzielnego wystąpienia hosta platformy sieci web (WWAHost.exe). Możesz korzystać z jednego hosta w danym momencie.

6.  Wyświetlanie i modyfikację zmiennych w swojej aplikacji lub użyj polecenia konsoli, zgodnie z opisem w [Szybki Start: Debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).

## <a name="see-also"></a>Zobacz też

- [Szybki start: Debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)