---
title: Tworzenie wycinków metody testów jednostkowych
ms.date: 04/24/2020
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2712210d4761edb90414e2a27beba74a3bacbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288666"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Utwórz klasy zastępcze metody testów jednostkowych za pomocą polecenia Utwórz testy jednostkowe

Polecenie **Utwórz testy jednostkowe** powoduje utworzenie wycinków metody testów jednostkowych. Ta funkcja pozwala na łatwą konfigurację projektu testowego, klasy testowej i częściowej metody testowej.

::: moniker range="vs-2017"
> [!NOTE]
> Polecenie **Utwórz testy jednostkowe** jest dostępne tylko dla kodu w języku C#, który jest przeznaczony dla .NET Framework (ale nie do programu .NET Core).
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Polecenie **Utwórz testy jednostkowe** jest dostępne tylko dla kodu w języku C#.
::: moniker-end

Polecenie menu **Utwórz testy jednostkowe** jest rozszerzalne i może służyć do generowania testów dla MSTest, MSTest v2, nunit i xUnit.

## <a name="get-started"></a>Rozpoczęcie pracy

Aby rozpocząć, wybierz metodę, typ lub przestrzeń nazw w edytorze kodu w projekcie, który chcesz przetestować, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Utwórz testy jednostkowe**. Zostanie otwarte okno dialogowe **Tworzenie testów jednostkowych** , w którym można skonfigurować sposób tworzenia testów.

![Za pomocą polecenia Utwórz testy jednostkowe](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Ustaw cechy testu jednostkowego

Jeśli planujesz uruchomić te testy jako część procesu automatyzacji testu, możesz rozważyć, że test został utworzony w innym projekcie testowym (druga opcja w oknie dialogowym powyżej) i ustawienie cech testów jednostkowych dla testu jednostkowego. Dzięki temu można łatwiej dołączać lub wykluczać te konkretne testy jako część potoku ciągłej integracji lub ciągłego wdrażania. Cechy są ustawiane przez dodanie metadanych do testu jednostkowego bezpośrednio, jak pokazano poniżej.

![Ustawianie cech testu jednostkowego](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Używanie platform testów jednostkowych innych firm

Aby automatycznie wygenerować testy jednostkowe dla NUnit lub xUnit, zainstaluj jedno z następujących rozszerzeń programu Test Framework z Visual Studio Marketplace:

* [Rozszerzenie NUnit dla generatorów testów](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozszerzenie xUnit.net dla generatorów testów](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kiedy należy używać tej funkcji?

Użyj tej funkcji, gdy chcesz utworzyć testy jednostkowe, ale w odróżnieniu od testowania istniejącego kodu, który ma niewielki lub brakujący zakres testów i brak dokumentacji. Innymi słowy, gdzie istnieje ograniczona lub nieistniejąca Specyfikacja kodu. Efektywnie implementuje podejście podobne do [inteligentnych testów jednostkowych](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) , które charakteryzuje obserwowane zachowanie kodu.

Jednak ta funkcja jest równie stosowana, gdy programista rozpocznie pisanie kodu, a następnie używa go do uruchamiania testów jednostkowych. W ramach przepływu kodowania, deweloper może chcieć szybko utworzyć element zastępczy metody testów jednostkowych (z odpowiednią klasą testową i odpowiednim projektem testowym) dla konkretnego fragmentu kodu.

## <a name="see-also"></a>Zobacz też

- [Tworzenie wycinków metody testów jednostkowych przy użyciu "tworzenia testów jednostkowych"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Wpisy w blogu testowania jednostkowego](https://devblogs.microsoft.com/devops/?s=unit+testing)
