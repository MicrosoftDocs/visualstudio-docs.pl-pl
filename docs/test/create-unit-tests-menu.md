---
title: Tworzenie wycinków kodu metoda testu jednostki
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7eb72f104560991f1bb191e62641041879df071
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58857727"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Tworzenie jednostki wycinki kodu metoda testu za pomocą polecenia Utwórz testy jednostkowe

**Utwórz testy jednostkowe** polecenie powoduje utworzenie jednostki wycinki kodu metoda testu. Ta funkcja umożliwia Łatwa konfiguracja projektu testowego, klasy testowej i testu zastępczego metoda znajdujący się w nim.

> [!NOTE]
> **Utwórz testy jednostkowe** polecenia menu jest dostępna tylko dla kodu zarządzanego, który jest przeznaczony dla .NET Framework (ale nie platformy .NET Core).

**Utwórz testy jednostkowe** polecenia menu jest wszechstronne i może służyć do generowania testów, MSTest, MSTest w wersji 2, NUnit i struktury xUnit.

## <a name="get-started"></a>Wprowadzenie

Aby rozpocząć, wybierz metodę, typu lub przestrzeni nazw w edytorze kodu w projekcie, którą chcesz przetestować, kliknij prawym przyciskiem myszy, a następnie wybierz **Utwórz testy jednostkowe**. **Utwórz testy jednostkowe** otwiera okno dialogowe, którego można skonfigurować, jak chcesz, aby testy, które ma zostać utworzony.

![Za pomocą polecenia Utwórz testy jednostki](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Ustaw cech testu jednostki

Jeśli planujesz uruchomić te testy jako część procesu automatyzacji testów, należy rozważyć, posiadające testu, utworzone w innym projekcie testowym (druga opcja w oknie dialogowym powyżej) i testów jednostkowych ustawienie cech dla testu jednostkowego. Dzięki temu można łatwiej lub wykluczane z tych określonych testów w ramach ciągłej integracji i ciągłego wdrażania potoku. Cechy są ustawiane przez dodanie metadanych do testu jednostkowego bezpośrednio, jak pokazano poniżej.

![Ustawienie cech testu jednostki](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Użyj struktury testów jednostkowych innej firmy

Do automatycznego generowania testów jednostkowych dla NUnit czy xUnit, należy zainstalować jedną z tych rozszerzeń struktury testów w Visual Studio Marketplace:

* [Rozszerzenie NUnit dla generatorów testu](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [rozszerzenie xUnit.net dla generatorów testu](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Kiedy należy używać tej funkcji?

Ta funkcja zawsze, gdy trzeba utworzyć testy jednostkowe, ale szczególnie w przypadku, gdy testujesz istniejący kod, który ma niewielkiego lub żadnego pokrycie testu i nie dokumentacji. Innymi słowy gdy specyfikacja ograniczony lub nieistniejącego kodu. Skutecznie implementuje podejście podobne do [inteligentne testy jednostkowe](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) który charakteryzuje obserwacji zachowania kodu.

Jednak ta funkcja jest również mają zastosowanie, gdy deweloper rozpoczyna się przez pisanie kodu, a następnie używa, uruchomienie testów jednostkowych. W ramach przepływu kodowania deweloper może być szybko tworzyć jednostki metoda zastępcza klasa testowa (z klasą testową odpowiedni i Projekt testowy odpowiednie) dla określonego fragmentu kodu.

## <a name="see-also"></a>Zobacz także

- [Tworzenie wycinków metody testów jednostkowych za pomocą "Utwórz testy jednostkowe"](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Wpisy w blogu testy jednostkowe](https://devblogs.microsoft.com/devops/?s=unit+testing)
