---
title: Okno dialogowe Opcje
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c864a10af9ad15d47e2342bb148af464b8f2a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591505"
---
# <a name="options-dialog-box-visual-studio"></a>Okno dialogowe Opcje (Visual Studio)

Okno dialogowe **Opcje** umożliwia skonfigurowanie zintegrowanego środowiska programistycznego (IDE) do potrzeb. Na przykład można ustanowić domyślną lokalizację zapisywania dla projektów, zmienić domyślny wygląd i zachowanie okien oraz utworzyć skróty dla często używanych poleceń. Istnieją również opcje specyficzne dla języka programowania i platformy. Dostęp do **opcji** można uzyskać z menu **Narzędzia.**

## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje

Okno dialogowe **Opcje** jest podzielone na dwie części: okienko nawigacji po lewej stronie i obszar wyświetlania po prawej stronie. Formant drzewa w okienku nawigacji zawiera węzły folderów, takie jak Środowisko, Edytor tekstu, Projekty i rozwiązania oraz Kontrola źródła. Rozwiń dowolny węzeł folderu, aby wyświetlić listę stron opcji, które zawiera. Po wybraniu węzła dla danej strony jego opcje są wyświetlane w obszarze wyświetlania.

Opcje funkcji IDE nie są wyświetlane w okienku nawigacji, dopóki funkcja nie zostanie załadowana do pamięci. W związku z tym te same opcje mogą nie być wyświetlane po rozpoczęciu nowej sesji, które były wyświetlane po zakończeniu ostatniego. Podczas tworzenia projektu lub uruchamiania polecenia, które używa określonej aplikacji, węzły dla odpowiednich opcji są dodawane do okna dialogowego Opcje. Te dodane opcje pozostaną dostępne tak długo, jak długo funkcja IDE pozostaje w pamięci.

> [!NOTE]
> Niektóre kolekcje ustawień mają zakres liczby stron wyświetlanych w okienku nawigacji okna dialogowego Opcje. Możesz wyświetlić wszystkie możliwe strony, wybierając pozycję **Pokaż wszystkie ustawienia**.

## <a name="how-options-are-applied"></a>Jak stosowane są opcje

Kliknięcie przycisku OK w oknie dialogowym **Opcje** zapisuje wszystkie ustawienia na wszystkich stronach. Kliknięcie przycisku Anuluj na dowolnej stronie anuluje wszystkie żądania zmiany, w tym wszystkie tylko wprowadzone na innych stronach **opcji.** Niektóre zmiany w ustawieniach opcji, takie jak wprowadzone w oknie [dialogowym Czcionki i Kolory, Środowisko, Opcje,](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md)zostaną wprowadzone dopiero po zamknięciu i ponownym otwarciu programu Visual Studio.

### <a name="show-all-settings"></a>Pokaż wszystkie ustawienia

Zaznaczenie lub odznaczenie **Pokaż wszystkie ustawienia** stosuje wszystkie zmiany wprowadzone w oknie dialogowym **Opcje,** nawet jeśli nie kliknięto jeszcze **przycisku OK**.

## <a name="see-also"></a>Zobacz też

- [Dopasowywanie edytora](../how-to-change-text-case-in-the-editor.md)
