---
title: Wzorce interakcji dla programu Visual Studio | Microsoft Docs
description: Zapoznaj się z biblioteką typowych wzorców interakcji, których można użyć podczas tworzenia nowych funkcji dla programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 215fa0145a342820320980f629bb35678ce09680
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072939"
---
# <a name="interaction-patterns-for-visual-studio"></a>Wzorce interakcji dla programu Visual Studio
## <a name="overview"></a>Omówienie
 Wzorzec projektowy, ogólnie rzecz biorąc, stanowi rdzeń projektu, który może być stosowany w określonych sytuacjach w celu rozwiązywania problemów z podobnymi zestawami ograniczeń. Projektanci funkcji i systemów używają tych wzorców projektowych jako punktów początkowych, które można następnie dostosować do ich konkretnej sytuacji.

 Program Visual Studio ma bibliotekę wspólnych wzorców interakcji, które należy wziąć pod uwagę podczas tworzenia nowych funkcji. Istnieją dwa podstawowe konteksty dla naszych wzorców projektowych: Visual Studio Client (devenv) i GitHub Codespaces (dawniej Visual Studio Online). W przypadku niektórych problemów z projektowaniem istnieje powszechny wzorzec, który działa dobrze we wszystkich sytuacjach. W wielu przypadkach rozwiązanie może być inne dla interfejsu użytkownika, który jest prezentowany w przeglądarce i który jest hostowany w aplikacji klienckiej.

### <a name="visual-studio-client-pattern-types"></a>Typy wzorców klienta programu Visual Studio

|Typ wzorca|Opis|Przykłady|
|------------------|-----------------|--------------|
|**Wzorce na poziomie aplikacji**|Wzorce wysokiego poziomu wspólne dla aplikacji, określanie lub wyświetlanie kontekstu aplikacji oraz zawierające złożone i kontrolne wzorce w nich|-Okna narzędzi<br />— Okna dokumentów|
|**Wzorce złożone**|Typowe wzorce, które mogą obejmować między wzorcami aplikacji lub rozpoznany wzorzec składający się z kilku kontrolek w konfiguracji odrębnej|— Przełączanie widoku<br />-Lista konstruktorów<br />— Wyświetlanie danych<br />— Powiadomienia<br />-Walidacja<br />-Wybór modeli|
|**Wzorce kontrolek**|Szczegóły dotyczące sposobu zachowania formantów niskiego poziomu|-Widoki drzewa<br />-Edycja w kontrolce siatki|

## <a name="application-patterns"></a>Wzorce aplikacji
 Na wysokim poziomie interfejs programu Visual Studio zawiera wiele okien, okien dialogowych, poleceń i pasków narzędzi w ramach jednego środowiska IDE. Hierarchia programu Visual Studio określa menu kontekstowe i dyski. Kluczowe punkty integracji w interfejsie użytkownika IDE to okna dokumentów, okna narzędzi, projekty, struktura poleceń, Edytor tekstu, Przybornik, okno Właściwości i narzędzia > opcje.

 Dla każdego z kluczowych punktów integracji w interfejsie użytkownika IDE istnieją podstawowe wzorce użycia:

- [Menu i polecenia dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakcje okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna narzędzi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konwencje edytora dokumentów](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Wzorce wspólnych kontrolek
 Wzorce formantów mają głównie wpływ na zachowanie poszczególnych kontrolek. Jest to jeden obszar, w którym spójność jest najbardziej krytyczna.

 Większość typowych kontrolek w programie Visual Studio powinna być zgodna z zaleceniami systemu Windows dla komputerów stacjonarnych. Nasze wytyczne obejmują tylko obszary, w których musimy rozszerzyć wspólne konwencje o interakcje specyficzne dla programu Visual Studio lub miejsca, w których zastępują wskazówki w całości w celu dostosowywania programu Visual Studio, aby zaspokoić potrzeby naszych zaawansowanych użytkowników.

- [Typowe wzorce kontrolek dla programu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Typowe kontrolki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Kontrolki tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Przyciski i hiperlinki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Wzorce złożone
 Istnieją różne sposoby wykonywania zadań przez użytkowników. Wszędzie tam, gdzie to możliwe, funkcje powinny być zaprojektowane tak, aby używać tych wzorców zarówno do interakcji, jak i do projektowania wizualnego.

 Chociaż w programie Visual Studio istnieje wiele wzorców złożonych, niektóre z najważniejszych w odniesieniu do spójności są następujące:

- [Wzorce złożone dla programu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfejs użytkownika i wgląd w obiekt](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Trwałość i zapisywanie ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
