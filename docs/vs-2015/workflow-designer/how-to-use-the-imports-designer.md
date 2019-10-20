---
title: 'Instrukcje: korzystanie z projektanta Imports | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47b5055cca0b00e7fdec49947df13b473a090aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659083"
---
# <a name="how-to-use-the-imports-designer"></a>Instrukcje: korzystanie z projektanta importów
Projektant Imports umożliwia wprowadzanie przestrzeni nazw dla typów, które będą używane w wyrażeniach. Podobnie jak w przypadku **importów** lub **użycia** słów kluczowych w C#Visual Basic .NET i, określenie przestrzeni nazw w projektancie Imports umożliwia po prostu wprowadzanie nazwy typu w wyrażeniu zamiast w pełni kwalifikowanej nazwy typu wersji.

 Projektant Imports reaguje na obie zmiany w interfejsie użytkownika i zmiany wprowadzone podczas zapisywania przepływu pracy. Gdy przepływ pracy zostanie zapisany, przestrzenie nazw mogą być dodawane automatycznie do projektanta Imports. Należą do nich między innymi:

- Przestrzenie nazw dla wszystkich typów używanych w deklaracjach zmiennych i argumentów.

- Przestrzenie nazw dla wszystkich typów używanych w wyrażeniach.

- Wszystkie inne przestrzenie nazw wymagane do serializacji przepływu pracy (na przykład przestrzenie nazw używane przez działania niestandardowe porzucone w przepływie pracy).

  Po zapisaniu przepływu pracy można zauważyć, że niektóre przestrzenie nazw usunięte ręcznie są automatycznie dodawane do projektanta importów z powodu logiki opisanej na poprzedniej liście.

### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Aby dodać przestrzeń nazw do listy importowanych przestrzeni nazw

1. Otwórz aplikację usługi przepływu pracy WCF, aplikację konsoli przepływu pracy lub projekt biblioteki działań w [!INCLUDE[vs2010](../includes/vs2010-md.md)] lub ponownie hostowanej aplikacji przepływu pracy.

2. Kliknij pozycję **Importy** w dolnej części kanwy głównej. Zostanie wyświetlony Projektant Imports.

3. Wprowadź lub wybierz przestrzeń nazw z kontrolki listy rozwijanej w górnej części projektanta importów.

     Podczas pisania zostanie wyświetlona lista prawidłowych przestrzeni nazw, które pasują do wpisanych znaków.

4. Naciśnij klawisz **Enter** , aby dodać przestrzeń nazw do listy.

5. Jeśli chcesz usunąć przestrzeń nazw z listy, wybierz przestrzeń nazw, a następnie naciśnij klawisz **delete** na klawiaturze. Należy zauważyć, że przestrzeń nazw można usunąć tylko wtedy, gdy przestrzeń nazw jest nieprawidłowa z jakiegokolwiek powodu, na przykład jeśli zestaw zawierający przestrzeń nazw nie jest już przywoływany przez projekt.