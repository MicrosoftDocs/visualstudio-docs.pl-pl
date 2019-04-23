---
title: Korzystanie z przybornika | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 207beb085046748a4eaabdff025cd461c5ddba26
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073367"
---
# <a name="using-the-toolbox"></a>Korzystanie z Przybornika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przybornik służy do dodawania formantów i innych elementów do projektu. Możesz przeciągać i upuszczać inne kontrolki na powierzchnię projektanta jest używany i zmień rozmiar i położenie kontrolki.  
  
 Przybornik pojawi się w połączeniu z projektanta widoków, takich jak Widok projektanta w pliku XAML. Pasek narzędzi wyświetla tylko formanty, które mogą być używane w bieżącym projektancie.  
  
 Wersja programu .NET Framework, że projekt jest ukierunkowany również wpływa na zbiór kontrolek widocznych w przyborniku. Domyślnie [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] projekty ukierunkowane na .NET Framework 4.5.1. Można ustawić projekt pod kątem innej wersji programu .NET Framework, wybierając węzeł projektu w **Eksploratora rozwiązań**, a następnie przechodząc do **aplikacji/właściwości/Target Framework**.  
  
## <a name="managing-the-toolbox-and-its-controls"></a>Zarządzanie przybornika i jego formantów  
 Domyślnie przybornik jest zwinięta z lewej strony środowiska IDE programu Visual Studio i jest wyświetlany, gdy kursor zostanie przeniesiony nad nim. Możesz przypiąć przybornika (klikając **numeru Pin** ikonę na pasku narzędzi przybornika) tak, aby zostanie zamknięte po przeniesieniu kursora. Można oddokować okno przybornika i przeciągnij w dowolne miejsce na ekranie. Można zadokować, oddokować i ukryć przybornik, kliknij prawym przyciskiem myszy pasek narzędzi przybornika i wybierając jedną z opcji.  
  
 Można zmienić kolejność elementów na karcie przybornika lub dodać niestandardowe karty i elementów za pomocą następujących poleceń w menu kontekstowym:  
  
- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.  
  
- **Pokaż wszystkie** — pokazuje wszystkie możliwe kontrole (nie tylko tych, które są stosowane do bieżącego projektanta).  
  
- **Widok listy** — zawiera kontrolki w pionie listy. Jeśli nie jest zaznaczone, formanty są wyświetlane w poziomie.  
  
- **Wybierz elementy** -otwiera **wybierz elementy przybornika** okno dialogowe, aby określić elementy, które pojawiają się w **przybornika**. Możesz pokazać lub ukryć element, zaznaczając lub usuwając zaznaczenie pola wyboru.  
  
- **Sortowanie elementów alfabetycznie** — Sortuje elementy według nazwy.  
  
- **Resetuj narzędzi** — przywraca domyślne ustawienia przybornika i elementów.  
  
- **Dodaj kartę** — dodaje nową kartę przybornika.  
  
- **Przenieś w górę** -Przesuwa wybrany element w górę.  
  
- **Przenieś w dół** -Przenosi zaznaczony element w dół.  
  
## <a name="creating-and-distributing-custom-toolbox-controls"></a>Tworzenie i rozpowszechnianie kontrolki przybornika niestandardowego  
 Kontrolki przybornika niestandardowego można utworzyć w języku Visual Basic lub Visual C# i można uruchomić za pomocą szablonu projektu, który jest oparty na [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) lub [Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md). Można dystrybuować formantu do członków zespołu lub opublikować go w sieci web za pomocą [Instalatora kontrolki przybornika](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).
