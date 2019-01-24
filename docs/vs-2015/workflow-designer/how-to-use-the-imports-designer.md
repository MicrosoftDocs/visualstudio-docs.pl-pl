---
title: 'Instrukcje: Używanie projektanta importów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6eed27b9bfef272035f299af1a68a3788587f3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759926"
---
# <a name="how-to-use-the-imports-designer"></a>Instrukcje: Używanie projektanta importów
Projektanta importów umożliwia wprowadzanie przestrzeni nazw dla typów, które będą używane w wyrażenia. Podobnie jak **importuje** lub **przy użyciu** słów kluczowych w języku Visual Basic .NET i języka C#, określania przestrzeni nazw w projektanta importów umożliwiają wystarczy wprowadzić nazwę typu w wyrażeniu, a nie w pełni kwalifikowanej Nazwa typu wersji.  
  
 Projektanta importów reaguje na zmiany w interfejsie użytkownika i zmian wprowadzonych po zapisaniu przepływu pracy. Po zapisaniu przepływu pracy, przestrzenie nazw mogą być dodawane automatycznie do projektanta importów. Należą do nich między innymi:  
  
- Przestrzenie nazw wszystkie typy używane w deklaracji zmiennej i argument.  
  
- Przestrzenie nazw wszystkie typy używane w wyrażeniach.  
  
- Wszystkie inne obszary nazw wymagane dla serializacji przepływu pracy (na przykład, przestrzeń nazw używaną przez niestandardowe działania w przepływie pracy).  
  
  Po zapisaniu przepływu pracy może się okazać, że niektóre przestrzenie nazw, który został ręcznie usunięty są automatycznie ponownie dodać do projektanta importów z powodu logiki opisane na powyższej liście.  
  
### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Aby dodać przestrzeń nazw do listy importowanych przestrzeni nazw  
  
1.  Otwórz aplikacja usługi przepływu pracy WCF, aplikacja konsoli przepływu pracy lub działania projektu biblioteki w [!INCLUDE[vs2010](../includes/vs2010-md.md)] lub aplikacja rehostowanym przepływu pracy.  
  
2.  Kliknij przycisk **Importy** w dolnej części kanwy głównego. Pojawi się okno projektanta importów.  
  
3.  Wprowadź lub wybierz przestrzeń nazw z formantu listy rozwijanej w górnej części projektanta importów.  
  
     Podczas wpisywania, zostanie wyświetlona lista prawidłowe przestrzenie nazw, które dopasowuje znaki wpisane.  
  
4.  Naciśnij klawisz **Enter** dodać przestrzeń nazw do listy.  
  
5.  Jeśli chcesz usunąć przestrzeni nazw z listy wybierz przestrzeń nazw, a następnie naciśnij klawisz **Usuń** kluczowe na klawiaturze. Należy pamiętać, że przestrzeń nazw można usunąć tylko jeśli przestrzeń nazw jest nieprawidłowa z jakiejkolwiek przyczyny, na przykład jeśli zestaw, który zawiera przestrzeń nazw nie jest już przywoływany przez projekt.