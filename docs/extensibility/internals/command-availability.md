---
title: Dostępność poleceń | Dokumenty firmy Microsoft
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709696"
---
# <a name="command-availability"></a>Dostępność poleceń

Kontekst programu Visual Studio określa, które polecenia są dostępne. Kontekst może ulec zmianie w zależności od bieżącego projektu, bieżącego edytora, pakietów VSPackages, które są ładowane i innych aspektów zintegrowanego środowiska programistycznego (IDE).

## <a name="command-contexts"></a>Konteksty poleceń

Następujące konteksty polecenia są najczęściej:

- IDE: Polecenia dostarczone przez IDE są zawsze dostępne.

- VSPackage: VSPackages można zdefiniować, kiedy polecenia mają być wyświetlane lub ukryte.

- Projekt: Polecenia projektu są wyświetlane tylko dla aktualnie wybranego projektu.

- Edytor: Tylko jeden edytor może być aktywny w czasie. Dostępne są polecenia z aktywnego edytora. Edytor ściśle współpracuje z usługą językową. Usługa języka musi przetwarzać jego polecenia w kontekście skojarzonego edytora.

- Typ pliku: edytor może załadować więcej niż jeden typ pliku. Dostępne polecenia mogą się zmieniać w zależności od typu pliku.

- Aktywne okno: Ostatnie okno aktywnego dokumentu ustawia kontekst interfejsu użytkownika dla powiązań kluczy. Jednak okno narzędzia, które ma tabelę powiązania kluczy, która przypomina wewnętrzną przeglądarkę sieci Web, może również ustawić kontekst interfejsu użytkownika. W przypadku okien dokumentów z wieloma kartami, takich jak edytor HTML, każda karta ma inny identyfikator GUID kontekstu polecenia. Po zarejestrowaniu okna narzędzia jest ono zawsze dostępne w menu **Widok.**

- Kontekst interfejsu użytkownika: konteksty interfejsu użytkownika są <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> identyfikowane przez <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> wartości klasy, na <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> przykład, gdy rozwiązanie jest budowane lub gdy debuger jest aktywny. Wiele kontekstów interfejsu użytkownika może być aktywnych w tym samym czasie.

## <a name="define-custom-context-guids"></a>Definiowanie identyfikatorów GUID kontekstu niestandardowego

Jeśli identyfikator GUID odpowiedniego kontekstu polecenia nie jest jeszcze zdefiniowany, można zdefiniować go w programie VSPackage, a następnie zaprogramować go jako aktywny lub nieaktywny zgodnie z wymaganiami do kontrolowania widoczności poleceń:

1. Zarejestruj identyfikatory GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> kontekstu, wywołując metodę.

2. Pobierz stan guid kontekstu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> wywołując metodę.

3. Włączanie i wyłączanie identyfikatorów <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> GUID kontekstu przez wywołanie metody.

> [!CAUTION]
> Upewnij się, że vsPackage nie wpływa na istniejące identyfikatory GUID kontekstu, ponieważ inne VSPackages może zależeć od nich.

## <a name="see-also"></a>Zobacz też

- [Obiekty kontekstu zaznaczenia](../../extensibility/internals/selection-context-objects.md)
- [Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
