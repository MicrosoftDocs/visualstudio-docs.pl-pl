---
title: Identyfikator GUID i identyfikatory poleceń programu Visual Studio | Microsoft Docs
description: Dowiedz się, jak zlokalizować identyfikator GUID i wartości identyfikatorów poleceń zawartych w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cabf5c9452cf0a6809673d488f9cf01252d7b0ef
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480450"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikator GUID i identyfikatory poleceń programu Visual Studio
Wartości identyfikatora GUID i identyfikatora poleceń zawartych w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio są zdefiniowane w plikach. vsct, które są instalowane w ramach zestawu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [polecenia, menu i grupy zdefiniowane przez środowisko IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Aby uzyskać więcej informacji na temat sposobu pracy z obiektami IDE zdefiniowanymi w plikach *. vsct* , zobacz sekcję [rozszerzając menu i polecenia](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Znajdź definicję polecenia
 Ponieważ program Visual Studio definiuje więcej niż 1000 poleceń, nie jest praktyczne, aby wyświetlić je w tym miejscu. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicję polecenia.

### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicję polecenia

1. W programie Visual Studio Otwórz następujące pliki w *<ścieżka instalacji zestawu SDK programu Visual Studio \> \VisualStudioIntegration\Common\Inc \\* folder: *SharedCmdDef. vsct*, *ShellCmdDef. vsct*, *VsDbgCmdUsed. vsct*, *Venusmenu. vsct*.

    Większość poleceń programu Visual Studio jest zdefiniowanych w *SharedCmdDef. vsct* i *ShellCmdDef. vsct*. *VsDbgCmdUsed. vsct* definiuje polecenia, które odnoszą się do debugera, a *Venusmenu. vsct* definiuje polecenia, które są specyficzne dla programowania w sieci Web.

2. Jeśli polecenie jest elementem menu, należy zwrócić uwagę na dokładny tekst elementu menu. Jeśli polecenie jest przyciskiem na pasku narzędzi, należy zwrócić uwagę na tekst etykietki narzędzia, który pojawia się po jej zatrzymaniu.

3. Naciśnij klawisz **Ctrl** + **F** , aby otworzyć okno dialogowe **Znajdowanie** .

4. W polu **Znajdź** , wpisz tekst zanotowany w kroku 2.

5. Sprawdź, czy **wszystkie otwarte dokumenty** są wyświetlane w polu **Szukaj w** .

6. Kliknij przycisk **Znajdź następny** do momentu wybrania tekstu w `<Strings>` sekcji [elementu Button](../../extensibility/button-element.md).

    `<Button>`Element, w którym pojawia się polecenie, jest definicją polecenia.

   Po znalezieniu definicji polecenia można umieścić kopię polecenia w innym menu lub pasku narzędzi, tworząc [element CommandPlacement](../../extensibility/commandplacement-element.md) , który ma takie same `guid` wartości, `id` jak polecenie. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Specjalne przypadki
 W następujących przypadkach tekst menu lub etykietka narzędzia mogą nie być dokładnie zgodne z definicją polecenia.

- Elementy menu, które zawierają podkreślony znak, taki jak polecenie **Print** w menu **plik** , w którym *P* jest podkreślony.

     Znaki, które są poprzedzone znakiem handlowego "i" (&) w nazwach elementów menu, są wyświetlane jako podkreślone. Jednak pliki *. vsct* są napisane w języku XML, który używa znaku handlowego "i" (&), aby wskazać znaki specjalne i wymaga, aby wyświetlić znak "i", musi być wpisany jako *&amp; amp;*. W związku z tym w pliku *. vsct* polecenie **Print** jest wyświetlane jako *&amp; amp; Drukuj*.

- Polecenia, które mają dynamiczny tekst, takie jak **Zapisz** \<Current Filename\> i dynamicznie generowane elementy menu, takie jak elementy na liście **ostatnie pliki** .

     Nie istnieje niezawodny sposób wyszukiwania tekstu dynamicznego. Zamiast tego Znajdź grupę, która hostuje odpowiednie polecenie, sprawdzając identyfikatory [GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub identyfikatorów [GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), a następnie wyszukaj identyfikator tej grupy. Jeśli definicja polecenia nie ma grupy jako [elementu nadrzędnego](../../extensibility/parent-element.md), Wyszukaj *SharedCmdPlace. vsct* i *ShellCmdPlace. vsct* (lub *VsDbgCmdPlace. vsct* dla poleceń debugera) dla `<CommandPlacement>` elementu, który ustawia element nadrzędny polecenia. *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct* i *VsDbgCmdPlace. vsct* znajdują się w folderze *\<Visual Studio SDK installation path\> \VisualStudioIntegration\Common\Inc \\* .

## <a name="see-also"></a>Zobacz też

- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Dokumentacja schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
