---
title: Debuguj przy użyciu prepobranej zawartości w aplikacjach platformy UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 28a73974a71df7fa652e4b246043e901df76e94c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730572"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debuguj aplikacje platformy UWP przy użyciu prepobranej zawartości w programie Visual Studio

 Aby zwiększyć wydajność aplikacji platformy UWP, możesz poprosić system Windows o wstępne załadowanie niektórych zawartości sieci Web, takich jak strony sieci Web lub obrazy, do pamięci podręcznej [WinInet](/windows/desktop/WinInet/about-wininet) aplikacji. Ta funkcja jest nazywana funkcją pobierania z wyprzedzeniem. Jest to szczególnie przydatne w przypadku zawartości, która jest używana podczas uruchamiania, ale można również korzystać z innej często używanej zawartości. Metody klasy [Windows. Networking. BackgroundTransfer. ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) umożliwiają określanie identyfikatorów URI zawartości, która ma zostać wstępnie Załaduj. Zapoznaj się z [przykładem pobierania z wyprzedzeniem Windows SDK zawartości](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) , aby zapoznać się z przykładami dodawania funkcji ContentPrefetcher do aplikacji.

 System Windows używa algorytmów heurystycznych w celu ustalenia, kiedy i w jaki sposób należy pobrać pobieranie i jakie zasoby zostaną pobrane. Algorytmy heurystyczne uwzględniają warunki sieciowe i systemowe, historię użycia aplikacji użytkownika oraz wyniki wcześniejszych prób pobrania. W programie Visual Studio można użyć polecenia **Wyzwalaj pobieranie z aplikacji ze sklepu Windows** , aby wymusić ignorowanie przez system Windows heurystycznych algorytmów ContentPrefetcher i wstępnego ładowania całej określonej zawartości sieci Web. Może to być przydatne, jeśli chcesz przetestować zachowanie aplikacji lub wydajność z zawartością do pobrania z wyprzedzeniem w znanym stanie (załadowanym lub niezaładowanym).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Aby wymusić wstępne ładowanie określonych zasobów ContentPrefetcher
 W tej procedurze przyjęto założenie, że skonfigurowano już funkcję ContentPrefetcher i określono identyfikatory URI zawartości do wstępnego ładowania w projekcie aplikacji. Aby wymusić wstępne ładowanie zawartości, gdy określone zasoby są nowe lub zmodyfikowane, należy uruchomić i zatrzymać aplikację przed wybraniem polecenia **Wyzwalaj pobieranie z wyprzedzeniem aplikacji ze sklepu Windows** . Najpierw uruchom aplikację, aby zarejestrować identyfikatory URI. **Wyzwól polecenie pobrania z wyprzedzeniem aplikacji ze sklepu Windows** wymusza pobranie przez ContentPrefetcher zawartości i dodanie jej do pamięci podręcznej. W kolejnych uruchomieniach aplikacji można założyć, że zawartość jest wstępnie załadowana.

1. Uruchom aplikację, aby zarejestrować identyfikatory URI zawartości z wyprzedzeniem przy użyciu aplikacji. W menu **debugowanie** wybierz **Rozpocznij debugowanie** (skrót klawiaturowy: F5).

2. W menu **Debuguj** wybierz polecenie **Zatrzymaj debugowanie** (skrót klawiaturowy: Shift + F5).

3. W menu **debugowanie** wybierz **inne elementy docelowe debugowania** , a następnie wybierz kolejno opcje **Wyzwalaj pobieranie aplikacji ze sklepu Windows**.

   Można teraz debugować, testować i analizować aplikację przy użyciu prepobranych zasobów sieci Web.

> [!NOTE]
> Powtórz te czynności za każdym razem, gdy dodasz lub zmodyfikujesz określoną zawartość sieci Web.

## <a name="see-also"></a>Zobacz także
- [Wpis w blogu: wyzwalanie pobierania z wyprzedzeniem dla aplikacji ze sklepu Windows w Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)