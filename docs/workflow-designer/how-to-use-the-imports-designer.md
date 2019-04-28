---
title: 'Projektant przepływu pracy — jak: Używanie projektanta importów'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11c0c959964fee21f2cdfe098907ab2dfe184f7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949069"
---
# <a name="how-to-use-the-imports-designer"></a>Instrukcje: Używanie projektanta importów

Projektanta importów umożliwia wprowadzanie przestrzeni nazw dla typów, które będą używane w wyrażenia. Podobnie jak **importuje** lub **przy użyciu** słów kluczowych w języku Visual Basic i C#, określając przestrzeniach nazw projektanta importów umożliwiają wystarczy wprowadzić nazwę typu w wyrażeniu, a nie w pełni Wersja kwalifikowana nazwa typu.

Projektanta importów reaguje na zmiany w interfejsie użytkownika i zmian wprowadzonych po zapisaniu przepływu pracy. Po zapisaniu przepływu pracy, przestrzenie nazw mogą być dodawane automatycznie do projektanta importów. Należą do nich między innymi:

- Przestrzenie nazw wszystkie typy używane w deklaracji zmiennej i argument.

- Przestrzenie nazw wszystkie typy używane w wyrażeniach.

- Wszystkie inne obszary nazw wymagane dla serializacji przepływu pracy (na przykład, przestrzeń nazw używaną przez niestandardowe działania w przepływie pracy).

  Po zapisaniu przepływu pracy może się okazać, że niektóre przestrzenie nazw, który został ręcznie usunięty są automatycznie ponownie dodać do projektanta importów z powodu logiki opisane na powyższej liście.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Aby dodać przestrzeń nazw do listy importowanych przestrzeni nazw

1. Otwórz aplikacja usługi przepływu pracy WCF, aplikacja konsoli przepływu pracy lub działania projektu biblioteki w programie Visual Studio lub aplikacji rehostowanym przepływu pracy.

2. Kliknij przycisk **Importy** w dolnej części kanwy głównego. Pojawi się okno projektanta importów.

3. Wprowadź lub wybierz przestrzeń nazw z formantu listy rozwijanej w górnej części projektanta importów.

     Podczas wpisywania, zostanie wyświetlona lista prawidłowe przestrzenie nazw, które dopasowuje znaki wpisane.

4. Naciśnij klawisz **Enter** dodać przestrzeń nazw do listy.

5. Jeśli chcesz usunąć przestrzeni nazw z listy wybierz przestrzeń nazw, a następnie naciśnij klawisz **Usuń** kluczowe na klawiaturze. Należy pamiętać, że przestrzeń nazw można usunąć tylko jeśli przestrzeń nazw jest nieprawidłowa z jakiejkolwiek przyczyny, na przykład jeśli zestaw, który zawiera przestrzeń nazw nie jest już przywoływany przez projekt.