---
title: Wzorce interakcji
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a7899fbd34d0f63b21fb13e224f2856a4dc74cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065171"
---
# <a name="interaction-patterns-for-visual-studio"></a>Wzorce interakcji dla programu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>Omówienie
 Wzorzec projektowania, ogólnie rzecz biorąc, to podstawowe rozwiązanie projektowania, które mogą być stosowane w określonych sytuacjach do rozwiązywania problemów z podobne zestawy warunków ograniczających. Projektanci systemu i funkcja pełnić te wzorce projektowe punktów początkowych — które następnie można dostosować do swoich konkretnej sytuacji.

 Program Visual Studio zawiera bibliotekę typowych wzorców interakcji, które należy uwzględnić podczas tworzenia nowych funkcji. Istnieją dwa konteksty core dla naszych wzorce projektowe: Visual Studio klienta (devenv) i Visual Studio Online. Niektóre problemy projektu jest wszechobecne wzorzec, który działa dobrze we wszystkich sytuacjach. W wielu przypadkach jednak rozwiązanie może być różne dla interfejsu użytkownika, który jest wyświetlenie w przeglądarce i to, co znajduje się w aplikacji klienckiej.

### <a name="visual-studio-client-pattern-types"></a>Typy wzorca w usłudze Visual Studio klientów

|Typ deseniu|Opis|Przykłady|
|------------------|-----------------|--------------|
|**Wzorce na poziomie aplikacji**|Wzorce wysokiego poziomu wspólne dla aplikacji, określania lub wyświetlanie kontekst aplikacji i zawierający wzorce złożone i kontroli w nich|— Windows narzędzie<br />-Okna dokumentów|
|**Wzorce złożone**|Typowe wzorce, które mogą rozciągać się na wzorce aplikacji lub rozpoznawanym wzorzec składa się z kilku formantów w różnych konfiguracji|-Przełączanie widoku<br />-Konstruktorzy list<br />— Wyświetlanie danych<br />-Powiadomienia<br />— Sprawdzanie poprawności<br />— Modele wybór|
|**Wzorce kontrolki**|Szczegółowe informacje, jak niskiego poziomu kontrolki powinny zachowywać się|-Widok drzewa<br />-Edycji w formancie siatki|

## <a name="application-patterns"></a>Wzorce aplikacji
 Na wysokim poziomie interfejsu programu Visual Studio składa się z wielu systemu windows, okien dialogowych, poleceń i paski narzędzi w ramach jednego środowiska IDE. Hierarchia programu Visual Studio Określa menu kontekstowe i dysków. Punkty integracji kluczy w interfejsie użytkownika środowiska IDE są okna dokumentów, okien narzędzi, projekty, strukturę polecenia, Edytor tekstu, przybornika, okno właściwości i narzędzia > Opcje.

 Dostępne są wzorce użycia podstawowego dla każdego z punktów integracji kluczy w interfejsie użytkownika środowiska IDE:

- [Menu i polecenia dla programu Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Wzorce aplikacji dla programu Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    - [Okno interakcji](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    - [Okna narzędzi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    - [Konwencje Edytor dokumentów](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    - [Okna dialogowe](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    - [Projekty](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Typowe wzorce kontrolki
 Wzorce kontrolki są głównie, informacje o poszczególnych kontrolkach powinny działać. Jest to jeden obszar, w którym jest najbardziej krytycznych spójności.

 Najczęstsze formanty w programie Visual Studio powinien być zgodny z wytycznymi pulpitu Windows. Nasze wskazówki zawierają tylko obszarów, w których należy rozszerzyć typowych konwersji za pomocą programu Visual Studio specyficznych interakcji lub miejsc, w których firma Microsoft zastępują wytycznych całkowicie Aby dostosować Visual Studio, aby zaspokoić potrzeby naszych zaawansowanych użytkowników.

- [Typowe wzorce kontrolek dla programu Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    - [Formanty standardowe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    - [Kontrolek tekstu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    - [Przyciski i hiperłączy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Wzorce złożone
 Istnieją różne sposoby, które użytkownicy chcą wykonywać zadania. Wszędzie tam, gdzie to możliwe, powinny być zaprojektowane funkcji dzięki tym wzorcom interakcji i projektowania wizualnego.

 Dostępnych jest wiele złożonych wzorców w programie Visual Studio, niektóre z najważniejszych w odniesieniu do spójności są:

- [Wzorce złożone dla programu Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    - [Interfejs użytkownika i wgląd w obiekcie](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    - [Wybór modeli](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    - [Trwałość i zapisywanie ustawień](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    - [Wprowadzanie dotykowe](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
