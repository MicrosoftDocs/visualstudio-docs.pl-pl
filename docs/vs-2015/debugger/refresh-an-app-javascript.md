---
title: Odświeżanie aplikacji (JavaScript) | Microsoft Docs
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
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5b8be97212f4510002a78e6565fc9884930db89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808016"
---
# <a name="refresh-an-app-javascript"></a>Odświeżanie aplikacji (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy systemów Windows i Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Podczas debugowania można wprowadzać zmiany w kodzie, a następnie odświeżyć aplikację ze sklepu przy użyciu języka JavaScript, wybierając przycisk **Odśwież aplikację systemu Windows** na pasku narzędzi **debugowania** . Wybranie tego przycisku spowoduje ponowne załadowanie aplikacji bez zatrzymywania i ponownego uruchamiania debugera. Funkcja odświeżania umożliwia modyfikowanie kodu HTML, CSS i JavaScript oraz szybkie wyświetlanie wyników. Ta funkcja jest obsługiwana dla aplikacji ze sklepu Windows i Windows Phone sklepu.  
  
 Odświeżanie nie utrzymuje stanu aplikacji ani nie odzwierciedla następujących zmian w aplikacji:  
  
- Zmiany pliku manifestu pakietu, w tym zmiany obrazów określone w manifeście pakietu.  
  
- Zmiany odniesienia, takie jak dodawanie lub usuwanie odwołania do zestawu SDK lub zmiany składników środowisko wykonawcze systemu Windows (plików winmd).  
  
- Zmiany zasobów, takie jak zmiany w ciągach w plikach. resjson.  
  
- Plik projektu zmienia się w wyniku zmiany nazwy ścieżki, nowych plików projektu lub usuniętych plików.  
  
- Zmiany właściwości projektu i elementu, takie jak zmiany w wybranym urządzeniu debugowania, lub zmiany akcji pakietu dla pliku (w okno Właściwości).  
  
> [!IMPORTANT]
> Po zmianie odwołań, zmianie manifestu pakietu lub wprowadzeniu innych zmian określonych na poprzedniej liście należy zatrzymać i ponownie uruchomić debuger, aby zaktualizować pliki źródłowe HTML, CSS i JavaScript.  
  
### <a name="to-refresh-an-app"></a>Aby odświeżyć aplikację  
  
1. W programie Visual Studio Utwórz nowy projekt za pomocą szablonu projektu aplikacja nawigacji.  
  
     Może to być aplikacja ze sklepu Windows, aplikacja ze sklepu Windows Phone lub aplikacja uniwersalna.  
  
2. Przy otwartym szablonie w programie Visual Studio wybierz element docelowy debugowania.  
  
     Jeśli projekt Windows Phone jest bieżącym projektem startowym, wybierz Windows Phone Emulator dla elementu docelowego debugowania. W przeciwnym razie wybierz opcję **symulator** lub **komputer lokalny**.  
  
     ![Wybierz listę obiektów docelowych debugowania](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3. Naciśnij klawisz F5, aby uruchomić aplikację w trybie debugowania.  
  
4. Przejdź do programu Visual Studio. (Naciśnij klawisz F12).  
  
5. W **Eksplorator rozwiązań**w folderze głównym **stron**  >  **home** Otwórz home.html.  
  
6. Zmień tekst tytułu strony z  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     na coś innego:  
  
    ```html  
    Hello!  
    ```  
  
7. Kliknij przycisk **Odśwież aplikację systemu Windows** , który wygląda podobnie do tego: ![Odśwież przycisk aplikacji systemu Windows](../debugger/media/js-refresh.png "JS_Refresh"). (Lub naciśnij klawisz F4).  
  
8. Przejdź do aplikacji. Aplikacja zostanie załadowana ponownie bez ponownego uruchomienia debugera i zostanie wyświetlona nowa nazwa strony.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start: debugowanie kodu HTML i CSS](../debugger/quickstart-debug-html-and-css.md)
