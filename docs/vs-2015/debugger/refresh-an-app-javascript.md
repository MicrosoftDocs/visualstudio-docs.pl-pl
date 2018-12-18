---
title: Odświeżanie aplikacji (JavaScript) | Dokumentacja firmy Microsoft
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
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1905d48e79567684da6215b419c348b32721e0e3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722894"
---
# <a name="refresh-an-app-javascript"></a>Odświeżanie aplikacji (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ma to zastosowanie, Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Można wprowadzić zmiany do kodu podczas debugowania, a następnie Odśwież app Store, przy użyciu języka JavaScript, wybierając **aplikacji Windows Odśwież** znajdujący się na **debugowania** paska narzędzi. Wybranie tego przycisku ponownie ładuje aplikację bez zatrzymywania i ponownego uruchamiania debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript i szybko wyświetlić wyniki. Ta funkcja jest obsługiwana dla aplikacji Windows Store i Windows Phone Store.  
  
 Odświeżanie nie zarządzania stanem swojej aplikacji lub uwzględnić następujące zmiany w aplikacji:  
  
-   Zmiany pliku manifestu pakietu, w tym zmiany w manifeście pakietu obrazów.  
  
-   Odwołanie zmiany, takie jak dodawanie lub usuwanie odwołania zestawu SDK lub zmiana składników środowiska wykonawczego Windows (winmd).  
  
-   Zmiany zasobów, takich jak zmiany na ciągi w plikach .resjson.  
  
-   Zmiany pliku projektu, które powodują zmiany nazwy ścieżki, nowe pliki projektu lub usunięte pliki.  
  
-   Zmiany właściwości projektów i elementów, takich jak zmiany na wybranym urządzeniu debugowania lub zmiany Akcja pakietu dla pliku (w oknie dialogowym Właściwości).  
  
> [!IMPORTANT]
>  Podczas zmiany odwołania, zmień manifest pakietu lub wprowadzić inne zmiany, określone w powyższej liście musisz zatrzymać i ponownie uruchomić debugera, aby zaktualizować pliki źródłowe HTML, CSS i JavaScript.  
  
### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikację  
  
1.  W programie Visual Studio Utwórz nowy projekt za pomocą szablonu projektu aplikacja nawigacji.  
  
     Może to być aplikacji Windows Store, Windows Phone Store aplikacji lub aplikacji uniwersalnej.  
  
2.  Za pomocą szablonu Otwórz w programie Visual Studio, wybierz element docelowy debugowania.  
  
     Jeśli projekt Windows Phone jest bieżący projekt startowy, zaznacz to emulator Windows Phone dla elementu docelowego debugowania. W przeciwnym razie wybierz **symulator** lub **komputera lokalnego**.  
  
     ![Wybierz opcję debugowania listy docelowej](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3.  Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
4.  Przełącz się do programu Visual Studio. (Naciśnij klawisz F12).  
  
5.  W **Eksploratora rozwiązań**w **stron** > **macierzystego** folder, otwórz home.html.  
  
6.  Zmień tekst tytułu strony z  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     się czymś innym, w następujący sposób:  
  
    ```html  
    Hello!  
    ```  
  
7.  Kliknij przycisk **aplikacji Windows Odśwież** przycisku, który wygląda następująco: ![przycisku aplikacji Windows Odśwież](../debugger/media/js-refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4).  
  
8.  Przełącz się do aplikacji. Aplikacja zostanie ponownie załadowana bez debugera, ponowne uruchomienie i pojawi się nowy tytuł strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)



