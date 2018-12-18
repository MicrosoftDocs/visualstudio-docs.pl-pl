---
title: Wybór obiektów kontekstu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: beaf1b9c67cdad3237d1ac48b4a8e464b0a203a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769397"
---
# <a name="selection-context-objects"></a>Obiekty kontekstu wyboru
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) używa obiektu kontekstu globalnego wyboru, aby określić, co powinno być wyświetlane w środowisku IDE. Każde okno w środowisku IDE może mieć własną obiekt kontekstu wybór wypchnięte do kontekst zaznaczenia globalnego. IDE aktualizuje kontekst zaznaczenia globalnego przy użyciu wartości z okna, gdy to okno ma fokus. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).  
  
 Każdej ramki okna lub lokacji w środowisku IDE ma usługi o nazwie <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Obiekt utworzony przez Twojego pakietu VSPackage, który jest zlokalizowany w ramki okna musi wywołać `QueryService` metodę, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfejsu.  
  
 Okna ramowe zachować części swoje informacje o kontekście wybór propagowanie kontekst zaznaczenia globalnych po ich uruchomieniu. Ta możliwość jest przydatna do okna narzędzi, które mogą mieć zaczynać się zaznaczenie jest puste.  
  
 Modyfikowanie zdarzeń wyzwalaczy kontekstu wyboru globalnego, które można monitorować pakietów VSPackage. Pakietów VSPackage można wykonywać następujące zadania przez zaimplementowanie `IVsTrackSelectionEx` i <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfejsów:  
  
- Zaktualizuj plik aktualnie aktywne w hierarchii.  
  
- Monitorowanie zmian w niektórych typów elementów. Na przykład, jeśli korzysta z Twojego pakietu VSPackage specjalny **właściwości** okna, można monitorować zmiany w aktywnej **właściwości** okno i ponownie uruchom Twoje żądanie.  
  
  Poniższa sekwencja zawiera typowe kurs wybór śledzenia.  
  
1.  IDE pobiera kontekst zaznaczenia z nowo otwartym oknie i umieszcza go w kontekście wyboru globalnego. Jeśli kontekst zaznaczenia używa HIERARCHY_DONTPROPAGATE lub SELCONTAINER_DONTPROPAGATE, te informacje nie są propagowane do kontekstu globalnego. Aby uzyskać więcej informacji, zobacz [informacje zwrotne dla użytkownika](../../extensibility/internals/feedback-to-the-user.md).  
  
2.  Zdarzenia powiadomień są emitowane do dowolnego pakietu VSPackage, który zażądał je.  
  
3.  Pakietu VSPackage działa na zdarzenia, które otrzymuje, wykonując działania, takie jak aktualizowanie hierarchii, ponowne uaktywnianie narzędzia lub inne podobne zadania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>   
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Wybór i aktualność w środowisku IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Typy projektów](../../extensibility/internals/project-types.md)

