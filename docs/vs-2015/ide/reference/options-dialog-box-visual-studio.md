---
title: Okno dialogowe Opcje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ed637943d7a849357338593ffc684e4f45c09a30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662443"
---
# <a name="options-dialog-box-visual-studio"></a>Opcje — Okno dialogowe [Visual Studio]
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno dialogowe **Opcje** umożliwia skonfigurowanie zintegrowanego środowiska programistycznego (IDE) do Twoich potrzeb. Na przykład można określić domyślną lokalizację zapisu dla projektów, zmienić domyślny wygląd i zachowanie systemu Windows oraz utworzyć skróty do często używanych poleceń. Dostępne są również opcje specyficzne dla języka i platformy deweloperskiej. Dostęp do **opcji** można uzyskać za pomocą menu **Narzędzia** .

> [!NOTE]
> Opcje dostępne w oknach dialogowych oraz nazwy i lokalizacje poleceń menu, które są widoczne, mogą się różnić od tego, co opisano w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje
 Okno dialogowe **Opcje** jest podzielone na dwie części: okienko nawigacji po lewej stronie i obszar wyświetlania po prawej stronie. Kontrolka drzewa w okienku nawigacji obejmuje węzły folderów, takie jak środowisko, Edytor tekstu, projekty i rozwiązania oraz kontrola źródła. Rozwiń węzeł dowolnego folderu, aby wyświetlić listę wszystkich opcji, które zawiera. Po wybraniu węzła dla określonej strony jego opcje są wyświetlane w obszarze wyświetlania.

 Opcje funkcji IDE nie są wyświetlane w okienku nawigacji, dopóki funkcja nie zostanie załadowana do pamięci. W związku z tym te same opcje mogą nie być wyświetlane po rozpoczęciu nowej sesji, która była wyświetlana w trakcie ostatniego zakończenia. Podczas tworzenia projektu lub uruchamiania polecenia korzystającego z określonej aplikacji węzły odpowiednich opcji są dodawane do okna dialogowego Opcje. Te dodane opcje będą nadal dostępne, o ile funkcja IDE pozostanie w pamięci.

> [!NOTE]
> Niektóre kolekcje ustawień mają zakres liczby stron, które pojawiają się w okienku nawigacji okna dialogowego Opcje. Możesz wyświetlić wszystkie możliwe strony, wybierając opcję **Pokaż wszystkie ustawienia**.

## <a name="how-options-are-applied"></a>Jak są stosowane opcje
 Kliknięcie przycisku OK w oknie dialogowym **Opcje** umożliwia zapisanie wszystkich ustawień na wszystkich stronach. Kliknięcie przycisku Anuluj na dowolnej stronie anuluje wszystkie żądania zmiany, w tym wszystkie utworzone na innych stronach **opcji** . Niektóre zmiany ustawień opcji, na przykład dotyczące [czcionek i kolorów, środowiska, okna dialogowego Opcje](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), zostaną zastosowane po zamknięciu i ponownym otwarciu programu Visual Studio.

### <a name="show-all-settings"></a>Pokaż wszystkie ustawienia
 Wybranie lub zaznaczenie pola wyboru **Pokaż wszystkie ustawienia** powoduje zastosowanie wszystkich zmian wprowadzonych w oknie dialogowym **Opcje** , mimo że jeszcze nie kliknięto **OK**.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie edytora](../../ide/customizing-the-editor.md)
