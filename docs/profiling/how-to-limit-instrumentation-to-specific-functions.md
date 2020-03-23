---
title: 'Jak: Ograniczenie oprzyrządowania do określonych funkcji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 34a63645933a173e449cf4292cc3d014cc3ec740
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775322"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Instrukcje: ograniczanie instrumentacji do określonych funkcji
Instrumentację i zbieranie danych można ograniczyć do jednej lub więcej funkcji, ustawiając opcje na stronie **Zaawansowane** **strony sesji wydajności** lub docelowych stronach właściwości binarnych:

- Jeśli określisz funkcje na stronie właściwości sesji wydajności, tylko te funkcje są instrumentowane we wszystkich instrumentowanych plikach binarnych sesji.

- Jeśli określisz funkcje na stronie właściwości pliku binarnego docelowego, tylko te funkcje, które znajdują się w tym konkretnym pliku binarnym są instrumentowane. Funkcje w innych plikach binarnych wykonania są instrumentowane jak zwykle.

  Ograniczanie zbierania danych w ten sposób jest obsługiwane tylko wtedy, gdy wybrana jest metoda profilowania instrumentacji.

> [!NOTE]
> Za pomocą strony **Zaawansowane** strony stron właściwości **Sesja wydajności** można również ustawić inne opcje dostępne dla narzędzia instrumentacji wiersza polecenia VSInstr narzędzia narzędziu narzędziowego wiersza polecenia [VSInstr.](../profiling/vsinstr.md)

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Aby ograniczyć instrumentację do określonych funkcji w sesji wydajności

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy nazwę sesji, a następnie kliknij polecenie **Właściwości**.

    Wyświetli się okno dialogowe **Strony właściwości**.

2. W oknie dialogowym **Strony właściwości** kliknij pozycję **Zaawansowane**.

3. W polu tekstowym **Opcje instrumentacji dodatkowe** użyj następującej składni, aby wpisać nazwę funkcji, które mają być instrumenta dla:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`jest przestrzenią nazw i nazwą funkcji. Ma format `Namespace` **::**`FunctionName`. Użyj średnika, aby oddzielić wiele funkcji. Użyj gwiazdki (\*), aby określić symbol wieloznaczny dla jednego lub więcej znaków. Na przykład **/include:MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.

   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, otwórz okno wiersza polecenia w katalogu instalacyjnym Narzędzia profilowania (zobacz [Określanie ścieżki do narzędzi wiersza polecenia),](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)a następnie wpisz **vsinstr /DumpFuncs**

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Aby ograniczyć oprzyrządowanie do określonych funkcji w pliku binarnym

1. W **Eksploratorze wydajności**znajdź nazwę binarną w węźle **Cele** sesji wydajności.

2. Kliknij prawym przyciskiem myszy nazwę binarną, a następnie kliknij polecenie **Właściwości**.

    Wyświetli się okno dialogowe **Strony właściwości**.

3. W oknie dialogowym **Strony właściwości** kliknij pozycję **Zaawansowane**.

4. W polu tekstowym **Opcje instrumentacji dodatkowe** użyj następującej składni, aby wpisać nazwę funkcji, które mają być instrumenta dla:

    **/include:** `FuncSpec` **[;** `FuncSpec` **]**`...`

    `FuncSpec`jest przestrzenią nazw i nazwą funkcji. Ma format `Namespace` **::**`FunctionName`. Użyj średnika, aby oddzielić wiele funkcji. Użyj gwiazdki (\*), aby określić symbol wieloznaczny dla jednego lub więcej znaków. Na przykład **/include:MyNS::\\*** określa wszystkie funkcje w obszarze nazw MyNS.

   > [!NOTE]
   > Aby wyświetlić listę funkcji w pliku binarnym, otwórz okno wiersza polecenia w katalogu instalacyjnym Narzędzia profilowania (zobacz [Określanie ścieżki do narzędzi wiersza polecenia),](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)a następnie wpisz **vsinstr /DumpFuncs**

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Instrukcje: ograniczanie instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [Instrukcje: określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)
