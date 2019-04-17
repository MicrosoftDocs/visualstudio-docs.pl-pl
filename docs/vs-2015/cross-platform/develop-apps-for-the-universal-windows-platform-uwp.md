---
title: Twórz aplikacje dla platformy Universal Windows (UWP) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a273e3422c1ab96a0c5fdba8330b218b4b7640f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666770"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uniwersalnej platformy Windows i naszych jednego rdzenia Windows umożliwia uruchamianie tę samą aplikację na dowolnym urządzeniu z systemem Windows 10 z telefonów do komputerów stacjonarnych. Tworzenie aplikacji Windows Universal za pomocą programu Visual Studio 2015 i narzędzi Universal Windows App Development.  
  
 ![Platforma Universal Windows](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Uruchom aplikację na telefonie z systemem Windows 10, system Windows 10 desktop lub konsoli Xbox. To ten sam pakiet aplikacji! Wraz z wprowadzeniem core systemu Windows 10 w pojedynczą, jednolitą jednego pakietu aplikacji można uruchamiać na wszystkich platformach. Różnych platform mają zestawów SDK rozszerzeń, które można dodać do aplikacji, aby skorzystać z zachowań określonych platform. Na przykład zestawu SDK rozszerzenia dla urządzeń przenośnych obsługuje przycisku Wstecz naciśniętym na urządzeniu z systemem Windows phone. Jeśli odwołujesz rozszerzenie SDK w projekcie, wystarczy dodać testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. To, jak może mieć ten sam pakiet aplikacji dla każdej platformy.  
  
 **Co to jest podstawowa Windows?**  
  
 Po raz pierwszy Windows ma zostały zaprojektowane od nowa w zapewnienie wspólnej podstawy na wszystkich platformach systemu Windows 10. Istnieje jeden wspólne źródło, jednej wspólnej jądra Windows, jeden stos operacji We/Wy plików i jednego modelu aplikacji. Dla interfejsu użytkownika istnieje tylko jeden struktury interfejsu użytkownika XAML i jednej struktury interfejsu użytkownika HTML. Dlatego możesz skoncentrować się na tworzeniu wspaniałych aplikacji, ponieważ wprowadziliśmy go łatwo aplikacji na różnych urządzeniach z systemem Windows 10.  
  
 **Co to dokładnie jest platformy uniwersalnej Windows?**  
  
 Jest po prostu zbiorem kontrakty i wersji. Te pozwalają na docelowy, gdzie można uruchomić aplikacji. System operacyjny nie jest już docelowych. Teraz możesz wskazać swoją aplikację do co najmniej jeden urządzenia z rodzin. Dowiedz się więcej szczegółów tego [Przewodnik po platformie](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Wymagania  
 Narzędzia Universal Windows App Development są dostarczane z emulatorów, które można użyć, aby zobaczyć, jak wygląda aplikacja na różnych urządzeniach. Aby użyć tych emulatorów, musisz zainstalować to oprogramowanie na komputerze fizycznym. Komputer fizyczny, należy uruchomić Windows 8.1 (x64) Professional edition lub nowszy, i mieć procesor obsługujący funkcję Hyper-V klienta i translację adresów drugiego poziomu (SLAT). Nie można użyć emulatorów, gdy program Visual Studio jest zainstalowany na maszynie wirtualnej.  
  
 Poniżej przedstawiono listę oprogramowania, które są potrzebne:  
  
- [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Upewnij się, że wybrano Universal Windows narzędzia do programowania aplikacji z listy opcjonalnych funkcji. Bez tych narzędzi nie będzie mieć możliwość tworzenia aplikacji uniwersalnych.  
  
  Po zainstalowaniu oprogramowania należy [włączyć urządzenia z systemem Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) do tworzenia aplikacji. (Nie potrzebujesz już licencję dewelopera dla każdego urządzenia z systemem Windows 10.)  
  
  **Windows 8.1 i Windows 7**  
  
  Jeśli chcesz tworzyć aplikacje Windows Universal przy użyciu programu Visual Studio 2015 na platformy inne niż Windows 10 są ograniczenia:  
  
- Windows 8.1: Nie można uruchomić aplikację lokalnie (tylko na urządzeniu zdalnym systemem Windows 10). Aby użyć emulatorów w programie Visual Studio, ale nie z symulatora.  
  
- Windows 7: Nie można uruchomić aplikację lokalnie (tylko na urządzeniu zdalnym systemem Windows 10). Nie możesz użyć emulatorów lub symulator w programie Visual Studio albo.  
  
  Projektant XAML można używać tylko w przypadku platformy programowania systemu Windows 10.  
  
## <a name="universal-windows-apps"></a>Universal Windows apps  
 Wybierz swój język preferowany Programowanie w językach C#, Visual Basic, C++ lub JavaScript, aby [tworzenie aplikacji Windows Universal dla urządzeń z systemem Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). Lub Obejrzyj [ten film stanowi wprowadzenie](http://channel9.msdn.com/Series/ConnectOn-Demand/229).  
  
 Jeśli masz istniejące aplikacje Windows Store 8.1, aplikacje systemu Windows Phone 8.1 lub Windows Universal apps utworzonych za pomocą programu Visual Studio 2015 RC [portu tych istniejących aplikacji](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) używać najnowszej wersji uniwersalnej platformy Windows.  
  
 Po utworzeniu aplikacji Universal Windows, należy najpierw [Zapakuj aplikację](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) go zainstalować na urządzeniu z systemem Windows 10 lub przesłać go do Windows Store.
