---
title: Zaawansowane ustawienia zabezpieczeń — Okno dialogowe
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 033c8d9c97d54b972a7bf30e9e1e04171e5b505e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595842"
---
# <a name="advanced-security-settings-dialog-box"></a>Zaawansowane ustawienia zabezpieczeń — Okno dialogowe

To okno dialogowe umożliwia określenie ustawień zabezpieczeń związanych z debugowaniem w strefie.

![Okno dialogowe Zaawansowane ustawienia zabezpieczeń w programie Visual Studio](../media/advanced-security-settings.png)

Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości**. Po wyświetleniu **projektanta projektu** kliknij kartę **Zabezpieczenia.** Na stronie **Zabezpieczenia** wybierz pozycję **Włącz pozycję Kliknij pozycję Ustawienia zabezpieczeń,** kliknij pozycję To jest aplikacja **częściowego zaufania**, a następnie kliknij pozycję **Zaawansowane**.

## <a name="uielement-list"></a>Lista UIElement

**Udzielenie aplikacji dostępu do miejsca pochodzenia**

Jeśli zaznaczysz to pole wyboru, aplikacja może uzyskać dostęp do witryny sieci Web lub udziału serwera, na którym jest publikowana. Ta opcja jest wybrana domyślnie.

**Debugowanie tej aplikacji tak, jakby została pobrana z następującego adresu URL**

Jeśli musisz zezwolić aplikacji na dostęp do udziału w witrynie sieci Web lub serwera odpowiadającego **adresowi URL instalacji** określonemu na stronie **Publikowanie,** wprowadź ten adres URL tutaj. Ta opcja jest dostępna tylko wtedy, gdy **wybrano opcję Przyznanie aplikacji dostępu do jej witryny pochodzenia.**

## <a name="see-also"></a>Zobacz też

- [Strona zabezpieczeń, Projektant projektu](../../ide/reference/security-page-project-designer.md)
