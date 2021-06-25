---
title: Wzorce interakcji dla Visual Studio | Microsoft Docs
description: Poznaj bibliotekę typowych wzorców interakcji, których można używać podczas tworzenia nowych funkcji dla Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 13a2ec4332cf8010dc5d214dfd61936725ac2063
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900554"
---
# <a name="interaction-patterns-for-visual-studio"></a>Wzorce interakcji dla programu Visual Studio
## <a name="overview"></a>Omówienie
 Ogólnie rzecz biorąc, wzorzec projektowy jest podstawą projektu, który można zastosować w określonych sytuacjach w celu rozwiązywania problemów z podobnymi zestawami ograniczeń. Projektanci funkcji i systemów używają tych wzorców projektowych jako punktów początkowych, które następnie można dostosować do ich określonej sytuacji.

 Visual Studio zawiera bibliotekę typowych wzorców interakcji, które należy wziąć pod uwagę podczas tworzenia nowych funkcji. Istnieją dwa podstawowe konteksty naszych wzorców projektowych: Visual Studio Client (devenv) i GitHub Codespaces (wcześniej Visual Studio Online). W przypadku niektórych problemów projektowych istnieje powszechny wzorzec, który dobrze sprawdza się we wszystkich sytuacjach. Jednak w wielu przypadkach rozwiązanie może różnić się w przypadku interfejsu użytkownika, który jest prezentowany w przeglądarce, i tego, który jest hostowany w aplikacji klienckiej.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio wzorców klienta

|Typ wzorca|Opis|Przykłady|
|------------------|-----------------|--------------|
|**Wzorce na poziomie aplikacji**|Wzorce wysokiego poziomu wspólne dla aplikacji, określanie lub wyświetlanie kontekstu aplikacji oraz zawierające w nich wzorce złożone i kontrolne|- Okna narzędzi<br />- Okna dokumentów|
|**Wzorce złożone**|Typowe wzorce, które mogą obejmować różne wzorce aplikacji, lub rozpoznany wzorzec, który składa się z kilku kontrolek w odrębnej konfiguracji|- Przełączanie widoku<br />- Konstruktorzy list<br />— Wyświetlanie danych<br />- Powiadomienia<br />— Walidacja<br />- Modele wyboru|
|**Wzorce kontrolek**|Szczegółowe informacje na temat oczekiwanego zachowania kontrolek niskiego poziomu|— Widoki drzewa<br />- Edytowanie w kontrolce siatki|

## <a name="application-patterns"></a>Wzorce aplikacji
 Na wysokim poziomie interfejs Visual Studio składa się z wielu okien, okien dialogowych, poleceń i pasków narzędzi w ramach jednego środowiska IDE. Hierarchia Visual Studio określa menu kontekstowe i menu dysków. Kluczowe punkty integracji w interfejsie użytkownika środowiska IDE to okna dokumentów, okna narzędzi, projekty, struktura poleceń, edytor tekstu, przybornik, okno Właściwości i narzędzia > opcje.

 Istnieją podstawowe wzorce użycia dla każdego z kluczowych punktów integracji w interfejsie użytkownika środowiska IDE:

- [Menu i polecenia dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakcje okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna narzędzi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konwencje edytora dokumentów](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Typowe wzorce kontrolek
 Wzorce kontrolek dotyczą głównie zachowania poszczególnych kontrolek. Jest to jeden z obszarów, w którym spójność jest najbardziej krytyczna.

 Najbardziej typowe kontrolki w Visual Studio powinny być zgodne z wytycznymi systemu Windows dla komputerów stacjonarnych. Nasze wytyczne obejmują tylko obszary, w których musimy rozszerzyć typowe konwencje o interakcje specyficzne dla Visual Studio, lub miejsca, w których całkowicie je przesłoniliśmy, aby dostosować Visual Studio do potrzeb naszych zaawansowanych użytkowników.

- [Typowe wzorce kontrolek dla programu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Typowe kontrolki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Przyciski i hiperlinki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Wzorce złożone
 Istnieje wiele sposobów, na które użytkownicy oczekują wykonania zadań. Wszędzie tam, gdzie to możliwe, funkcje powinny być zaprojektowane tak, aby używać tych wzorców zarówno do interakcji, jak i projektowania wizualnego.

 Chociaż istnieje wiele wzorców złożonych w Visual Studio, najważniejsze z nich są:

- [Wzorce złożone dla programu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfejs użytkownika obiektu on-object i podgląd](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Ustawienia trwałości i zapisywania](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
