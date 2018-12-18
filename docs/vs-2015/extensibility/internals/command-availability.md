---
title: Polecenie Dostępność | Dokumentacja firmy Microsoft
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
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b822f85a0eda7952db37f1479ce6e8c536589716
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773265"
---
# <a name="command-availability"></a>Dostępność poleceń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kontekst programu Visual Studio Określa, jakie polecenia są dostępne. Kontekst można zmienić w zależności od bieżącego projektu, bieżącego edytora, pakietów VSPackage, które są ładowane i inne aspekty zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="command-contexts"></a>Konteksty polecenia  
 Następujących kontekstów się polecenia są najbardziej rozpowszechnione.  
  
-   **IDE** poleceń dostępnych w IDE, są zawsze dostępne.  
  
-   **Pakietu VSPackage** pakietów VSPackage można zdefiniować, kiedy są polecenia mają być wyświetlane lub ukryte.  
  
-   **Projekt** polecenia projektu są widoczne tylko dla obecnie wybranego projektu.  
  
-   **Edytor** w danym momencie tylko jeden z nich może być aktywne. Polecenia z aktywnego edytora są dostępne. Edytor ściśle współpracuje z usługą language. Usługa językowa musi przetworzyć polecenia w kontekście skojarzonego edytora.  
  
-   **Typ pliku** edytora mogą ładować więcej niż jeden typ plików. Dostępne polecenia można zmienić w zależności od typu pliku.  
  
-   **Aktywne okno** ostatniego aktywne okno dokumentu ustawia kontekst interfejsu użytkownika dla powiązań klawiszy. Jednak okna narzędzi, który zawiera klucz powiązania podobny wewnętrznej przeglądarki sieci Web można również ustawić kontekstu interfejsu użytkownika. Dla systemu windows z wieloma kartami dokumentu, takich jak edytor HTML każda karta ma innego polecenia kontekstu identyfikatora GUID. Po zarejestrowaniu okna narzędzia jest zawsze dostępne na **widoku** menu.  
  
-   **Kontekstu interfejsu użytkownika** kontekstów interfejsu użytkownika są identyfikowane za pomocą wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> klasy, na przykład <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> podczas kompilowania rozwiązania lub <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> gdy aktywny jest debugera. Wiele kontekstów interfejsu użytkownika może być aktywne w tym samym czasie.  
  
## <a name="defining-custom-context-guids"></a>Definiowanie kontekstowego identyfikatorów GUID  
 Jeśli kontekst odpowiednie polecenia, identyfikator GUID nie jest już zdefiniowany, można zdefiniować, w swojej pakietu VSPackage i Zaprogramuj się być aktywne lub nieaktywne zgodnie z potrzebami można kontrolować widoczność poleceń.  
  
1.  Rejestrowanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.  
  
2.  Pobieranie stanu kontekstu identyfikatora GUID, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.  
  
3.  Włączanie i wyłączanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.  
  
    > [!CAUTION]
    >  Upewnij się, że Twoje pakietu VSPackage nie wpływa na wszystkich kontekstach istniejące identyfikatory GUID ponieważ innych pakietów VSPackage może zależeć od ich.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

