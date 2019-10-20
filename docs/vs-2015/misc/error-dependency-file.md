---
title: 'Błąd: nie można &#39;skopiować&#39; pliku zależności &#39;w&#39; projekcie projektu do katalogu uruchomieniowego, ponieważ spowodowałoby to konflikt z plikiem &#39;&#39; zależności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656048"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Błąd: nie można &#39;skopiować&#39; pliku zależności &#39;w&#39; projekcie projektu do katalogu uruchomieniowego, ponieważ spowodowałoby to konflikt z plikiem &#39;zależności&#39;
Występuje konflikt między odwołaniami; więcej niż jedna odrębna zależność o tej samej nazwie pliku jest kopiowana do katalogu bin w celu uruchomienia aplikacji. Katalog uruchamiania nie może rozwiązać konfliktu, ponieważ żadne z tych zależności nie są odwołaniami podstawowymi.

 Ten błąd spowoduje niepowodzenie kompilacji.

 Dwukrotne kliknięcie tego elementu Lista zadań spowoduje przejście do węzła odwołania w projekcie, w którym występuje konflikt.

 **Aby poprawić ten błąd**

- Utwórz jeden z zestawów bezpośrednio odwołanie do projektu. Możliwym minusem tego podejścia jest to, że wybór zestawu nie jest gwarantowany do pracy z zestawami wymagającymi innej wersji przywoływanego zestawu.

     \- lub-

- Upewnij się, że obie kopie zestawu są silne i znajdują się w globalnej pamięci podręcznej zestawów. Eliminuje to konieczność kopiowania zestawów do katalogu bin.

## <a name="see-also"></a>Zobacz też
 [Zarządzanie odwołaniami w](../ide/managing-references-in-a-project.md) [globalnej pamięci podręcznej zestawów](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [zestawy o silnych nazwach](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [zestaw wersja](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [instrukcje: Tworzenie i usuwanie zależności projektu](../ide/how-to-create-and-remove-project-dependencies.md)