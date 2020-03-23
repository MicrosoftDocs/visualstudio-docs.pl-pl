---
title: Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 2ef09f58d22e3cb72af5b745f16b2acf8920900e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75587150"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Opracowywanie aplikacji na platformę uniwersalną systemu Windows (UWP)

Dzięki uniwersalnej platformie Windows i naszemu rdzeniu systemu Windows możesz uruchomić tę samą aplikację na dowolnym urządzeniu z systemem Windows 10, od telefonów po komputery stacjonarne. Utwórz te uniwersalne aplikacje systemu Windows za pomocą programu Visual Studio i narzędzi do tworzenia uniwersalnych aplikacji systemu Windows.

![Platforma uniwersalna systemu Windows](../cross-platform/media/uwp_coreextensions.png)

Uruchom aplikację na telefonie z systemem Windows 10, komputerze z systemem Windows 10 lub konsoli Xbox. To ten sam pakiet aplikacji! Wraz z wprowadzeniem systemu Windows 10 pojedynczy, ujednolicony rdzeń, jeden pakiet aplikacji może działać na wszystkich platformach. Kilka platform ma rozszerzenia SDK, które można dodać do aplikacji, aby skorzystać z zachowań specyficznych dla platformy. Na przykład sdk rozszerzeń dla urządzeń przenośnych obsługuje przycisk wstecz naciśnięty na telefonie z systemem Windows. Jeśli odwołujesz się do sdk rozszerzenia w projekcie, a następnie po prostu dodać sprawdzanie środowiska uruchomieniowego, aby przetestować, czy ten SDK jest dostępny na tej platformie. W ten sposób możesz mieć ten sam pakiet aplikacji dla każdej platformy!

**Co to jest rdzeń systemu Windows?**

Po raz pierwszy system Windows został refaktoryzowany, aby mieć wspólny rdzeń na wszystkich platformach Windows 10. Istnieje jedno wspólne źródło, jedno wspólne jądro systemu Windows, jeden stos we/wy pliku i jeden model aplikacji. Dla interfejsu użytkownika istnieje tylko jedna struktura interfejsu użytkownika XAML i jedna struktura interfejsu użytkownika HTML. Możesz skupić się na tworzeniu świetnej aplikacji, ponieważ ułatwiliśmy uruchamianie aplikacji na różnych urządzeniach z systemem Windows 10.

**Czym dokładnie jest uniwersalna platforma Windows?**

Uniwersalna platforma systemu Windows jest po prostu zbiorem kontraktów i wersji. Umożliwiają one kierowanie miejsca, w którym aplikacja może działać. Nie jest już ukierunkowany na system operacyjny; teraz kierujesz reklamy na jedną lub więcej rodzin urządzeń. Dowiedz się więcej o szczegółach, czytając wprowadzenie [do platformy uniwersalnej systemu Windows](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Wymagania

Narzędzia do tworzenia aplikacji uniwersalnych systemu Windows są wyposażone w emulatory, których można użyć, aby zobaczyć, jak aplikacja wygląda na różnych urządzeniach. Jeśli chcesz użyć tych emulatorów, musisz zainstalować to oprogramowanie na komputerze fizycznym. Komputer fizyczny musi działać w wersji Professional systemu Windows 8.1 (x64) lub nowszej oraz mieć procesor obsługujący funkcję tłumaczenia adresów hyper-V i drugiego poziomu (SLAT). Nie można używać emulatorów, gdy program Visual Studio jest zainstalowany na maszynie wirtualnej.

Oto lista potrzebnych programów:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Program Visual Studio 2017 obsługuje tworzenie platformy uniwersalnej systemu Windows tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [Kierowanie na platformę](/visualstudio/productinfo/vs2017-compatibility-vs) programu Visual Studio i [wymagania systemowe.](/visualstudio/productinfo/vs2017-system-requirements-vs)

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Konieczne będzie również opcjonalne obciążenie deweloperne platformy uniwersalnej systemu Windows.

     ![Obciążenie platformy uniwersalnej systemupos](media/uwp_workload.png)

::: moniker-end

::: moniker range="vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Program Visual Studio 2019 obsługuje tworzenie platformy uniwersalnej systemu Windows tylko w systemie Windows 10. Aby uzyskać więcej informacji, zobacz [Kierowanie na platformę](/visualstudio/releases/2019/compatibility/) programu Visual Studio i [wymagania systemowe.](/visualstudio/releases/2019/system-requirements/)

- [Visual Studio](https://visualstudio.microsoft.com/downloads). Konieczne będzie również opcjonalne obciążenie deweloperne platformy uniwersalnej systemu Windows.

     ![Obciążenie platformy uniwersalnej systemupos](media/uwp_workload.png)

::: moniker-end

Po zainstalowaniu tego oprogramowania należy włączyć urządzenie z systemem Windows 10 do tworzenia. Zobacz [Włączanie urządzenia do tworzenia](/windows/uwp/get-started/enable-your-device-for-development). Nie potrzebujesz już licencji dewelopera dla każdego urządzenia z systemem Windows 10.

## <a name="universal-windows-apps"></a>Aplikacje uniwersalne systemu Windows

Wybierz preferowany język programowania z języka C#, Visual Basic, C++ lub JavaScript, aby utworzyć aplikację uniwersalną platformy systemu Windows dla urządzeń z systemem Windows 10. Przeczytaj artykuł [Tworzenie pierwszej aplikacji](/windows/uwp/get-started/your-first-app) lub obejrzyj klip wideo [Omówienie narzędzi dla systemu Windows 10.](https://channel9.msdn.com/Series/ConnectOn-Demand/229)

Jeśli masz istniejące aplikacje ze Sklepu Windows 8.1, aplikacje dla systemu Windows Phone 8.1 lub aplikacje systemu Uniwersalnego systemu Windows utworzone za pomocą programu Visual Studio 2015, musisz przenieść te aplikacje, aby korzystać z najnowszej platformy uniwersalnej systemu Windows. Zobacz [Przechodzenie z środowiska wykonawczego systemu Windows 8.x do platformy uniwersalnej systemu Windows](/windows/uwp/porting/w8x-to-uwp-root).

Po utworzeniu aplikacji uniwersalnego systemu Windows należy spakować aplikację, aby zainstalować ją na urządzeniu z systemem Windows 10 lub przesłać do Sklepu Windows. Zobacz [Aplikacje do pakowania](/windows/uwp/packaging/index).

## <a name="see-also"></a>Zobacz też

- [Tworzenie urządzeń mobilnych na różnych platformach w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
