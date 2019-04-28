---
title: Polecenie Dostępność | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7dfe8a6b3e4c84fd97a159f6ac43e0de47536f0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861817"
---
# <a name="command-availability"></a>Dostępność poleceń

Kontekst programu Visual Studio Określa, jakie polecenia są dostępne. Kontekst można zmienić w zależności od bieżącego projektu, bieżącego edytora, pakietów VSPackage, które są ładowane i inne aspekty zintegrowanego środowiska programistycznego (IDE).

## <a name="command-contexts"></a>Konteksty polecenia

Następujących kontekstów się polecenia są najbardziej rozpowszechnione:

- IDE: Polecenia dostarczane przez środowisko IDE, są zawsze dostępne.

- {1&gt;VSPackage&lt;1}. Pakietów VSPackage można zdefiniować, kiedy są polecenia mają być wyświetlane lub ukryte.

- Projekt: Projekt polecenia pojawiają się tylko dla obecnie wybranego projektu.

- Edytor: Tylko jeden z nich może być aktywny w danym momencie. Polecenia z aktywnego edytora są dostępne. Edytor ściśle współpracuje z usługą language. Usługa językowa musi przetworzyć polecenia w kontekście skojarzonego edytora.

- Typ pliku: Edytor mogą ładować więcej niż jeden typ plików. Dostępne polecenia można zmienić w zależności od typu pliku.

- Aktywne okno: Ostatnie aktywne okno dokumentu ustawia kontekstu interfejsu użytkownika dla powiązań klawiszy. Jednak okna narzędzi, które ma jedną tabelę powiązanie klucza, który przypomina wewnętrznej przeglądarki sieci web można również ustawić kontekstu interfejsu użytkownika. Dla systemu windows z wieloma kartami dokumentu, takich jak edytor HTML każda karta ma innego polecenia kontekstu identyfikatora GUID. Po zarejestrowaniu okna narzędzia jest zawsze dostępne na **widoku** menu.

- Kontekst interfejsu użytkownika: Konteksty interfejsu użytkownika są identyfikowane za pomocą wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> klasy, na przykład <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> podczas kompilowania rozwiązania lub <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> gdy aktywny jest debugera. Wiele kontekstów interfejsu użytkownika może być aktywne w tym samym czasie.

## <a name="define-custom-context-guids"></a>Zdefiniuj kontekstowego identyfikatorów GUID

Jeśli kontekst odpowiednie polecenia, identyfikator GUID nie jest już zdefiniowany, możesz zdefiniować w swojej pakietu VSPackage i Zaprogramuj się być aktywne lub nieaktywne zgodnie z potrzebami można kontrolować widoczność poleceń:

1. Rejestrowanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.

2. Pobieranie stanu kontekstu identyfikatora GUID, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.

3. Włączanie i wyłączanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.

> [!CAUTION]
> Upewnij się, że Twoje pakietu VSPackage nie wpływa na wszystkich kontekstach istniejące identyfikatory GUID ponieważ innych pakietów VSPackage może zależeć od ich.

## <a name="see-also"></a>Zobacz także

- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)