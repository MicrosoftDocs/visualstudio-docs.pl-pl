---
title: Właściwości Przyciski okna | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706172"
---
# <a name="properties-window-buttons"></a>Przyciski okna właściwości
W zależności od języka programowania i typu produktu niektóre przyciski są domyślnie wyświetlane na pasku narzędzi okna **Właściwości.** We wszystkich przypadkach wyświetlane są przyciski **Kategoryzowane,** **Alfabezowane,** **Właściwości**i **Strony właściwości.** W języku Visual C# i Visual Basic wyświetlany jest również przycisk **Zdarzenia.** W niektórych projektach języka Visual C++ są wyświetlane **komunikaty VC++** i **vc overrides.** Dodatkowe przyciski mogą być wyświetlane dla innych typów projektów. Aby uzyskać więcej informacji na temat przycisków w oknie **Właściwości,** zobacz [Okno Właściwości](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementacja przycisków okna właściwości
 Po kliknięciu przycisku **Kategoryzowane** program <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Visual Studio wywołuje interfejs obiektu, który ma fokus do sortowania jego właściwości według kategorii. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>jest implementowany `IDispatch` na obiekcie, który jest prezentowany w oknie **Właściwości.**

 Istnieje 11 wstępnie zdefiniowanych kategorii właściwości, które mają wartości ujemne. Można zdefiniować kategorie niestandardowe, ale zaleca się przypisywanie im wartości dodatnich w celu odróżnienia ich od wstępnie zdefiniowanych kategorii.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> zwraca odpowiednią wartość kategorii właściwości dla określonej właściwości. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> zwraca ciąg, który zawiera nazwę kategorii. Wystarczy zapewnić obsługę niestandardowych wartości kategorii, ponieważ visual studio zna standardowe wartości kategorii właściwości.

 Po kliknięciu przycisku **Alfabetycznie** właściwości są wyświetlane w kolejności alfabetycznej według nazwy. Nazwy są pobierane `IDispatch` według zlokalizowanego algorytmu sortowania.

 Po otwarciu okna **Właściwości** przycisk **Właściwości** jest automatycznie wyświetlany w wybrany sposób. W innych częściach środowiska wyświetlany jest ten sam przycisk i można go kliknąć, aby wyświetlić okno **Właściwości.**

 Przycisk **Strony właściwości** jest `ISpecifyPropertyPages` niedostępny, jeśli nie jest zaimplementowany dla wybranego obiektu. Strony właściwości wyświetlają właściwości zależne od konfiguracji, które są zazwyczaj skojarzone z rozwiązaniami i projektami, ale mogą być również skojarzone z elementami projektu (na przykład w języku Visual C++).

> [!NOTE]
> Nie można dodać przycisków paska narzędzi do okna **Właściwości** przy użyciu kodu niezarządzanego. Aby dodać przycisk paska narzędzi, należy utworzyć obiekt <xref:System.Windows.Forms.Design.PropertyTab>zarządzany, który pochodzi od programu .

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
