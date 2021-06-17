---
title: Okno dialogowe Opcje
description: Dowiedz się więcej na temat okna dialogowego Opcje, jego układu i sposobu, w jaki visual studio stosuje wybrane opcje do projektów i rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79bd2d95a12aa7c42705d106cf71b4061a020431
ms.sourcegitcommit: 113b7df611583307d3965984233a33355d6b0318
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2021
ms.locfileid: "112126544"
---
# <a name="options-dialog-box-visual-studio"></a>Okno dialogowe Opcje (Visual Studio)

Okno **dialogowe** Opcje umożliwia skonfigurowanie zintegrowanego środowiska projektowego (IDE) do swoich potrzeb. Można na przykład ustanowić domyślną lokalizację zapisywania dla projektów, zmienić domyślny wygląd i zachowanie okien oraz utworzyć skróty dla często używanych poleceń. Dostępne są również opcje specyficzne dla języka i platformy programowania. Dostęp do opcji **można uzyskać** **z** menu Narzędzia.

## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje

Okno **dialogowe** Opcje jest podzielone na dwie części: okienko nawigacji po lewej stronie i obszar wyświetlania po prawej stronie. Kontrolka drzewa w okienku nawigacji zawiera węzły folderów, takie jak Środowisko, Edytor tekstu, Projekty i rozwiązania oraz Kontrola źródła. Rozwiń dowolny węzeł folderu, aby wyświetlić listę stron opcji, które zawiera. Po wybraniu węzła dla określonej strony jego opcje są wyświetlane w obszarze wyświetlania.

Opcje funkcji środowiska IDE nie są wyświetlane w okienku nawigacji, dopóki funkcja nie zostanie załadowana do pamięci. W związku z tym te same opcje mogą nie być wyświetlane podczas rozpoczynania nowej sesji, które były wyświetlane jako ostatnia. Podczas tworzenia projektu lub uruchamiania polecenia korzystającego z określonej aplikacji węzły dla odpowiednich opcji są dodawane do okna dialogowego Opcje. Te dodane opcje pozostaną dostępne tak długo, jak długo funkcja IDE pozostanie w pamięci.

> [!NOTE]
> Niektóre kolekcje ustawień mają zakres liczby stron wyświetlanych w okienku nawigacji okna dialogowego Opcje.

## <a name="how-options-are-applied"></a>Jak są stosowane opcje

Kliknięcie przycisku OK w **oknie** dialogowym Opcje powoduje zapisanie wszystkich ustawień na wszystkich stronach. Kliknięcie przycisku Anuluj na dowolnej stronie anuluje wszystkie żądania zmiany, w tym wszystkie wprowadzone na innych **stronach** Opcje. Niektóre zmiany ustawień opcji, takie jak wprowadzone w czcionkach i [kolorach, środowisku,](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)oknie dialogowym Opcje, zostaną wprowadzone dopiero po zamknięciu i ponownym otwarciu Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Dopasowywanie edytora](../how-to-change-text-case-in-the-editor.md)
- [Ustawienia i preferencje usługi Git](../../version-control/git-settings.md)
