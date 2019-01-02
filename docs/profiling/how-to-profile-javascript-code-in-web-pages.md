---
title: 'Instrukcje: Profiluj kod JavaScript na stronach sieci Web | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc3c83e81608d671db8bad655c4853e5262ea467
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863648"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Instrukcje: Profiluj kod JavaScript na stronach sieci web

Visual Studio Profiling Tools umożliwia zbieranie danych wydajności dla kodu JavaScript, która jest wykonywana w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, dowolnej strony sieci web lub aplikacji JavaScript przy użyciu Instrumentacji, metoda profilowania. Wymaga programu Internet Explorer 8 lub nowszy.

> [!WARNING]
> Aby profilować kod JavaScript w aplikacjach platformy uniwersalnej systemu Windows, zobacz [pamięć języka JavaScript](../profiling/javascript-memory.md) 

Aby utworzyć sesję wydajności, można użyć Kreatora profilowania. Określ metody instrumentacji, a następnie określ JavaScript profilowania opcję na stronie Instrumentacji w oknie dialogowym właściwości sesji wydajności.

Po określeniu profilowanie plików JavaScript, kod JavaScript, który wykonuje w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod, który jest wykonywany na serwerze są profilowane.

- Aby uzyskać [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, zarówno kod JavaScript, który jest wykonywany w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod, który jest wykonywany na serwerze są profilowane.

- Dla dowolnej strony sieci web kod JavaScript, który jest wykonywany w przeglądarce jest profilowana.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci web platformy ASP.NET

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci web w programie Visual Studio.

2. Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie kreatora wydajności, należy określić **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora, upewnij się, że bieżący projekt jest zaznaczony na liście elementów docelowych, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora wybierz **Profiluj kod JavaScript** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora kliknij **Zakończ** do uruchomienia aplikacji sieci web w przeglądarce.

7. Przetestuj funkcjonalność, która powinny być profilowane.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profilowanie kodu JavaScript w stronach sieci web lub aplikacji JavaScript

1. Otwórz program Visual Studio.

2. Na **analizy** menu, kliknij przycisk **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie kreatora wydajności, należy określić **Instrumentacji** metoda profilowania, a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **dalej.**

5. Na trzeciej stronie kreatora:

    1. Wpisz adres URL strony w **jakim adresem URL lub ścieżką będzie działała aplikacja sieci** pole.

    2. Wybierz **Profiluj kod JavaScript** pole wyboru, a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora kliknij **Zakończ** można uruchomić strony sieci web w przeglądarce.

7. Przetestuj funkcjonalność, która powinny być profilowane.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.