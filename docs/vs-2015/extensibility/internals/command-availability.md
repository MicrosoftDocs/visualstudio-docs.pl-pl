---
title: Dostępność poleceń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780976"
---
# <a name="command-availability"></a>Dostępność poleceń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kontekst programu Visual Studio Określa, które polecenia są dostępne. Kontekst można zmienić w zależności od bieżącego projektu, bieżącego edytora, załadowanej pakietów VSPackage i innych aspektów zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="command-contexts"></a>Konteksty poleceń  
 Poniżej przedstawiono kontekst poleceń.  
  
- **Środowisko IDE** Polecenia dostarczone przez IDE są zawsze dostępne.  
  
- **Pakietu VSPackage** Pakietów VSPackage może zdefiniować, kiedy polecenia mają być wyświetlane lub ukryte.  
  
- **Projekt** Polecenia projektu są wyświetlane tylko dla aktualnie wybranego projektu.  
  
- **Edytor** Tylko jeden edytor może być aktywny w danym momencie. Dostępne są polecenia z aktywnego edytora. Edytor ściśle współpracuje z usługą języka. Usługa językowa musi przetwarzać swoje polecenia w kontekście skojarzonego edytora.  
  
- **Typ pliku** Edytor może załadować więcej niż jeden typ pliku. Dostępne polecenia mogą się zmieniać w zależności od typu pliku.  
  
- **Aktywne okno** Okno ostatniego aktywnego dokumentu ustawia kontekst interfejsu użytkownika dla powiązań kluczy. Jednak okno narzędzi, które ma tabelę powiązań kluczy przypominającą wewnętrzną przeglądarkę internetową, może również ustawić kontekst interfejsu użytkownika. W przypadku okien dokumentów z wielodostępnymi, takimi jak edytor HTML, każda karta ma inny identyfikator GUID kontekstu polecenia. Po zarejestrowaniu okna narzędzi jest ono zawsze dostępne w menu **Widok** .  
  
- **Kontekst interfejsu użytkownika** Konteksty interfejsu użytkownika są identyfikowane przez wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> klasy, na przykład <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> podczas kompilowania rozwiązania lub <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> gdy debuger jest aktywny. Jednocześnie może być aktywnych wiele kontekstów interfejsu użytkownika.  
  
## <a name="defining-custom-context-guids"></a>Definiowanie identyfikatorów GUID kontekstu niestandardowego  
 Jeśli odpowiedni identyfikator GUID kontekstu polecenia nie jest jeszcze zdefiniowany, można go zdefiniować w pakietu VSPackage, a następnie program powinien być aktywny lub nieaktywny, zgodnie z wymaganiami, aby kontrolować widoczność poleceń.  
  
1. Zarejestruj identyfikatory GUID kontekstu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metodę.  
  
2. Pobierz stan identyfikatora GUID kontekstu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metodę.  
  
3. Włącz i Wyłącz identyfikatory GUID kontekstu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.  
  
    > [!CAUTION]
    > Upewnij się, że pakietu VSPackage nie ma wpływu na żadne istniejące identyfikatory GUID kontekstu, ponieważ inne pakietów VSPackage mogą być od nich zależne.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md)   
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
