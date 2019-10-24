---
title: Przyciski okna właściwości | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2a41917a58a6fc5780b62c2c9e3db8aa52d407
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725268"
---
# <a name="properties-window-buttons"></a>Przyciski okna właściwości
W zależności od języka programowania i typu produktu niektóre przyciski są domyślnie wyświetlane na pasku narzędzi okna **Właściwości** . We wszystkich przypadkach są wyświetlane **przyciski z**przydzielonymi, **alfabetycznymi**, **właściwościami**i **stronami właściwości** . W wizualizacjach C# i Visual Basic jest również wyświetlany przycisk **zdarzenia** . W niektórych projektach C++ wizualizacji są wyświetlane **komunikaty VC + +** i przyciski **zastąpień VC** . Dodatkowe przyciski mogą być wyświetlane dla innych typów projektów. Aby uzyskać więcej informacji o przyciskach w oknie **Właściwości** , zobacz [okno właściwości](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementacja przycisków okna właściwości
 Po kliknięciu przycisku z **kategoryzacją** program Visual Studio wywoła interfejs <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> na obiekcie, który ma fokus, aby posortować jego właściwości według kategorii. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> jest zaimplementowana w obiekcie `IDispatch`, który jest prezentowany w oknie **Właściwości** .

 Istnieją 11 wstępnie zdefiniowanych kategorii właściwości, które mają wartości ujemne. Można definiować niestandardowe kategorie, ale zalecamy przypisanie im wartości dodatnich, aby odróżnić je od wstępnie zdefiniowanych kategorii.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> zwraca odpowiednią wartość kategorii właściwości dla określonej właściwości. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> zwraca ciąg, który zawiera nazwę kategorii. Musisz zapewnić obsługę niestandardowych wartości kategorii, ponieważ program Visual Studio wie standardowe wartości kategorii właściwości.

 Po kliknięciu przycisku z **alfabetem** właściwości są wyświetlane w kolejności alfabetycznej według nazwy. Nazwy są pobierane przez `IDispatch` zgodnie z zlokalizowanym algorytmem sortowania.

 Po otwarciu okna **Właściwości** przycisk **Właściwości** jest automatycznie pokazywany jako zaznaczony. W innych częściach środowiska zostanie wyświetlony ten sam przycisk, a następnie można kliknąć go, aby wyświetlić okno **Właściwości** .

 Przycisk **strony właściwości** jest niedostępny, jeśli `ISpecifyPropertyPages` nie jest zaimplementowany dla wybranego obiektu. Na stronach właściwości są wyświetlane właściwości zależne od konfiguracji, które są zwykle skojarzone z rozwiązaniami i projektami, ale można je także kojarzyć z elementami projektu (na przykład C++w wizualizacji).

> [!NOTE]
> Nie można dodać przycisków paska narzędzi do okna **Właściwości** przy użyciu kodu niezarządzanego. Aby dodać przycisk paska narzędzi, należy utworzyć obiekt zarządzany, który pochodzi z <xref:System.Windows.Forms.Design.PropertyTab>.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)