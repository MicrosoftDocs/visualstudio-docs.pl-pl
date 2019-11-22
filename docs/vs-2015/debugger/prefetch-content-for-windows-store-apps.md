---
title: Zawartość z wyprzedzeniem dla aplikacji ze sklepu Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac6479b4dbb0815374174140deb0d660636ac9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300523"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Zawartość pobrana z wyprzedzeniem dla aplikacji Sklepu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dotyczy tylko Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Aby zwiększyć wydajność aplikacji ze sklepu Windows, możesz zażądać systemu Windows do wstępnego załadowania niektórych zawartości sieci Web, takich jak strony sieci Web lub obrazy,[do pamięci](https://msdn.microsoft.com/library/aa383630.aspx)podręcznej [WinInet w](https://msdn.microsoft.com/0a06f2af-957a-4dff-a8cc-187370181b5c)aplikacji. Ta funkcja jest nazywana funkcją pobierania z wyprzedzeniem. Jest to szczególnie przydatne w przypadku zawartości, która jest używana podczas uruchamiania, ale można również korzystać z innej często używanej zawartości. Metody klasy [Windows. Networking. BackgroundTransfer. ContentPrefetcher](https://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) umożliwiają określanie identyfikatorów URI zawartości, która ma zostać wstępnie Załaduj.  
  
 System Windows używa algorytmów heurystycznych w celu ustalenia, kiedy i w jaki sposób należy pobrać pobieranie i jakie zasoby zostaną pobrane. Algorytmy heurystyczne uwzględniają warunki sieciowe i systemowe, historię użycia aplikacji użytkownika oraz wyniki wcześniejszych prób pobrania. W programie Visual Studio można użyć polecenia **Wyzwalaj pobieranie z aplikacji ze sklepu Windows** , aby wymusić ignorowanie przez system Windows heurystycznych algorytmów ContentPrefetcher i wstępnego ładowania całej określonej zawartości sieci Web. Może to być przydatne, jeśli chcesz przetestować zachowanie aplikacji lub wydajność z zawartością do pobrania z wyprzedzeniem w znanym stanie (załadowanym lub niezaładowanym).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Aby wymusić wstępne ładowanie określonych zasobów ContentPrefetcher  
 W tej procedurze przyjęto założenie, że skonfigurowano już funkcję ContentPrefetcher i określono identyfikatory URI zawartości do wstępnego ładowania w projekcie aplikacji. Aby wymusić wstępne ładowanie zawartości, gdy określone zasoby są nowe lub zmodyfikowane, należy uruchomić i zatrzymać aplikację przed wybraniem polecenia **Wyzwalaj pobieranie z wyprzedzeniem aplikacji ze sklepu Windows** . Najpierw uruchom aplikację, aby zarejestrować identyfikatory URI. **Wyzwól polecenie pobrania z wyprzedzeniem aplikacji ze sklepu Windows** wymusza pobranie przez ContentPrefetcher zawartości i dodanie jej do pamięci podręcznej. W kolejnych uruchomieniach aplikacji można założyć, że zawartość jest wstępnie załadowana.  
  
1. Uruchom aplikację, aby zarejestrować identyfikatory URI zawartości z wyprzedzeniem przy użyciu aplikacji. W menu **debugowanie** wybierz **Rozpocznij debugowanie** (skrót klawiaturowy: F5).  
  
2. W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (skrót klawiaturowy: Shift + F5).  
  
3. W menu **debugowanie** wybierz **inne elementy docelowe debugowania** , a następnie wybierz kolejno opcje **Wyzwalaj pobieranie aplikacji ze sklepu Windows**.  
  
   Można teraz debugować, testować i analizować aplikację przy użyciu prepobranych zasobów sieci Web.  
  
> [!NOTE]
> Powtórz te czynności za każdym razem, gdy dodasz lub zmodyfikujesz określoną zawartość sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Wpis w blogu: wyzwalanie pobierania z wyprzedzeniem dla aplikacji ze sklepu Windows w Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
