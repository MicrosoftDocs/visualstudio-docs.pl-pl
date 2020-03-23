---
title: 'Jak: Profil JavaScript Kod na stronach internetowych | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 07c628b3c1f0be1c7ecc615dcae44f7736aa884e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775309"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Jak: Profil kodu JavaScript na stronach internetowych

Narzędzia profilowania programu Visual Studio mogą zbierać dane [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dotyczące wydajności kodu JavaScript, który jest wykonywany w aplikacji sieci web, dowolnej stronie sieci web lub aplikacji JavaScript przy użyciu metody profilowania instrumentacji. Wymaga programu Internet Explorer 8 lub nowszego.

> [!WARNING]
> Aby profilować język JavaScript w aplikacjach platformy uniwersalnej systemu Windows, zobacz [Pamięć javascript](../profiling/javascript-memory.md)

Za pomocą Kreatora profilowania można utworzyć sesję wydajności. Określ metodę instrumentacji, a następnie określ opcję profilowania JavaScript na stronie Instrumentacja okna dialogowego właściwości sesji wydajności.

Po określeniu profilowania JavaScript profilowanie, zarówno kod JavaScript, który jest wykonywany w przeglądarce, jak i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod, który jest wykonywany na serwerze są profilowane.

- W [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] przypadku aplikacji sieci web profilowane są zarówno kod [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] JavaScript, który jest wykonywany w przeglądarce, jak i kod wykonywany na serwerze.

- Dla dowolnej strony sieci web kod JavaScript, który jest wykonywany w przeglądarce jest profilowany.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować javascript w projekcie aplikacji sieci web ASP.NET

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projekt sieci web w programie Visual Studio.

2. W menu **Analiza** kliknij polecenie **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie Kreatora wydajności określ metodę profilowania **instrumentacji,** a następnie kliknij przycisk **Dalej**.

4. Na drugiej stronie kreatora upewnij się, że bieżący projekt jest zaznaczony na liście obiektów docelowych, a następnie kliknij przycisk **Dalej.**

5. Na trzeciej stronie kreatora zaznacz pole wyboru **Profil JavaScript,** a następnie kliknij przycisk **Dalej**.

6. Na czwartej stronie kreatora kliknij przycisk **Zakończ,** aby uruchomić aplikację internetową w przeglądarce.

7. Korzystaj z funkcji, które chcesz profilować.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Profiluj javascript na poszczególnych stronach internetowych lub w aplikacjach JavaScript

1. Otwórz program Visual Studio.

2. W menu **Analiza** kliknij polecenie **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie Kreatora wydajności określ metodę profilowania **instrumentacji,** a następnie kliknij przycisk **Dalej**.

4. Na drugiej stronie kreatora kliknij pozycję ASP.NET lub javascript, a następnie kliknij przycisk **Dalej.**

5. Na trzeciej stronie kreatora:

    1. Wpisz adres URL strony w polu **Jaki adres URL lub ścieżka spowoduje uruchomienie aplikacji.**

    2. Zaznacz pole wyboru **Profil JavaScript,** a następnie kliknij przycisk **Dalej**.

6. Na czwartej stronie kreatora kliknij przycisk **Zakończ,** aby uruchomić stronę internetową w przeglądarce.

7. Korzystaj z funkcji, które chcesz profilować.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.
