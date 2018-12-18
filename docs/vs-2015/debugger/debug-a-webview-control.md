---
title: Debugowanie kontrolki WebView | Dokumentacja firmy Microsoft
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f8a4dcc64903b97e3b469fb962777e3b90f84ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729057"
---
# <a name="debug-a-webview-control"></a>Debugowanie kontrolki WebView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Do inspekcji i debugowania `WebView` formantów w aplikacji środowiska wykonawczego Windows, można skonfigurować programu Visual Studio, aby dołączyć debuger skryptów, po uruchomieniu aplikacji. Począwszy od programu Visual Studio 2013 Update 2, użytkownik ma dwa sposoby interakcji z `WebView` kontrolki za pomocą debugera:  
  
-   Otwórz [narzędzia DOM Explorer](../debugger/quickstart-debug-html-and-css.md) dla `WebView` wystąpienia i Sprawdzanie elementów DOM, badać problemy dotyczące stylów CSS i mają zostać przetestowane dynamicznie renderowanych zmiany stylów.  
  
-   Wybierz stronę sieci Web lub `iFrame` wyświetlane w `WebView` wystąpienia jako cel w [konsoli JavaScript](../debugger/javascript-console-commands.md) okna, a następnie współdziałał z sieci Web za pomocą polecenia konsoli. Konsolę zapewnia dostęp do bieżącego kontekstu wykonywania skryptu.  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>Dołącz debuger (C#, Visual Basic, C++)  
  
1.  W programie Visual Studio, należy dodać `WebView` kontrolki do aplikacji środowiska wykonawczego Windows.  
  
2.  W Eksploratorze rozwiązań Otwórz właściwości projektu, wybierając **właściwości** z menu skrótów dla projektu.  
  
3.  Wybierz **debugowania**. W **proces aplikacji** wybierz **skryptu**.  
  
     ![Dołączanie debugera skryptów](../debugger/media/js-dom-webview-script-debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (Opcjonalnie) Wersje non-Express programu Visual Studio można wyłączyć debugowanie just-in-time (JIT), wybierając **narzędzia**, **opcje**, **debugowanie**, **Just-In-Time**, a następnie wyłączenie JIT debugowania skryptu.  
  
    > [!NOTE]
    >  Debugowanie JIT jest wyłączona, można ukryć, okna dialogowe dla nieobsłużonych wyjątków, które występują w niektórych witrynach sieci Web. W programie Visual Studio Express debugowanie JIT zawsze jest wyłączona.  
  
5.  Naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>Skorzystaj z Eksploratora modelu DOM do inspekcji i debugowanie kontrolki WebView  
  
1.  (C#, Visual Basic, C++) Dołączanie debugera skryptów do swojej aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.  
  
2.  Jeśli jeszcze nie, Dodaj `WebView` kontrolę aplikacji, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
3.  Przejdź do strony `Webview` kontrolkach.  
  
4.  Otwórz okno Eksploratora DOM `WebView` kontroli, wybierając **debugowania**, **Windows**, **narzędzia DOM Explorer**, a następnie wybierz adres URL `WebView` , chcesz sprawdzić.  
  
     ![Otwieranie Eksploratora DOM](../debugger/media/js-dom-webview.png "JS_DOM_WebView")  
  
     Eksplorator DOM skojarzony z `WebView` pojawia się jako nowa karta w programie Visual Studio.  
  
5.  Wyświetlanie i modyfikowanie elementów DOM na żywo i style CSS, zgodnie z opisem w [stylów CSS debugowania przy użyciu narzędzia DOM Explorer](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>Korzystanie z okna konsoli języka JavaScript do inspekcji i debugowanie kontrolki WebView  
  
1.  (C#, Visual Basic, C++) Dołączanie debugera skryptów do swojej aplikacji. Zobacz sekcję pierwszą, aby uzyskać instrukcje.  
  
2.  Jeśli jeszcze nie, Dodaj `WebView` kontrolę aplikacji, a następnie naciśnij klawisz F5, aby rozpocząć debugowanie.  
  
3.  Otwieranie okna konsoli języka JavaScript dla `WebView` kontroli, wybierając **debugowania**, **Windows**, **konsoli JavaScript**.  
  
     Zostanie wyświetlone okno konsoli JavaScript.  
  
4.  Przejdź do strony `Webview` kontrolkach.  
  
5.  W oknie konsoli, wybierz stronę sieci Web lub `iFrame` wyświetlane przez `WebView` w kontrolce **docelowej** listy.  
  
     ![Docelowa wybierane w oknie konsoli JavaScript](../debugger/media/js-console-target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  Za pomocą konsoli, możesz wchodzić w interakcje za pomocą jednego `WebView`, `iFrame`, udostępnić kontraktu lub internetowych procesów roboczych w danym momencie. Każdy element wymaga oddzielnego wystąpienia hosta platformy sieci web (WWAHost.exe). Możesz korzystać z jednego hosta w danym momencie.  
  
6.  Wyświetlanie i modyfikację zmiennych w swojej aplikacji lub użyj polecenia konsoli, zgodnie z opisem w [Szybki Start: debugowanie kodu JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) i [polecenia konsoli JavaScript](../debugger/javascript-console-commands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)



