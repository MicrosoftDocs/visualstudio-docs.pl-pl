---
title: Wzorce interakcji dla programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698376"
---
# <a name="interaction-patterns-for-visual-studio"></a>Wzorce interakcji dla programu Visual Studio
## <a name="overview"></a>Omówienie
 Wzorzec projektu, ogólnie rzecz biorąc, jest rdzeniem projektu, który może być stosowany w określonych sytuacjach w celu rozwiązania problemów z podobnymi zestawami ograniczeń. Projektanci funkcji i systemów używają tych wzorców projektowych jako punktów wyjścia, które można następnie dostosować do ich konkretnej sytuacji.

 Visual Studio ma bibliotekę typowych wzorców interakcji, które powinny być brane pod uwagę podczas tworzenia nowych funkcji. Istnieją dwa podstawowe konteksty dla naszych wzorców projektowych: Visual Studio Client (devenv) i Visual Studio Online. W przypadku niektórych problemów projektowych istnieje wszechobecny wzór, który działa dobrze we wszystkich sytuacjach. W wielu przypadkach jednak rozwiązanie może być różne dla interfejsu użytkownika, który jest prezentowany w przeglądarce i który jest obsługiwany w aplikacji klienckiej.

### <a name="visual-studio-client-pattern-types"></a>Typy wzorców klienta programu Visual Studio

|Typ wzoru|Opis|Przykłady|
|------------------|-----------------|--------------|
|**Wzorce na poziomie aplikacji**|Wzorce wysokiego poziomu wspólne dla aplikacji, określanie lub wyświetlanie kontekstu aplikacji oraz zawierające wzorce kompozytowe i kontrolne w nich zawarte|- Okna narzędziowe<br />- Okna dokumentów|
|**Wzory kompozytowe**|Typowe wzorce, które mogą obejmować wzorce aplikacji lub rozpoznany wzorzec składający się z kilku formantów w odrębnej konfiguracji|- Przełączanie widoku<br />- Budowniczowie list<br />- Wyświetlanie danych<br />- Powiadomienia<br />- Walidacja<br />- Modele selekcji|
|**Wzorce sterowania**|Szczegółowe informacje na temat tego, jak powinny zachowywać się kontrole niskiego poziomu|- Widoki drzewa<br />- Edycja w formancie siatki|

## <a name="application-patterns"></a>Wzorce aplikacji
 Na wysokim poziomie interfejs programu Visual Studio składa się z wielu okien, okien dialogowych, poleceń i pasków narzędzi w ramach jednego IDE. Hierarchia programu Visual Studio określa kontekst i dyski menu. Kluczowymi punktami integracji w interfejsie użytkownika IDE są okna dokumentów, okna narzędzi, projekty, struktura poleceń, edytor tekstu, przybornik, okno Właściwości i Opcje >.

 Istnieją podstawowe wzorce użycia dla każdego z kluczowych punktów integracji w interfejsie użytkownika IDE:

- [Menu i polecenia dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interakcje między oknami](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Okna narzędzi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Konwencje edytora dokumentów](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Typowe wzorce sterowania
 Wzorce kontroli są głównie o tym, jak poszczególne formanty mają się zachowywać. Jest to jeden z obszarów, w których spójność jest najbardziej krytyczna.

 Najczęściej formanty w programie Visual Studio należy postępować zgodnie z wytycznymi systemu Windows dla komputerów stacjonarnych. Nasze wytyczne obejmują tylko obszary, w których musimy rozszerzyć wspólne konwencje za pomocą interakcji specyficznych dla programu Visual Studio lub miejsca, w których całkowicie zastępujemy wytyczne, aby dostosować program Visual Studio do potrzeb naszych zaawansowanych użytkowników.

- [Typowe wzorce kontrolek dla programu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Typowe kontrolki](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Formanty tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Przyciski i hiperłącza](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Wzory kompozytowe
 Istnieje wiele sposobów, że użytkownicy oczekują do wykonywania zadań. Tam, gdzie to możliwe, funkcje powinny być zaprojektowane tak, aby używać tych wzorców zarówno do interakcji, jak i projektowania wizualnego.

 Chociaż istnieje wiele wzorów kompozytowych w programie Visual Studio, niektóre z najważniejszych w odniesieniu do spójności są:

- [Wzorce złożone dla programu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfejs użytkownika obiektu i podglądanie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modele wyboru](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Ustawienia trwałości i zapisywania](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
