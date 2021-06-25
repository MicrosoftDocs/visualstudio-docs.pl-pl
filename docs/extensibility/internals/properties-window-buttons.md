---
title: Przyciski okna właściwości | Microsoft Docs
description: Dowiedz się więcej o przyciskach wyświetlanych domyślnie na pasku narzędzi okno Właściwości oraz o implementacji przycisków.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c45d6cf0f271683c3c708bd71ef46377a5c5ca
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903453"
---
# <a name="properties-window-buttons"></a>Przyciski okna właściwości
W zależności od języka programowania i typu produktu niektóre przyciski są domyślnie wyświetlane na pasku narzędzi **okna** Właściwości. We wszystkich przypadkach wyświetlane są **przyciski Kategoryzowane,** **Alfabetyczne,** **Właściwości** i **Strony** właściwości. W języku Visual C# i Visual Basic zostanie **również** wyświetlony przycisk Zdarzenia. W niektórych Visual C++ projektach są wyświetlane komunikaty **VC++** i przyciski **Przesłonięcia VC.** Dodatkowe przyciski mogą być wyświetlane dla innych typów projektów. Aby uzyskać więcej informacji na temat przycisków w **oknie** Właściwości, zobacz [Okno właściwości](../../ide/reference/properties-window.md).

## <a name="implementation-of-properties-window-buttons"></a>Implementacja przycisków okna właściwości
 Po kliknięciu **przycisku Categorized** (Skategoryzowana) Visual Studio interfejs obiektu, który ma fokus na posortowanie <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> właściwości według kategorii. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> Jest zaimplementowany `IDispatch` w obiekcie, który jest przedstawiony w **oknie** Właściwości.

 Istnieje 11 wstępnie zdefiniowanych kategorii właściwości, które mają wartości ujemne. Można definiować kategorie niestandardowe, ale zalecamy przypisanie im wartości dodatnich w celu odróżnienia ich od wstępnie zdefiniowanych kategorii.

 Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> zwraca odpowiednią wartość kategorii właściwości dla określonej właściwości. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> zwraca ciąg zawierający nazwę kategorii. Wystarczy zapewnić obsługę niestandardowych wartości kategorii, ponieważ Visual Studio zna standardowe wartości kategorii właściwości.

 Po kliknięciu przycisku **Alfabetyczne** właściwości są wyświetlane w kolejności alfabetycznej według nazwy. Nazwy są pobierane przez program `IDispatch` zgodnie ze zlokalizowanym algorytmem sortowania.

 Po **otwarciu** okna Właściwości przycisk **Właściwości** jest automatycznie wyświetlany jako wybrany. W innych częściach środowiska jest wyświetlany ten sam przycisk i można go kliknąć, aby wyświetlić **okno** Właściwości.

 Przycisk **Strony właściwości** jest niedostępny, jeśli nie został `ISpecifyPropertyPages` zaimplementowany dla wybranego obiektu. Strony właściwości zawierają właściwości zależne od konfiguracji, które są zwykle skojarzone z rozwiązaniami i projektami, ale można je również skojarzyć z elementami projektu (na przykład w Visual C++).

> [!NOTE]
> Nie można dodawać przycisków paska narzędzi do **okna Właściwości** przy użyciu kodu niezaimażowego. Aby dodać przycisk paska narzędzi, należy utworzyć obiekt zarządzany, który pochodzi <xref:System.Windows.Forms.Design.PropertyTab> od .

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
