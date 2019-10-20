---
title: Opracowywanie aplikacji dla platforma uniwersalna systemu Windows (platformy UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ed601f6b3bfeba4d7aebed5955b340fb28908c74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660208"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dzięki platforma uniwersalna systemu Windows i naszym jednemu rdzeńowi systemu Windows można uruchomić tę samą aplikację na dowolnym urządzeniu z systemem Windows 10 z telefonów na komputerach stacjonarnych. Twórz te aplikacje uniwersalne systemu Windows za pomocą programu Visual Studio 2015 i narzędzi do tworzenia aplikacji uniwersalnych systemu Windows.

 ![platforma uniwersalna systemu Windows](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Uruchom aplikację na telefonie z systemem Windows 10, Windows 10 Desktop lub Xbox. Jest to ten sam pakiet aplikacji. Wraz z wprowadzeniem pojedynczego, ujednoliconego rdzeń systemu Windows 10 jeden pakiet aplikacji może być uruchamiany na wszystkich platformach. Kilka platform zawiera zestawy SDK rozszerzeń, które można dodać do aplikacji, aby korzystać z zachowań specyficznych dla platformy. Na przykład zestaw SDK rozszerzenia dla urządzeń przenośnych obsługuje naciśnięcie przycisku Wstecz w systemie Windows Phone. Jeśli odwołujesz się do zestawu SDK rozszerzenia w projekcie, po prostu Dodaj testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. Oznacza to, że możesz mieć ten sam pakiet aplikacji dla każdej platformy.

 **Co to jest rdzeń systemu Windows?**

 Po raz pierwszy system Windows został wdrożony jako wspólny rdzeń na wszystkich platformach Windows 10. Istnieje jedno wspólne źródło, jedno wspólne jądro systemu Windows, jeden stos plików we/wy i jeden model aplikacji. Dla interfejsu użytkownika istnieje tylko jedna struktura interfejsu użytkownika języka XAML i jedna struktura interfejsu użytkownika języka HTML. Dzięki temu możesz skoncentrować się na tworzeniu doskonałej aplikacji, ponieważ ułatwia ona uruchamianie aplikacji na różnych urządzeniach z systemem Windows 10.

 **Co to jest dokładnie platforma uniwersalna systemu Windows?**

 Jest to po prostu zbiór kontraktów i wersji. Umożliwiają one docelową lokalizację, w której można uruchomić aplikację. Nie jest już wskazywany system operacyjny. Teraz możesz przystąpić do aplikacji do co najmniej jednej rodziny urządzeń. Więcej informacji znajdziesz w tym [przewodniku po platformie](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

## <a name="requirements"></a>Wymagania
 Narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows są dostarczane z emulatorami, za pomocą których można zobaczyć, jak aplikacja wygląda na różnych urządzeniach. Jeśli chcesz używać tych emulatorów, musisz zainstalować to oprogramowanie na komputerze fizycznym. Na maszynie fizycznej musi działać system Windows 8.1 (x64) Professional Edition lub nowszy oraz procesor obsługujący funkcję Hyper-V klienta i translację adresów drugiego poziomu (SLAT). Emulatorów nie można używać, gdy program Visual Studio jest zainstalowany na maszynie wirtualnej.

 Poniżej znajduje się lista programów, które są potrzebne:

- [Windows 10](http://windows.microsoft.com/windows/downloads)

- [Program Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Upewnij się, że na liście funkcje opcjonalne są wybrane narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows. Bez tych narzędzi nie będziesz mieć możliwości tworzenia aplikacji uniwersalnych.

  Po zainstalowaniu tego oprogramowania musisz [włączyć urządzenie z systemem Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) na potrzeby programowania. (W przypadku każdego urządzenia z systemem Windows 10 nie jest już wymagana licencja dewelopera).

  **Obsługa Windows 8.1 i systemu Windows 7**

  Jeśli zdecydujesz się na programowanie aplikacji uniwersalnych systemu Windows za pomocą programu Visual Studio 2015 na platformie innej niż Windows 10, są to ograniczenia:

- Windows 8.1: nie można uruchomić aplikacji lokalnie (tylko na zdalnym urządzeniu z systemem Windows 10). Można użyć emulatorów w programie Visual Studio, ale nie do symulatora.

- Windows 7: nie można uruchomić aplikacji lokalnie (tylko na zdalnym urządzeniu z systemem Windows 10). Nie można użyć emulatorów ani symulatora w programie Visual Studio.

  Projektanta XAML można używać tylko wtedy, gdy platforma deweloperskia jest w systemie Windows 10.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows
 Wybierz preferowany język programistyczny C#od, Visual Basic C++ lub JavaScript, aby [utworzyć uniwersalną aplikację systemu Windows dla urządzeń z systemem Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Lub obejrzyj [to wideo z wprowadzeniem](http://channel9.msdn.com/Series/ConnectOn-Demand/229).

 Jeśli masz istniejące aplikacje ze sklepu Windows 8,1, aplikacje Windows Phone 8,1 lub aplikacje uniwersalne systemu Windows utworzone za pomocą programu Visual Studio 2015 RC, należy [przenieść te istniejące aplikacje](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) , aby używały najnowszych platforma uniwersalna systemu Windows.

 Po utworzeniu aplikacji uniwersalnej systemu Windows należy [spakować aplikację](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) , aby ją zainstalować na urządzeniu z systemem Windows 10 lub przesłać do sklepu Windows.
