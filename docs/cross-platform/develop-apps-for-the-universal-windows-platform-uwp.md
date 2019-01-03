---
title: Twórz aplikacje dla platformy Universal Windows (UWP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2017
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: stevehoag
ms.author: shoag
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a7f0279249be7b5a48b342f1de26179af7b89f80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843794"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
Dzięki platformie Universal Windows i naszych jednego rdzenia Windows można uruchamiać tę samą aplikację na dowolnym urządzeniu systemu Windows 10, od telefonów do komputerów stacjonarnych. Tworzenie aplikacji Universal Windows za pomocą programu Visual Studio i narzędzia do programowania uniwersalnych aplikacji Windows.

 ![Platforma Universal Windows](../cross-platform/media/uwp_coreextensions.png "UWP_CoreExtensions")

 Uruchom aplikację na telefonie z systemem Windows 10, system Windows 10 desktop lub konsoli Xbox. To ten sam pakiet aplikacji! Wraz z wprowadzeniem core systemu Windows 10 w pojedynczą, jednolitą jednego pakietu aplikacji można uruchamiać na wszystkich platformach. Różnych platform, mają rozszerzenie SDK, które można dodać do aplikacji, aby skorzystać z zachowań określonych platform. Na przykład zestawu SDK rozszerzenia dla urządzeń przenośnych obsługuje przycisku Wstecz naciśniętym na urządzeniu z systemem Windows phone. Jeśli odwołujesz rozszerzenie SDK w projekcie, wystarczy dodać testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. To, jak może mieć ten sam pakiet aplikacji dla każdej platformy.

 **Co to jest podstawowa Windows?**

 Po raz pierwszy Windows ma zostały zaprojektowane od nowa w zapewnienie wspólnej podstawy na wszystkich platformach systemu Windows 10. Istnieje jeden wspólne źródło, jednej wspólnej jądra Windows, jeden stos operacji We/Wy plików i jednego modelu aplikacji. Dla interfejsu użytkownika istnieje tylko jeden struktury interfejsu użytkownika XAML i jednej struktury interfejsu użytkownika HTML. Możesz skoncentrować się na tworzeniu wspaniałych aplikacji, ponieważ wprowadziliśmy go łatwo aplikacji na różnych urządzeniach z systemem Windows 10.

 **Co to dokładnie jest platformy uniwersalnej Windows?**

Platformy uniwersalnej Windows jest po prostu kolekcją umów i wersji. Te pozwalają na docelowy, gdzie można uruchomić aplikacji. Nie jest już docelowy system operacyjny; Teraz możesz wskazać przynajmniej jednego urządzenia z rodzin. Dowiedz się więcej szczegółów, czytając [wprowadzenie do platformy uniwersalnej Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Wymagania
 Narzędzia do programowania uniwersalnych aplikacji Windows są dostarczane z emulatorów, które można użyć, aby zobaczyć, jak wygląda aplikacja na różnych urządzeniach. Aby użyć tych emulatorów, musisz zainstalować to oprogramowanie na komputerze fizycznym. Komputer fizyczny, należy uruchomić Windows 8.1 (x64) Professional edition lub nowszy, i mieć procesor obsługujący funkcję Hyper-V klienta i translację adresów drugiego poziomu (SLAT). Nie można użyć emulatorów, gdy program Visual Studio jest zainstalowany na maszynie wirtualnej.

 Poniżej przedstawiono listę oprogramowania, które są potrzebne:

-   [System Windows 10](http://windows.microsoft.com/windows/downloads). Program Visual Studio 2017 obsługuje tworzenie platformy uniwersalnej systemu Windows tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz Visual Studio [platformy](/visualstudio/productinfo/vs2017-compatibility-vs) i [wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs).

-   [Program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Należy również opcjonalny obciążenia programowania Universal Windows Platform.

     ![Obciążenie platformy uniwersalnej systemu Windows](media/uwp_workload.png)

Po zainstalowaniu tego oprogramowania, należy włączyć urządzenia z systemem Windows 10 do tworzenia aplikacji. Zobacz [włączyć urządzenia na potrzeby programowania](/windows/uwp/get-started/enable-your-device-for-development). Nie potrzebujesz już licencję dewelopera dla każdego urządzenia z systemem Windows 10.

## <a name="universal-windows-apps"></a>Universal Windows apps
Wybierz język preferowany programowania w języku C#, Visual Basic, C++ lub JavaScript do tworzenia aplikacji Universal Windows Platform dla urządzeń z systemem Windows 10. Odczyt [Utwórz swoją pierwszą aplikację](/windows/uwp/get-started/your-first-app) lub Obejrzyj [narzędzia dla systemu Windows 10 — omówienie](https://channel9.msdn.com/Series/ConnectOn-Demand/229) wideo.

Jeśli masz istniejące aplikacje Windows Store 8.1, aplikacje systemu Windows Phone 8.1 lub Windows Universal aplikacje, które zostały utworzone przy użyciu programu Visual Studio 2015, konieczne będzie portu tych aplikacji mają być użyj najnowszej wersji uniwersalnej platformy Windows. Zobacz [przenoszenie ze środowiska wykonawczego Windows 8.x do platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root).

Po utworzeniu aplikacji Universal Windows, należy spakować aplikację, aby go zainstalować na urządzeniu z systemem Windows 10 lub przesłać go do Windows Store. Zobacz [pakowanie aplikacji](/windows/uwp/packaging/index).

## <a name="see-also"></a>Zobacz także
[Tworzenie aplikacji mobilnych dla wielu platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
