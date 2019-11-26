---
title: Korzystanie z przybornika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba8a37ac9e049455ffe19314dee0e228c3c14c97
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295608"
---
# <a name="using-the-toolbox"></a>Korzystanie z Przybornika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą przybornika można dodawać kontrolki i inne elementy do projektu. Możesz przeciągać i upuszczać inne kontrolki na powierzchnię projektanta jest używany i zmień rozmiar i położenie kontrolki.

 Przybornik pojawia się w połączeniu z widokami projektanta, takimi jak widok projektanta pliku XAML. W przyborniku są wyświetlane tylko te kontrolki, które mogą być używane w bieżącym projektancie.

 Wersja .NET Framework, do której odwołuje się projekt, wpływa również na zestaw kontrolek widocznych w przyborniku. Domyślnie projekty [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] są przeznaczone dla .NET Framework 4.5.1. Można ustawić dla projektu inną wersję .NET Framework, wybierając węzeł projektu w **Eksplorator rozwiązań**, a następnie przechodząc do pozycji **Właściwości/aplikacja/platforma docelowa**.

## <a name="managing-the-toolbox-and-its-controls"></a>Zarządzanie przybornikiem i jego kontrolkami
 Domyślnie Przybornik jest zwinięty wzdłuż lewej krawędzi środowiska IDE programu Visual Studio i pojawia się po przesunięciu kursora nad nim. Możesz przypiąć Przybornik (klikając ikonę **pinezki** na pasku narzędzi przybornika), tak aby pozostała otwarta po przesunięciu kursora. Możesz również oddokować okno przybornika i przeciągnąć je w dowolne miejsce na ekranie. Przybornik można zadokować, oddokować i ukryć, klikając prawym przyciskiem myszy pasek narzędzi przybornika i wybierając jedną z opcji.

 Można zmienić rozmieszczenie elementów na karcie przybornika lub dodać niestandardowe karty i elementy przy użyciu następujących poleceń w menu kontekstowym:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Pokaż wszystko** — pokazuje wszystkie możliwe kontrolki (nie tylko te, które mają zastosowanie do bieżącego projektanta).

- **Widok listy** — pokazuje kontrolki na liście pionowej. Jeśli nie jest zaznaczone, formanty są wyświetlane w poziomie.

- **Wybierz elementy** — otwiera okno dialogowe **Wybierz elementy przybornika** , aby można było określić elementy, które są wyświetlane w **przyborniku**. Możesz pokazać lub ukryć element, zaznaczając lub usuwając zaznaczenie pola wyboru.

- **Sortuj elementy alfabetycznie** — sortuje elementy według nazwy.

- **Resetuj pasek narzędzi** — przywraca domyślne ustawienia i elementy przybornika.

- **Dodaj kartę** — dodaje nową kartę przybornika.

- **Przenieś w górę** — przenosi zaznaczony element w górę.

- **Przenieś w dół** — przenosi zaznaczony element w dół.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Tworzenie i dystrybuowanie niestandardowych formantów przybornika
 Możesz utworzyć niestandardową kontrolkę przybornika w Visual Basic lub C#wizualizacji, a następnie można rozpocząć od szablonu projektu opartego na [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) lub [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). Następnie można rozesłać swój formant do członków zespołu lub opublikować go w sieci Web za pomocą [Instalatora formantów przybornika](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).
