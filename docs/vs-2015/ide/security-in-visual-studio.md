---
title: Zabezpieczenia
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f89e9a58d1ea501b9d92a44eead5e343cc7c014b
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57866940"
---
# <a name="security-in-visual-studio"></a>Zabezpieczenia w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Należy rozważyć bezpieczeństwo we wszystkich aspektach programowania aplikacji, od projektowania do wdrożenia. Rozpocznij od uruchamianie programu Visual Studio w bezpieczny sposób. Zobacz [uprawnienia użytkownika](../ide/user-permissions-and-visual-studio.md).

 Aby efektywnie rozwijać bezpieczne aplikacje, powinieneś rozumieć podstawy pojęć związanych z bezpieczeństwem i funkcji zabezpieczeń platform, dla których tworzysz. Należy również mieć świadomość bezpiecznych technik kodowania.

## <a name="understanding-security"></a>Opis zabezpieczeń
 [Zabezpieczenia](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) zabezpieczenia dostępu kodu w tym artykule opisano .NET Framework, zabezpieczenia oparte na rolach, zasady zabezpieczeń i narzędzia zabezpieczeń.

## <a name="coding-for-security"></a>Bezpieczne kodowanie
 Większość błędów kodowania, które powodują powstanie luk w zabezpieczeniach, występuje, ponieważ deweloperzy mogą stosować błędne założenia podczas pracy z danymi wejściowymi użytkownika lub ponieważ nie w pełni rozumieją platformę, dla której tworzą.

 [Kodowanie wytyczne dotyczące bezpiecznego](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) zawiera wskazówki dotyczące klasyfikacji składników, aby rozwiązywać problemy z bezpieczeństwem.

 [Najlepsze rozwiązania dotyczące zabezpieczeń](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) Discusses przepełnienia bufora oraz pełny obraz zabezpieczeń Microsoft Visual C++ umożliwia sprawdzenie funkcji dostarczanej przez flagę czasu kompilacji/GS.
