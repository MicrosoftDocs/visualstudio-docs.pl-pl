---
title: Przyciski okna właściwości | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d21e8d13ef8af83b12d30b6c78c253f371a11c30
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54973866"
---
# <a name="properties-window-buttons"></a>Przyciski okna właściwości
W zależności od języka programowania i typ produktu, domyślnie na pasku narzędzi są wyświetlane określone przyciski **właściwości** okna. We wszystkich przypadkach **kategorii**, **Alphabetized**, **właściwości**, i **stron właściwości** przyciski są wyświetlane. W środowisku Visual C# i Visual Basic **zdarzenia** przycisk jest również wyświetlany. W niektórych projektów języka Visual C++ **VC ++ wiadomości** i **zastępuje VC** przyciski są wyświetlane. Mogą być wyświetlane dodatkowe przyciski dla innych typów projektów. Aby uzyskać więcej informacji na temat przycisków w **właściwości** okna, zobacz [okno właściwości](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Implementacja przyciski okna właściwości  
 Po kliknięciu **kategorii** przycisk wywołań programu Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> interfejsu na obiekt, który ma fokus, by Sortuj właściwości według kategorii. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> jest wdrażana w `IDispatch` obiektów, które są prezentowane **właściwości** okna.  
  
 Istnieje 11 kategorii wstępnie zdefiniowanych właściwości, które mają wartości ujemnych. Można zdefiniować własne kategorie, ale zaleca się, że zostanie przypisana wartość dodatnią, aby odróżnić je od wstępnie zdefiniowanych kategorii.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Metoda zwraca wartość kategorii odpowiednie właściwości dla określonej właściwości. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Metoda zwraca ciąg zawierający nazwę kategorii. Wystarczy zapewniają obsługę wartości kategorię niestandardową, ponieważ wartości kategorii standardowe właściwości wie, Visual Studio.  
  
 Po kliknięciu **Alphabetized** przycisku właściwości są wyświetlane w porządku alfabetycznym według nazwy. Nazwy są pobierane przez `IDispatch` zgodnie z zlokalizowanych algorytmu sortowania.  
  
 Gdy **właściwości** okno jest otwarte, **właściwości** przycisk jest automatycznie wyświetlana zaznaczona. W innych częściach środowiska wyświetlany jest ten sam przycisk, a kliknięcie, aby pokazać **właściwości** okna.  
  
 **Stron właściwości** przycisk jest niedostępny, jeśli `ISpecifyPropertyPages` nie został zaimplementowany dla wybranego obiektu. Strony właściwości wyświetlania właściwości zależne od konfiguracji, które są zwykle skojarzone z rozwiązaniami i projektami, ale mogą być również być skojarzone z elementami projektu (na przykład w programie Visual C++).  
  
> [!NOTE]
>  Nie można dodać przyciski paska narzędzi na **właściwości** oknie za pomocą kodu niezarządzanego. Aby dodać przycisk paska narzędzi, należy utworzyć obiektu zarządzanego, która pochodzi od klasy <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)