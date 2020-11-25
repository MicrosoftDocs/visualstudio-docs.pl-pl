---
title: Okno dialogowe Opcje
description: Dowiedz się więcej na temat okna dialogowego Opcje, jego układu i sposobu, w jaki program Visual Studios stosuje opcje wybrane dla projektów i rozwiązań.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abf435625cc9003dc569542e24e020e3801ec00
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039812"
---
# <a name="options-dialog-box-visual-studio"></a>Opcje — okno dialogowe (Visual Studio)

Okno dialogowe **Opcje** umożliwia skonfigurowanie zintegrowanego środowiska programistycznego (IDE) do Twoich potrzeb. Na przykład można określić domyślną lokalizację zapisu dla projektów, zmienić domyślny wygląd i zachowanie systemu Windows oraz utworzyć skróty do często używanych poleceń. Dostępne są również opcje specyficzne dla języka i platformy deweloperskiej. Dostęp do **opcji** można uzyskać za pomocą menu **Narzędzia** .

## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje

Okno dialogowe **Opcje** jest podzielone na dwie części: okienko nawigacji po lewej stronie i obszar wyświetlania po prawej stronie. Kontrolka drzewa w okienku nawigacji obejmuje węzły folderów, takie jak środowisko, Edytor tekstu, projekty i rozwiązania oraz kontrola źródła. Rozwiń węzeł dowolnego folderu, aby wyświetlić listę wszystkich opcji, które zawiera. Po wybraniu węzła dla określonej strony jego opcje są wyświetlane w obszarze wyświetlania.

Opcje funkcji IDE nie są wyświetlane w okienku nawigacji, dopóki funkcja nie zostanie załadowana do pamięci. W związku z tym te same opcje mogą nie być wyświetlane po rozpoczęciu nowej sesji, która była wyświetlana w trakcie ostatniego zakończenia. Podczas tworzenia projektu lub uruchamiania polecenia korzystającego z określonej aplikacji węzły odpowiednich opcji są dodawane do okna dialogowego Opcje. Te dodane opcje będą nadal dostępne, o ile funkcja IDE pozostanie w pamięci.

> [!NOTE]
> Niektóre kolekcje ustawień mają zakres liczby stron, które pojawiają się w okienku nawigacji okna dialogowego Opcje.

## <a name="how-options-are-applied"></a>Jak są stosowane opcje

Kliknięcie przycisku OK w oknie dialogowym **Opcje** umożliwia zapisanie wszystkich ustawień na wszystkich stronach. Kliknięcie przycisku Anuluj na dowolnej stronie anuluje wszystkie żądania zmiany, w tym wszystkie utworzone na innych stronach **opcji** . Niektóre zmiany ustawień opcji, na przykład dotyczące [czcionek i kolorów, środowiska, okna dialogowego Opcje](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), zostaną zastosowane po zamknięciu i ponownym otwarciu programu Visual Studio.

## <a name="see-also"></a>Zobacz też

- [Dopasowywanie edytora](../how-to-change-text-case-in-the-editor.md)
