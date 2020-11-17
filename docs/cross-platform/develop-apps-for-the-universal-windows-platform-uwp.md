---
title: Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
description: Dowiedz się więcej na temat tworzenia aplikacji przy użyciu programu Visual Studio i narzędzi do tworzenia aplikacji uniwersalnych systemu Windows.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: e9cff517c60a67ee9bbf929c59a1150d5ace3757
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671422"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)

Korzystając z platforma uniwersalna systemu Windows i naszego systemu Windows Core, możesz uruchomić tę samą aplikację na dowolnym urządzeniu z systemem Windows 10 z telefonów na komputerach stacjonarnych. Twórz te aplikacje uniwersalne systemu Windows za pomocą programu Visual Studio i narzędzi do tworzenia aplikacji uniwersalnych systemu Windows.

![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

Uruchom aplikację na telefonie z systemem Windows 10, Windows 10 Desktop lub Xbox. Jest to ten sam pakiet aplikacji. Wraz z wprowadzeniem pojedynczego, ujednoliconego rdzeń systemu Windows 10 jeden pakiet aplikacji może być uruchamiany na wszystkich platformach. Kilka platform zawiera zestawy SDK rozszerzeń, które można dodać do aplikacji, aby korzystać z zachowań specyficznych dla platformy. Na przykład zestaw SDK rozszerzenia dla urządzeń przenośnych obsługuje naciśnięcie przycisku Wstecz w systemie Windows Phone. Jeśli odwołujesz się do zestawu SDK rozszerzenia w projekcie, po prostu Dodaj testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. Oznacza to, że możesz mieć ten sam pakiet aplikacji dla każdej platformy.

**Co to jest rdzeń systemu Windows?**

Po raz pierwszy system Windows został wdrożony jako wspólny rdzeń na wszystkich platformach Windows 10. Istnieje jedno wspólne źródło, jedno wspólne jądro systemu Windows, jeden stos plików we/wy i jeden model aplikacji. Dla interfejsu użytkownika istnieje tylko jedna struktura interfejsu użytkownika języka XAML i jedna struktura interfejsu użytkownika języka HTML. Możesz skoncentrować się na tworzeniu doskonałej aplikacji, ponieważ ułatwia ona uruchamianie aplikacji na różnych urządzeniach z systemem Windows 10.

**Co to jest dokładnie platforma uniwersalna systemu Windows?**

Platforma uniwersalna systemu Windows jest po prostu kolekcją kontraktów i wersji. Umożliwiają one docelową lokalizację, w której można uruchomić aplikację. Nie jest już ukierunkowany system operacyjny; Teraz należy określić co najmniej jedną rodzinę urządzeń. Więcej informacji można uzyskać, odczytując [wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Wymagania

Narzędzia programistyczne dla aplikacji uniwersalnych systemu Windows są dostarczane z emulatorami, za pomocą których można zobaczyć, jak aplikacja wygląda na różnych urządzeniach. Jeśli chcesz używać tych emulatorów, musisz zainstalować to oprogramowanie na komputerze fizycznym. Na maszynie fizycznej musi działać system Windows 8.1 (x64) Professional Edition lub nowszy oraz procesor obsługujący funkcję Hyper-V klienta i translację adresów drugiego poziomu (SLAT). Emulatorów nie można używać, gdy program Visual Studio jest zainstalowany na maszynie wirtualnej.

Poniżej znajduje się lista programów, które są potrzebne:

::: moniker range="vs-2017"

- [System Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Program Visual Studio 2017 obsługuje programowanie platformy UWP tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [wymagania systemowe dotyczące](/visualstudio/productinfo/vs2017-system-requirements-vs) [platformy](/visualstudio/productinfo/vs2017-compatibility-vs) programu Visual Studio i system.

- [Program Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Wymagane jest również opcjonalne platforma uniwersalna systemu Windows obciążenie pracą programistyczną.

     ![Obciążenie platformy UWP](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [System Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Program Visual Studio 2019 obsługuje programowanie platformy UWP tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [wymagania systemowe dotyczące](/visualstudio/releases/2019/system-requirements/) [platformy](/visualstudio/releases/2019/compatibility/) programu Visual Studio i system.

- [Program Visual Studio](https://visualstudio.microsoft.com/downloads). Wymagane jest również opcjonalne platforma uniwersalna systemu Windows obciążenie pracą programistyczną.

     ![Obciążenie platformy UWP](media/uwp_workload.png)

::: moniker-end

Po zainstalowaniu tego oprogramowania musisz włączyć urządzenie z systemem Windows 10 na potrzeby programowania. Zobacz [Włączanie urządzenia na potrzeby programowania](/windows/uwp/get-started/enable-your-device-for-development). Na każdym urządzeniu z systemem Windows 10 nie jest już wymagana licencja dewelopera.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Wybierz preferowany język programowania w języku C#, Visual Basic, C++ lub JavaScript, aby utworzyć aplikację platforma uniwersalna systemu Windows dla urządzeń z systemem Windows 10. Przeczytaj artykuł [Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app) lub Obejrzyj film wideo z [omówieniem narzędzi dla systemu Windows 10](https://channel9.msdn.com/Series/ConnectOn-Demand/229) .

Jeśli masz istniejące aplikacje ze sklepu Windows 8,1, aplikacje Windows Phone 8,1 lub aplikacje uniwersalne systemu Windows, które zostały utworzone za pomocą programu Visual Studio 2015, musisz przenieść te aplikacje, aby używały najnowszych platforma uniwersalna systemu Windows. Zobacz [przechodzenie z środowisko wykonawcze systemu Windows 8. x do platformy UWP](/windows/uwp/porting/w8x-to-uwp-root).

Po utworzeniu aplikacji uniwersalnej systemu Windows należy spakować aplikację, aby ją zainstalować na urządzeniu z systemem Windows 10 lub przesłać do sklepu Windows. Zobacz [pakowanie aplikacji](/windows/uwp/packaging/index).

## <a name="see-also"></a>Zobacz także

- [Programowanie aplikacji mobilnych na wiele platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
