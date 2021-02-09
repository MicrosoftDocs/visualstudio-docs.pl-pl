---
title: Profilowanie kodu JavaScript na stronach sieci Web | Microsoft Docs
description: Dowiedz się, jak program Visual Studio narzędzia profilowania może zbierać dane dotyczące wydajności kodu JavaScript przy użyciu metody profilowania Instrumentacji.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 288fa04fa44528ad34c68cf3d770bb6d5673b976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907120"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>Instrukcje: profilowanie kodu JavaScript na stronach sieci Web

Program Visual Studio narzędzia profilowania może zbierać dane dotyczące wydajności kodu JavaScript, który jest wykonywany w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, dowolnej stronie sieci Web lub aplikacji JavaScript przy użyciu metody profilowania Instrumentacji. Wymaga programu Internet Explorer 8 lub nowszego.

> [!WARNING]
> Aby profilować kod JavaScript w aplikacjach platformy UWP, zobacz [JavaScript Memory](../profiling/javascript-memory.md)

Aby utworzyć sesję wydajności, można użyć Kreatora profilowania. Określ metodę instrumentacji, a następnie określ opcję profilowania JavaScript na stronie Instrumentacja okna dialogowego właściwości dla sesji wydajności.

Po określeniu profilowania JavaScript, zarówno kod JavaScript wykonywany w przeglądarce, jak i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod wykonywany na serwerze są profilowane.

- W przypadku [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web kod języka JavaScript wykonywany w przeglądarce i [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod wykonywany na serwerze są profilowane.

- W przypadku dowolnej strony sieci Web kod JavaScript wykonywany w przeglądarce jest profilowany.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>Aby profilować kod JavaScript w projekcie aplikacji sieci Web ASP.NET

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Projekt sieci Web w programie Visual Studio.

2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie Kreatora wydajności Określ metodę profilowania **Instrumentacji** , a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora upewnij się, że na liście elementów docelowych wybrano bieżący projekt, a następnie kliknij przycisk **Dalej.**

5. Na trzeciej stronie kreatora zaznacz pole wyboru **profil JavaScript** , a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora kliknij przycisk **Zakończ** , aby uruchomić aplikację sieci Web w przeglądarce.

7. Wykonuj funkcje, które chcesz profilować.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>Aby profilować kod JavaScript na poszczególnych stronach sieci Web lub w aplikacjach JavaScript

1. Otwórz program Visual Studio.

2. W menu **Analizuj** kliknij polecenie **Uruchom Kreatora wydajności**.

3. Na pierwszej stronie Kreatora wydajności Określ metodę profilowania **Instrumentacji** , a następnie kliknij przycisk **dalej**.

4. Na drugiej stronie kreatora kliknij aplikację ASP.NET lub JavaScript, a następnie kliknij przycisk **Dalej.**

5. Na trzeciej stronie kreatora:

    1. Wpisz adres URL strony w polu **adres URL lub ścieżka uruchomi aplikację** .

    2. Zaznacz pole wyboru **profil JavaScript** , a następnie kliknij przycisk **dalej**.

6. Na czwartej stronie kreatora kliknij przycisk **Zakończ** , aby uruchomić stronę sieci Web w przeglądarce.

7. Wykonuj funkcje, które chcesz profilować.

8. Aby zakończyć sesję profilowania, zamknij przeglądarkę.
