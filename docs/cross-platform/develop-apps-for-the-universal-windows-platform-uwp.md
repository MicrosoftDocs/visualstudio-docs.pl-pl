---
title: Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
description: Dowiedz się więcej o tworzeniu aplikacji przy Visual Studio i platforma uniwersalna systemu Windows programistyki.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: e54fdd71d848d1edad93fe38598d71c9dbbede7f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308119"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)

Za pomocą platforma uniwersalna systemu Windows i jednego rdzenia systemu Windows możesz uruchomić tę samą aplikację na dowolnym urządzeniu Windows 10, od telefonów do komputerów stacjonarnych. Utwórz te aplikacje uniwersalne systemu Windows za Visual Studio i narzędzia do tworzenia aplikacji uniwersalnych systemu Windows.

![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

Uruchom aplikację na telefonie Windows 10, komputerze Windows 10 lub konsoli Xbox. Jest to ten sam pakiet aplikacji. Wraz z wprowadzeniem jednego Windows 10, ujednoliconego rdzenia, jeden pakiet aplikacji może działać na wszystkich platformach. Kilka platform ma zestawy SDK rozszerzeń, które można dodać do aplikacji, aby korzystać z zachowań specyficznych dla platformy. Na przykład zestaw SDK rozszerzenia dla urządzeń przenośnych obsługuje przycisk Wstecz naciśnięty na telefonie z systemem Windows. Jeśli odwołujesz się do zestawu SDK rozszerzenia w projekcie, wystarczy dodać testy środowiska uruchomieniowego, aby sprawdzić, czy ten zestaw SDK jest dostępny na tej platformie. W ten sposób możesz mieć ten sam pakiet aplikacji dla każdej platformy.

**Co to jest rdzeń systemu Windows?**

Po raz pierwszy system Windows został refaktoryzowany, aby mieć wspólny rdzeń na wszystkich Windows 10 platformach. Istnieje jedno wspólne źródło, jedno wspólne jądro systemu Windows, jeden stos we/wy pliku i jeden model aplikacji. Interfejs użytkownika zawiera tylko jedną platformę interfejsu użytkownika XAML i jedną platformę interfejsu użytkownika HTML. Możesz skoncentrować się na tworzeniu wspaniałej aplikacji, ponieważ ułatwiamy uruchamianie aplikacji na różnych Windows 10 urządzeniach.

**Jaka jest dokładnie platforma uniwersalna systemu Windows?**

Ten platforma uniwersalna systemu Windows jest po prostu kolekcją kontraktów i wersji. Umożliwiają one ukierunkowanie działania aplikacji na miejsce docelowe. System operacyjny nie jest już docelowy. Teraz docelowa jest co najmniej jedna rodzina urządzeń. Dowiedz się więcej, [czytając wprowadzenie do platforma uniwersalna systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Wymagania

Narzędzia do tworzenia aplikacji uniwersalnych systemu Windows są dostarczane z emulatorami, których można użyć, aby zobaczyć, jak aplikacja wygląda na różnych urządzeniach. Jeśli chcesz używać tych emulatorów, musisz zainstalować to oprogramowanie na maszynie fizycznej. Na maszynie fizycznej musi Windows 8.1 (x64) Professional lub wyższa wersja oraz procesor obsługujący funkcję Hyper-V klienta i translę adresów drugiego poziomu (SLAT). Emulatorów nie można używać, gdy Visual Studio na maszynie wirtualnej.

Oto lista potrzebnych programów:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 obsługuje tworzenie aplikacji platformy UWP tylko na Windows 10. Aby uzyskać więcej informacji, zobacz Visual Studio [platform docelowych](/visualstudio/productinfo/vs2017-compatibility-vs) i [Wymagania systemowe](/visualstudio/productinfo/vs2017-system-requirements-vs).

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Będziesz również potrzebować opcjonalnego platforma uniwersalna systemu Windows tworzenia aplikacji.

     ![Obciążenie platformy uniwersalnej systemu Windows](media/uwp_workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 obsługuje tworzenie aplikacji platformy UWP tylko na Windows 10. Aby uzyskać więcej informacji, zobacz Visual Studio [platform docelowych](/visualstudio/releases/2019/compatibility/) i [Wymagania systemowe](/visualstudio/releases/2019/system-requirements/).

- [Visual Studio](https://visualstudio.microsoft.com/downloads). Będziesz również potrzebować opcjonalnego platforma uniwersalna systemu Windows tworzenia aplikacji.

     ![Obciążenie platformy uniwersalnej systemu Windows](media/uwp_workload.png)

::: moniker-end

Po zainstalowaniu tego oprogramowania należy włączyć urządzenie Windows 10 na potrzeby tworzenia oprogramowania. Zobacz [Enable your device for development (Włączanie urządzenia do celów deweloperowych).](/windows/uwp/get-started/enable-your-device-for-development) Nie potrzebujesz już licencji dewelopera dla każdego Windows 10 urządzenia.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Wybierz preferowany język programowania w języku C#, Visual Basic, C++ lub JavaScript, aby utworzyć platforma uniwersalna systemu Windows dla Windows 10 urządzeń. Przeczytaj [klip wideo Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app) lub obejrzyj film z [omówieniem Windows 10 Tools for Windows 10.](https://channel9.msdn.com/Series/ConnectOn-Demand/229)

Jeśli masz istniejące aplikacje ze Sklepu Windows 8.1, aplikacje ze Sklepu Windows Phone 8.1 lub aplikacje uniwersalne systemu Windows utworzone za pomocą programu Visual Studio 2015, musisz je portować, aby korzystać z najnowszych platforma uniwersalna systemu Windows. Zobacz Move from środowisko wykonawcze systemu Windows 8.x to UWP (Przenoszenie z [wersji 8.x do platformy UWP).](/windows/uwp/porting/w8x-to-uwp-root)

Po utworzeniu aplikacji uniwersalnej systemu Windows należy spakować aplikację, aby zainstalować ją na urządzeniu Windows 10 lub przesłać do Sklepu Windows. Zobacz [Packaging apps (Pakowanie aplikacji).](/windows/uwp/packaging/index)

## <a name="see-also"></a>Zobacz też

- [Międzyplatformowe tworzenie aplikacji mobilnych w Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
